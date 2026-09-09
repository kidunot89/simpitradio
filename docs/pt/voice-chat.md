# Voz no rádio

O SimPitRadio escreve o que disseste na caixa de chat do jogo. Isto acrescenta a outra
metade: as pessoas contra quem corres mandam-te também o *áudio*, e tu ouves.

De propósito, não é o Discord. O Discord já existe, funciona, e toda a gente já está num.
O que o Discord não consegue fazer é pôr-te numa sala com **quem quer que esteja nesta
sessão**, sem combinar antes, e calar os que estão a quatro quilómetros.

## O que viaja

**O excerto do push-to-talk, ao largar. Não uma transmissão em direto.**

O ciclo do acionador já grava um excerto enquanto a tecla está premida e entrega-o ao
Whisper ao largar. A voz reutiliza exatamente esse excerto: ao largar vai para o Whisper
*e* para o relé, e os outros reproduzem-no. Nada do caminho de gravação muda.

Uma transmissão em direto seria outra aplicação. Precisa de tramas de 20 ms, de um buffer
de jitter, de um misturador e de um relógio de reprodução, tudo no caminho do áudio, e a
recompensa é que as pessoas te ouvem 1,5 segundos mais cedo. O excerto é aquilo que um
rádio de box é de qualquer modo: manténs o botão, dizes uma coisa, chega.

A consequência que vale a pena conhecer: **um excerto é atómico.** Não pode ser
interrompido, chega inteiro ou não chega, e duas pessoas a falar ao mesmo tempo produzem
dois excertos que fazem fila em vez de se atropelarem. Isso é melhor do que uma corrida,
não pior.

## Quem o ouve

O relé é burro. Distribui um excerto por todos os da sala e não decide quem o deve
receber, porque não pode — não faz ideia de onde está quem quer que seja na pista, e
dar-lhe essa informação seria pior do que inútil.

**A proximidade é decidida na máquina de quem ouve.** A memória partilhada do LMU
transporta a posição no mundo de *cada* carro, não só do teu, por isso cada cliente já
sabe exatamente a que distância está cada outro piloto. Nada de posicional é alguma vez
publicado ao relé, e a funcionalidade trabalha mesmo que quem opera o relé seja hostil.

**Ganha a visão que quem ouve tem de onde está quem fala.** Um excerto chega depois de
quem falava ter parado, por isso a posição que traz tem um segundo ou dois — a ritmo de
corrida, cem metros, o que contra um raio de 200 m decide a resposta. O bloco de
classificação tem cada carro tal como está *agora*, e a pergunta é quem está perto do
carro alvo quando a mensagem toca.

O excerto transporta a posição de quem fala na mesma, como recurso para alguém que o bloco
de quem ouve ainda não apanhou: um piloto que acabou de entrar, ou cuja entrada
desapareceu. Uma posição velha vale mais do que nenhuma.

Preferir a vista local significa também que um excerto não consegue falar até passar pelo
filtro. Um cliente que afirma estar ao teu lado quando está a um quilómetro é simplesmente
medido onde está de facto. Isso é consequência de usar o número mais fresco, não um
mecanismo de segurança — quem não se consegue situar de todo continua audível, porque um
silêncio que ninguém consegue explicar é a falha pior.

`proximity_only` no plugin do LMU liga isto; `proximity_metres` define o raio. Desligado,
ouves a sessão inteira, que é o que queres nos treinos e numa volta de formação.

### A assistir

A proximidade devia ser medida a partir do carro no ecrã: seguir uma luta no meio da qual
estás, enquanto ouves o rádio de quatro quilómetros mais além, onde o teu próprio carro
está estacionado, não é proximidade em nenhum sentido que um espectador reconhecesse.

Tem de ser **detetado**. Quem está a correr não consegue alcançar uma lista pendente, e
quem assiste não devia ter de o fazer.

**O bloco de memória partilhada não o diz**, e três fontes plausíveis foram verificadas
contra uma sessão realmente assistida e postas de lado — cada uma parece a certa, e
nenhuma o é:

- `telemetry.playerVehicleIdx` é o veículo do *jogador*. Enquanto se assistia a outra
  pessoa, continuava apontado ao carro estacionado de quem assistia.
- `appInfo.mOptionsLocation` leu 0 o tempo todo.
- `$rFactor2SMMP_Graphics$` é publicado e transportaria tanto uma posição de câmara como o
  id do lugar observado — mas o LMU nunca o preenche. O buffer é inteiramente zeros à parte
  o contador de versão, porque o jogo não chama a retrochamada gráfica a partir da qual o
  plugin do rF2 o enche. O bloco Extended vizinho estava vivo nesse mesmo instante, por
  isso é uma escolha do LMU e não uma instalação estragada.

**A própria API HTTP do LMU diz.** `http://127.0.0.1:6397/rest/watch/standings` é o que os
overlays do próprio jogo leem, e cada entrada traz `hasFocus` — posto no carro que está a
ser visto, distinto de `player`, que fica no teu. O seu `slotID` é o mesmo número que
`mID` na memória partilhada, por isso os dois juntam-se diretamente. Faz parte do jogo e
não de um plugin qualquer, por isso não precisa de nada instalado.

Lido com um tempo-limite curto e guardado em cache por um segundo: isto corre no ciclo do
acionador, a resposta tem ~16 KB, e uma aplicação de ditado nunca deve esperar por um jogo
a meio de carregar. **As falhas também vão para cache** — caso contrário um jogo fechado
custa um tempo-limite em cada pressão.

Toda a falha dá None, e `SessionInfo.listener()` recai então no carro conduzido e por fim
em None, que `audible` lê como audível. Manter em silêncio um carro estacionado como
referência filtraria a sessão por um sítio para onde ninguém está a olhar, e nenhum
ouvinte conseguiria distinguir isso de uma funcionalidade avariada.

**«Proximidade» quer dizer na pista e em mais lado nenhum.** São metros entre dois carros
no jogo, lidos do simulador, calculados localmente. Não tem nada que ver com onde alguém
mora, e nenhuma localização física é lida, deduzida ou transmitida. O *alojamento* de
relés, mais abaixo, também fala de distância, no sentido de rede — isso é uma questão de
encaminhamento entre servidores e não tem relação com quem consegues ouvir.

## Que sala

O id de sessão é derivado, nunca anunciado:

    sha256("pitradio/1:{mServerPublicIP}:{mServerPort}")[:32]

Toda a gente no mesmo servidor de jogo calcula o mesmo id sem que ninguém publique qual é
esse servidor — o relé aprende um hash e mais nada. Offline e um jogador não têm servidor,
por isso não produzem id nem sala, o que é o comportamento correto e não um caso especial.

O traçado está deliberadamente *fora* da chave. Muda entre sessões no mesmo servidor, e
uma sala que se dissolve quando o evento passa ao traçado seguinte é uma sala pior.

A identidade dentro de uma sala é o nome do piloto vindo do bloco de classificação.
`mSteamID` é zero na prática, por isso não há nada melhor disponível.

## O relé

**O código e a configuração do relé não estão neste repositório.** O SimPitRadio é
público; o servidor, o seu Terraform e o seu Ansible são privados, juntamente com o
segredo de cliente OAuth de que precisam. O Terraform e o Ansible existem ali para um
trabalho: levantar de forma reproduzível, a partir de uma imagem limpa, um anfitrião de
voz **fornecido por um piloto**.

O endereço do relé base também não está neste repositório. É escrito em
[endpoints.py](../src/pitradio/endpoints.py) **em tempo de compilação**, por isso uma
cópia do código — ou um fork — não tem endereço nenhum e a voz fica simplesmente
indisponível. É um estado que funciona, não um estragado: melhor do que cada clone do
código apontar um microfone a um servidor cujo dono nunca aceitou suportá-lo.

Mais nada na aplicação pode fixar um endereço no código. Um sítio para sobrescrever, um
sítio onde olhar quando está errado.

    wss://<relé>/chat/{id-de-sessão}

Um WebSocket por cliente, TLS, excertos como tramas binárias com um cabeçalho pequeno. É
todo o protocolo. TLS porque um relé é a máquina de um desconhecido e o áudio da tua voz
não devia atravessá-la às claras; WebSocket porque sobrevive a todos os NAT e firewalls
empresariais a que o UDP em cru não sobrevive, e porque a largura de banda de áudio de
vinte pilotos a carregar num botão de vez em quando não é nada.

**Não é literalmente ponto a ponto.** O P2P a sério precisa de ICE, STUN e de um recurso a
TURN — e o TURN é um relé, por isso o caminho de recurso é este desenho de qualquer
maneira, alcançado depois de arrastar uma pilha WebRTC para dentro de uma compilação
Nuitka que já luta com dependências nativas. O relé é uma caixinha, e é honesto quanto a
sê-lo.

### Anfitriões da comunidade

Os relés existem para estarem *perto de quem fala*. Uma grelha tirada de três continentes
encaminhada por uma caixa em Frankfurt paga o Atlântico duas vezes em cada excerto; um relé
escolhido para o grupo não. É essa toda a razão por que os pilotos podem alojar: nem o
custo, nem a descentralização por si mesma — a geografia.

O Terraform faz a máquina; o Ansible instala o relé, a unidade systemd e o certificado
TLS, por isso um anfitrião é reproduzível a partir de uma imagem Ubuntu limpa sem passos
manuais.

Primeiro OAuth da DigitalOcean, porque é o que existe hoje. A Linode tem um fluxo real de
aplicação OAuth e pode seguir. **A AWS não pode**: não tem OAuth de consumidor para
aprovisionamento — são chaves IAM ou SSO do Identity Center — por isso precisa de um
caminho próprio e não é uma questão de acrescentar um botão.

#### Escolher um é uma decisão de grupo, não pessoal

**Todos os clientes de uma sessão têm de escolher o mesmo relé, ou não escolhem nenhum.**
Deixados a si próprios, cada um escolheria o anfitrião mais perto de *si*, o que para uma
grelha transatlântica significa dois relés, duas salas, e as duas metades da sessão
sentadas naquilo que parece exatamente uma funcionalidade a funcionar, sem mais ninguém lá
dentro. É a mesma falha silenciosa de uma chave de sessão que não bate certo, alcançada por
outro caminho.

Por isso há um coordenador, no anfitrião base fixo, e é ele que decide:

1. Os clientes entram na sala no relé configurado da compilação e reportam o seu tempo de
   ida e volta medido a cada relé candidato.
2. O coordenador escolhe aquele com o melhor pior caso em toda a sala — minimizando a
   latência do piloto *mais lento*, não a média, porque a questão é que ninguém fique
   isolado.
3. Diz a toda a gente para migrar, e reconectam-se ali em conjunto.

O anfitrião base é também o relé de recurso, e é isso que torna a coisa comportável: o
coordenador tem de estar sempre ligado de qualquer maneira, mais vale que transporte o
áudio das sessões pequenas ou locais demais para valer a pena mudar.

#### Porque não interligar todos os anfitriões

A alternativa óbvia: deixar cada cliente ligar-se ao relé que lhe fica mais perto *a ele*, e
fazer os relés reencaminharem excertos uns para os outros. É um desenho a sério — o Mumble
liga servidores assim — e é genuinamente mais elegante num aspeto, porque apaga a decisão de
grupo acima. Não há nada para acordar se a sala abrange todos os relés, por isso a falha da
sala dividida nem sequer pode acontecer.

Continua a ser a troca errada aqui, por uma razão: **mandamos excertos, não uma transmissão
em direto.** Um excerto é despachado depois de quem fala ter parado, por isso a diferença
entre 90 ms e 250 ms de encaminhamento não é coisa que alguém consiga percecionar — o que é
a maior parte do argumento a favor da geografia, e todo o argumento para pagar dois saltos
extra para a melhorar.

O que a interligação custa não são saltos, é estado. Os relés teriam de trocar entre si a
composição das salas, autenticar-se uns aos outros e proteger-se contra ciclos e entregas
duplicadas, e um relé alojado por um piloto que entre nesse tecido consegue ver tráfego de
salas onde não tem membros. Isso é um projeto de sistemas distribuídos aparafusado à ilharga
de uma aplicação de ditado, ao serviço de um orçamento de latência que este desenho não tem.

Se o SimPitRadio alguma vez passar a transmitir em direto, isto inverte-se e a interligação
passa a ser a resposta certa. A forma a construir então: uma malha completa com um segredo
partilhado, a composição das salas propagada por boato, e cada excerto a levar um id com um
limite de **um salto** entre relés — sem reencaminhamento transitivo, o que mata à nascença
os ciclos de encaminhamento e limita o alastramento em vez de confiar nele.

#### Quando um anfitrião desaparece

Um relé que desaparece não pode acabar com a conversa. O coordenador guarda a sala, repara
que o relé deixou de responder, volta a correr a escolha sobre o que resta e migra os
pilotos restantes — o mesmo mecanismo da escolha inicial, por isso não há um caminho de
recuperação à parte para correr mal. Os clientes mantêm a ligação ao coordenador aberta
exatamente por isto: é a coisa que sobrevive.

Um piloto que sai da sessão não leva o relé dele a meio da corrida. A máquina dele não é o
relé — é um droplet que aprovisionou — e puxá-lo debaixo dos pés de quem ainda está a
conduzir seria o pior momento possível.

#### Quando a sessão acaba

As salas são desmontadas, não deixadas a correr. O LMU reporta a sua fase de jogo, por isso
um cliente que vê a sessão acabar di-lo; quando o último cliente sai, ou a sala fica calada
para lá de um tempo de inatividade, o coordenador fecha-a. Um relé sem salas nenhumas é
candidato a `terraform destroy`, e essa é a diferença entre isto custar a um piloto uns
cêntimos por evento ou custar-lhe um droplet para sempre.

O tempo de inatividade conta tanto como o sinal explícito. Um cliente que rebenta, salta
para outra janela e desaparece ou perde a rede nunca envia nada — por isso nada pode
depender de que o faça.

## Consentimento

A voz está **desligada até ser ligada**, por perfil, e a janela diz quem te pode ouvir antes
de dizer o que quer que seja. Uma aplicação de ditado que abrisse em silêncio o microfone a
vinte desconhecidos seria uma traição, por melhor que a funcionalidade fosse.

Só push-to-talk. Não há modo de microfone aberto e não deve haver: a tecla é o
consentimento.
