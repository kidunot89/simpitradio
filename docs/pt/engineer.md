# O engenheiro

Uma voz com nome que acompanha o simulador e fala consigo: os seus tempos de
volta, os carros ao lado e respostas quando lhe pergunta alguma coisa.

Partilha a tecla de push-to-talk com tudo o resto que o SimPitRadio faz.
Mantenha o gatilho premido, diga «Chief, target P3», solte — e em vez de ir para
a janela de chat, é o engenheiro que responde.

**Está desligado até o ligar.** Nada é dito até ir a Definições → Engenheiro e
marcar a caixa.

---

## Começo rápido

1. Abra **Definições → Engenheiro** e marque **Engenheiro ligado**.
2. Escolha um dos quatro engenheiros. Isso define o nome, a voz e o quanto ele
   fala.
3. Carregue em **Testar**. Deverá ouvi-lo repetir o próprio nome.
4. Defina o **Dispositivo de saída** para os seus auscultadores — os mesmos que
   usa para o chat de voz, não a saída do simulador.
5. Conduza. Ele lê o seu tempo de volta na linha.
6. Mantenha o gatilho premido e diga **«Chief, target P3»** para iniciar o coach
   de curva contra quem estiver em terceiro.

Se o Testar não disser nada, veja [Nada é dito](#nada-é-dito) no fim.

---

## Falar com ele

Há duas formas de uma frase se tornar um comando, e ambas são deliberadamente
estreitas. A mesma tecla envia mensagens a toda a gente na sua sessão, portanto
um comando que o engenheiro *invente* é uma mensagem que, em silêncio, nunca
chega.

**Diga o nome dele primeiro.** «Chief, target P3.» O nome vem primeiro, a
expressão vem logo a seguir. `hey`, `ok` e `right` são permitidos antes do nome.

**Ou diga uma expressão sozinha** — mas apenas as que não levam um piloto.
«initiate corner coaching» funciona sem nada à frente. «target Verstappen» não,
porque «target» poderia começar uma frase vulgar e o seu argumento não tem fim:
*«target time is a twenty three»* seria de outro modo engolido por inteiro e
nunca chegaria à janela de chat.

Dizer apenas o nome dá «go ahead», como faria um rádio a sério — e mantém um
«Chief» perdido fora de uma mensagem para outras vinte pessoas.

**«Stop»** funciona sempre, seja o que for que esteja a decorrer e seja o que for
que o tenha iniciado. O mesmo vale para «stand down», «cancel», «that's enough» e
«forget it».

Tudo o que o engenheiro não reconhece é uma mensagem, e vai para a janela de chat
exatamente como antes.

---

## Escolher um engenheiro

Vêm quatro com a aplicação:

| | Voz | Estilo |
| --- | --- | --- |
| **Chief** | masculina | Calmo e completo. «Curva quatro, o Tandy foi mais rápido à saída, dois décimos.» |
| **Ada** | feminina | Seca. Omite o número da curva: «Tandy, melhor saída, dois décimos.» |
| **Marshall** | masculina | Mais lento e mais completo, se os outros parecerem apressados. |
| **Vic** | feminina | Rápida e curta. A que menos fala dos quatro. |

São **predefinições, não gravações** — um nome, uma voz do Windows preferida, um
ritmo e o quanto dizem. Vale a pena dizê-lo com clareza, porque «quatro vozes»
costuma significar quatro conjuntos de áudio: um pacote de voz gerado tem um a
dois gigabytes, e distribuir quatro seria um download de oito gigabytes para
substituir algo que já está de graça em qualquer máquina Windows.

Cada um escolhe a melhor voz do Windows instalada que corresponda à sua
preferência e ao seu idioma. Numa instalação normal do Windows 11 há normalmente
duas ou três, portanto dois engenheiros podem partilhar uma voz e distinguir-se
pelo ritmo e pela formulação. Se quiser uma específica, defina **Voz do Windows**
e isso sobrepõe-se à predefinição.

**Tratado por** é aquilo a que ele responde. Ponha o que quiser — o nome só serve
para o interpelar, e «Bob, target P3» funciona exatamente igual.

---

## O que ele lhe diz

### Tempos de volta

Lê a sua volta quando cruza a linha, e diz quando foi a sua melhor. Ligado por
predefinição.

### Spotter

Anuncia carros ao lado: «car left», «car right», «cars both sides», e depois
«clear» assim que se afastam. Desligado por predefinição, e há uma coisa a saber.

**Qual lado é qual não pôde ser verificado sem um carro numa pista.** As posições
vêm das coordenadas de mundo do próprio simulador, e se as contas dão esquerda ou
direita depende de uma convenção de orientação que este projeto não conseguiu
confirmar a partir de uma máquina de desenvolvimento. Portanto, se ele disser
«esquerda» para um carro à sua direita, ligue **Trocar os lados do spotter** em
Perfis → definições do plugin do jogo. Uma marca, uma vez.

Tudo o resto no spotter é exato: usa as posições do jogo, descarta a altura (para
que uma ponte ou as esses de Le Mans não ponham ninguém encostado à sua porta) e
não anuncia carros numa reta adjacente.

### Danos

Diz o que se partiu e se deve entrar por causa disso. Ligado por predefinição, e
precisa de um simulador que publique o estado do carro — hoje, é o Le Mans
Ultimate.

> *Perdeu carroçaria. Boxes esta volta.*

**Dito quando muda, não enquanto dura.** Um piloto que carrega uma traseira
esquerda amolgada durante meia hora não precisa de ser lembrado disso a cada
passagem, por isso fala no momento em que piora e depois cala-se. Cada parte da
leitura é vigiada, não só a pior — uma segunda coisa a soltar-se de um carro já
amolgado é novidade, mesmo que a gravidade não tenha mudado.

**O que ele diz é onde, e depois se.** Já sabe que bateu em alguma coisa; o que
não vê do banco é o quão mau é e se há tempo para reparar. Por isso nomeia o
sítio — o nariz, a traseira, todo o lado esquerdo — e depois dá uma de três
respostas:

| | |
| --- | --- |
| **Boxes esta volta** | o carro não pode ser corrido, apenas trazido devagar: uma peça pendurada, um furo, uma roda perdida ou um nariz partido. O tempo que resta não muda isto — a alternativa é bandeira negra ou um muro |
| **Boxes quando puder** | vale a pena reparar. Sempre em treinos e qualificação, onde uma paragem não custa nada e o objetivo de estar em pista é ter um carro que funcione |
| **Fique em pista, aguentamos assim** | uma corrida com menos de um quinto por correr. A três voltas do fim, é melhor levar um carro maltratado à bandeira do que devolver um minuto |

Danos ligeiros recebem a primeira metade e nenhum conselho. Ouvir que deve pesar
uma paragem por um guarda-lamas traseiro riscado é pior do que não ouvir nada.

Nunca fala por cima do coach. Os danos são urgentes — quer saber que a asa se foi
antes da curva seguinte e não depois — mas uma crítica que pediu não merece ser
cortada por um carro que daqui a quatro segundos continuará partido. O spotter é
o único anúncio que fala por cima de seja o que for.

---

## Quem ele observa

O engenheiro mantém um **foco**: um piloto com quem o compara. Não tem de o
definir. Por predefinição é **o carro à frente na sua classe**, ou o carro atrás
quando é você a liderá-la — porque não há ninguém à frente para perseguir, e a
pergunta passa a ser se os está a manter atrás.

Só segue uma mudança depois de a posição se **manter oito segundos**. As posições
fervilham: medido num arranque de corrida real, quinze pilotos diferentes foram o
carro da frente em noventa segundos, e cada troca deitava fora as voltas
acumuladas, pelo que nunca tinha o suficiente para dizer fosse o que fosse.

Diga se quiser outra pessoa:

- `focus on {piloto}` — ou «keep an eye on», «keep tabs on», «study», «watch»
- `default focus` — de volta a escolher sozinho
- `stop focusing` — desligado, e fica desligado até ser chamado de novo

Um piloto que você indique nunca é ignorado. Voltar duas curvas depois para quem
está à frente é a aplicação a discordar de si.

O separador Estado mostra quem está a ser observado, e `what are we watching`
pergunta-o.

---

## Perguntar-lhe coisas

Cada pergunta tem uma caixa de expressões em Definições → Engenheiro, uma por
linha, e o que escrever substitui os valores predefinidos. Cada uma pode ser
desligada; uma pergunta desligada não contribui com expressão nenhuma, pelo que
as suas palavras chegam à janela de chat como quaisquer outras em vez de serem
apanhadas e respondidas com nada.

- **O seu carro** — `what's my best lap`, `how are the tyres`, `what's the
  damage`, `how's the fuel`, `how much fuel do I need to finish the race when I
  pit on the next lap`
- **A sessão** — `who has the fastest lap`, `who's fastest`,
  `who has the fastest sector`, `who's in the lead`, `who's ahead`
- **Onde se perde o tempo** — `where am I slower`, `where am I faster`, qualquer
  delas com `than {piloto}` no fim

**As perguntas passam à frente na fila.** Uma pergunta feita a meio de um anúncio
do engenheiro ficava atrás dele ou era descartada de vez — a fila guarda seis e
uma volta movimentada enche-a — por isso perguntava, ouvia-o a falar de outra
coisa, e não obtinha resposta. Uma resposta agora limpa o tráfego vulgar, corta o
que está a ser dito, e não pode ser empurrada para fora. Continua a ceder ao
spotter, porque um carro ao lado é uma questão de não bater.

**Uma pergunta a que ele não sabe responder fica fora da janela de chat.** «Who's
faster?» não é uma expressão que ele conheça, e antes passava e ia para a sessão.
Tudo o que se lê como pergunta — acaba em ponto de interrogação, ou começa por um
interrogativo — recebe «say again» em vez disso. Há uma caixa no separador Chat de
texto se preferir o comportamento antigo, e uma pergunta que tenha desligado
explicitamente chega à mesma ao chat, porque desligá-la é a sua forma de dizer que
aquelas palavras são suas.

Pode pôr o nome do engenheiro em qualquer das pontas: «Bono, how are the tyres» e
«how are the tyres, Bono» funcionam ambas. É a vírgula que o marca como nome, por
isso `focus on Bono` continua a focar um piloto chamado Bono.

### Onde sou mais lento

A que vale mesmo a pena conhecer. Compara-o com o seu foco **curva a curva, com
média sobre todas as voltas desta sessão** em vez de ser lida de uma só — uma
volta isolada diz o que aconteceu naquela volta, e a pergunta é sobre o que
continua a acontecer.

> Chief, where am I slower
>
> *Curva três, é mais lento à entrada, dois décimos.*
>
> *Curva sete, ele tem melhor saída, um décimo.*

Diz *como*, não só onde: entrada, saída, travar mais tarde, ou mais lento em toda
a curva. Onde existir um catálogo de curvas para o circuito, usa o nome — «Eau
Rouge» em vez de «curva três».

**Como encontra as curvas.** Não há mapa do traçado e não vai haver — exigiria um
ficheiro por circuito, ficaria desatualizado a cada mudança de configuração, e
funcionaria nas quatro pistas que alguém tivesse tido tempo de fazer. Uma curva é
um sítio onde a volta de referência abrandou e voltou a acelerar, o que é
verdade em todos os circuitos de todos os simuladores. As chicanes contam como uma
só curva.

**Descreve, não instrui.** «Ele tem melhor saída» é o que a aplicação sabe. Não
sabe se foi a trajetória, os pneus ou o vácuo, e «trave mais tarde» seria um
palpite vestido de coaching.

**Se faltarem voltas, diz de quem.** Suas ou dele — de outro modo «sem voltas para
comparar» deixa-o a adivinhar quais.

### O que não usará como referência

- Uma volta com qualquer parte na via das boxes. Uma volta rápida que na verdade
  foi um atalho pelas boxes tornar-se-ia de outro modo o alvo com que todos são
  medidos, e nada nela pareceria errado.
- Uma volta a que se juntou a meio.
- Uma volta para a qual o simulador não deu tempo — uma volta de saída, ou um
  carro que acabou de chegar.
- Qualquer coisa de outro circuito. Mudar de traçado limpa tudo.

Também se cala enquanto está a assistir. Comentar uma volta que está a ver em vez
de conduzir não faria sentido.

---

## Quando o seu simulador não consegue responder

Nem todos os simuladores publicam as mesmas coisas, e o engenheiro di-lo em vez de
adivinhar. O Assetto Corsa original, por exemplo, publica **o seu próprio carro e
nada sobre mais ninguém** — nem nome, nem posição, nem tempo de volta de outro
piloto — pelo que tudo o que o compara com a grelha não tem dados por via nenhuma.

Pergunte-lhe aí «who's leading» e ele responde **«este jogo não diz»**. É
deliberado e não é o mesmo que «não há ninguém para observar», que significa que a
grelha está mesmo vazia. Dizer a um piloto que está em sétimo que não há ninguém à
frente dele não é uma resposta inútil, é uma resposta falsa.

Comportamentos que precisam de dados que o seu simulador não fornece são ignorados
com uma linha no registo em vez de ficarem ligados e mudos:

```
Spotter is on but this sim does not publish positions or spotter; it will stay quiet
```

`--telemetry` imprime o que o seu simulador está de facto a enviar — veja a última
secção.

---

## Outros idiomas

O engenheiro fala o idioma que definiu para a **transcrição**, a não ser que o
fixe no separador Engenheiro. É a predefinição certa e não uma arbitrária: os seus
comandos chegam através do Whisper, portanto se o Whisper está a produzir
espanhol, um engenheiro à escuta de expressões inglesas nunca ouvirá uma única.

Tudo o que ele diz — incluindo as expressões de ativação — passa pelos mesmos
catálogos de tradução da janela. Acrescentar um idioma é um ficheiro JSON em
`src/pitradio/locale/`; veja o README principal.

**Os números são escritos por extenso em inglês e lidos como algarismos em todo o
resto.** Não é preguiça: a gramática dos números é genuinamente específica de cada
língua — o alemão inverte dezenas e unidades, o espanhol funde os vintes — e uma
implementação feita a meio produziria disparates ditos com confiança na língua de
alguém. Os algarismos entregam o problema ao motor de voz dessa língua, que já o
resolve corretamente. O efeito colateral é que um pacote de voz não inglês não
consegue cobrir números, e estes saem sintetizados.

---

## Pacotes de voz

**De que pacote fala este engenheiro define-se aqui, no separador Engenheiro**, e
o coach escolhe o seu no separador Coaching — são dois trabalhos distintos e um
piloto pode razoavelmente querer ouvir qual dos dois está a falar.

**Instalar, gravar e remover pacotes é Definições → Voz.** Um pacote é algo que a
aplicação possui; aquele de que uma persona fala é uma definição dessa persona.

Vêm dois pacotes: **Norman** e **Claudia**. Ambos foram gerados com o Piper — veja
[voicepacks.md](voicepacks.md) — e qualquer um pode ser substituído por um pacote
seu.

Um pacote de voz substitui o sintetizador por áudio gravado: uma pasta de
ficheiros WAV, uma pasta por expressão, várias tomadas cada uma. O engenheiro
escolhe uma tomada ao acaso, e é isso, sobretudo, que faz um pacote soar a pessoa
e a síntese de fala não.

**A disposição é a do Crew Chief**, de propósito:

```
%APPDATA%\pitradio\voices\
  Ada\
    voice\
      corners\
        two_tenths\
          a.wav
          b.wav
```

Um `<pacote>/<expressão>/*.wav` plano também funciona, e é o que se obtém ao gravar
por sua conta.

Essa disposição faz com que um pacote gerado pelo
[crew-chief-autovoicepack](https://github.com/cktlco/crew-chief-autovoicepack)
possa ser colocado tal como está. Para gerar um para as expressões do SimPitRadio
em vez das do Crew Chief:

1. Definições → **Voz** → **Escrever lista de expressões**. Isto escreve
   `phrase_inventory.csv` na pasta de vozes, no idioma do engenheiro.
2. Dê essa lista ao gerador em vez da dele.
3. Ponha a pasta de saída sob `voices\` e escolha-a no separador Engenheiro (ou
   use **Definições → Voz → Abrir pasta de pacotes de voz** para lá chegar).

**Nomes e números nunca estão num pacote** e são sempre ditos pela voz do Windows.
Não há como contornar — nenhum pacote consegue conter o nome de todos os pilotos
nem todos os tempos de volta — pelo que um anúncio como «curva quatro, o Tandy foi
mais rápido à saída» é em parte gravado e em parte sintetizado. Essa costura
ouve-se. Continua a ser o compromisso certo: a alternativa é um pacote que deixa de
ser usado assim que um piloto é nomeado, o que é a maioria dos anúncios.

Os pacotes são guardados ao lado da sua configuração, não na pasta de instalação,
para que uma atualização não apague um gigabyte de áudio que escolheu instalar.

---

## Como tudo encaixa

O engenheiro corre **na sua própria thread**, separada das quatro que o
SimPitRadio já tem, e falar ganha uma thread abaixo dessa. Nenhuma delas pode
segurar o hook de teclado, o worker ou a janela.

Tudo o que ele faz tem o direito de falhar. O engenheiro ficar calado nunca lhe
pode custar um disparo, uma transcrição ou uma mensagem no chat — por isso, se
alguma coisa aqui se partir, as palavras vão para a janela de chat como sempre
foram e o problema é uma linha no registo.

Lê o simulador dez vezes por segundo através do mesmo plugin que fornece os nomes
dos pilotos para as menções. Não há um segundo caminho de dados nem uma ligação
extra ao jogo.

---

## Nada é dito

**O Testar não faz nada.** O sintetizador corre num host de PowerShell usando
`System.Speech`, que faz parte do .NET Framework em todas as máquinas Windows 10 e
11. Procure `no speech host` no registo — uma máquina bloqueada com o PowerShell
impedido é a causa habitual.

**Consegue ouvi-lo, mas não nos auscultadores.** Defina o dispositivo de saída no
separador Áudio. Por predefinição usa o dispositivo do sistema, que durante uma
corrida é muitas vezes a coluna do volante.

**Lê tempos de volta mas nunca faz coaching.** O coach de curva precisa de uma
volta de referência. Até o piloto que escolheu ter completado uma — limpa, não
pelas boxes — não há nada com que comparar. A linha de estado do separador
Engenheiro diz quantas curvas já mapeou.

**Faz coaching mas não diz nada em algumas curvas.** É o desenho: essas curvas
estavam dentro do limiar. Baixe o **Limiar de curva** se quiser mais.

**Não responde a nada do que diz.** Verifique o nome no separador Engenheiro, e
lembre-se de que qualquer expressão que leve um piloto precisa do nome à frente.
Diga «Chief» sozinho — se obtiver «go ahead», está a ouvir e o problema é a
expressão.

**Comeu uma mensagem.** Não devia. Se o engenheiro apanhou algo que queria enviar,
a linha do registo diz `that was for the engineer` juntamente com aquilo com que
correspondeu — por favor abra um problema com essa linha, porque um matcher
demasiado zeloso é o único bug desta funcionalidade que custa algo de real.

---

## Verificar o que o seu simulador está mesmo a enviar

A maioria dos problemas de «o engenheiro não diz nada» não é o engenheiro. Inicie
o jogo, ponha-se **em pista e em movimento**, depois:

```bash
python -m pitradio --telemetry
```

Imprime cada carro tal como o engenheiro o vê — distância na volta, velocidade,
contagem de voltas, setor, tempos, bandeira de boxes, posição no mundo — e, mais
útil ainda, compara leituras consecutivas e diz-lhe se alguma coisa está a mudar.

Essa última parte importa mais do que parece. Um simulador em pausa ou parado num
menu continua a publicar um bloco que parece completamente saudável: carros,
posições, velocidades, tudo plausível. Nada se mexe, portanto o engenheiro não tem
nada a dizer, e nenhuma imagem isolada mostra isso. Se reportar

> Nothing changed across 4 reads, including the sim's own clock.

então o jogo está em pausa, num menu, ou a sessão terminou — não está avariado.

O que observar quando *está* vivo:

| Coluna | Alimenta |
| --- | --- |
| `lapdist`, `speed` | a deteção de curvas, e onde se perde o tempo |
| `lap`, `last lap`, `best lap` | os anúncios de tempo de volta e volta mais rápida |
| `sec` — muda três vezes por volta | todos os anúncios de setor |
| `world x/y/z` — diferente por carro | o spotter |

A linha `provides:` no topo diz quais destas coisas o plugin afirma fornecer. Um
comportamento que precise de algo em falta é ignorado em vez de ficar ligado e
mudo, e o registo diz que capacidade falta.

## O que cada simulador consegue fazer

Os simuladores publicam coisas muito diferentes, e um comportamento cujos dados
faltam é **ignorado com uma linha no registo** em vez de ficar ligado e mudo.

| | Le Mans Ultimate | iRacing | Assetto Corsa / Competizione / Evo | Automobilista 2, Project CARS 2 / 3 |
| --- | --- | --- | --- | --- |
| Tempos de volta | sim | sim | sim | derivados |
| Nova volta mais rápida | sim | sim | — | sim |
| Anúncios de setor | sim | — | sim | — |
| Onde sou mais lento | qualquer piloto | qualquer piloto | a sua própria melhor | qualquer piloto |
| Quem está à frente / na liderança | sim | sim | — | sim |
| Spotter | geometria | o anúncio do próprio simulador | só o Competizione | geometria |
| Menções a pilotos, «P3» | sim | sim | — | sim |
| Danos | sim | — | — | — |
| Coaching e o diagrama de segmento | sim | — | — | — |

As lacunas são dos jogos, não da aplicação:

- **O iRacing** não publica tempos de setor por carro, portanto os anúncios de
  setor não têm com que trabalhar. O seu spotter é o melhor de todos — o
  `CarLeftRight` vem das carroçarias reais, pelo que não precisa de definição de
  troca nem de estimativa de largura.
- **O Assetto Corsa** publica tempos de volta apenas para o seu carro e nenhum
  nome de piloto. É por isso que não há classificações nem menções, e é por isso
  que «onde sou mais lento» persegue a sua própria melhor volta — que é para isso
  que serve uma sessão de treinos, de qualquer forma.

  O jogo original vai mais longe: não publica **nenhum outro carro**, nem sequer
  uma posição. Verificado contra uma corrida real de oito carros, o vetor de
  coordenadas tinha o jogador na posição zero e memória intacta em todas as
  outras — zeros, um NaN, um desnormalizado. Portanto o spotter também não tem lá
  nada com que trabalhar, e o plugin di-lo por sessão e não por jogo: **o
  Competizione publica** esse vetor, e o mesmo plugin reporta posições nele.
- **O Automobilista 2 e o Project CARS** trazem *contagens* de voltas em vez de
  tempos na parte do bloco em que vale a pena confiar, pelo que os tempos são aqui
  medidos a cronómetro. Uma volta que atravesse uma pausa sai mais longa do que
  foi; isso falha para o lado seguro, uma vez que uma volta inflacionada nunca se
  torna a referência que uma comparação persegue. O campo de setor deles é um enum
  que não foi possível determinar a partir de fora dos jogos, pelo que os anúncios
  de setor não são oferecidos.

O Automobilista 2 tem entrada própria em vez de partilhar a do Project CARS, para
que possa escolher o jogo que está mesmo a correr e para que os dois mantenham
definições de spotter e de proximidade separadas.

**O Le Mans Ultimate é o único verificado contra o jogo em execução.** Todos os
outros leitores são testados contra memória partilhada construída à mão, o que
apanha uma largura de campo errada, um nome mal descodificado ou um erro de
preenchimento — e não consegue apanhar um pressuposto errado sobre o que o
simulador põe onde. Execute `--telemetry` com o jogo em pista antes de confiar em
qualquer um deles, e sobretudo no Assetto Corsa Evo, que ainda está em acesso
antecipado e pode mudar a sua disposição.

**O iRacing está marcado como experimental**, e aparece assim no seletor de
perfis. Não por ser pior código do que os outros, mas porque ninguém a trabalhar
no SimPitRadio tem uma cópia — por isso, ao contrário dos restantes, não será
verificado contra a realidade a não ser que alguém que o tenha corra `--telemetry`
e diga o que veio. Se for você, por favor faça-o; a nota na lista de plugins pede
exatamente isso.

## Definições por simulador

Três dos números do engenheiro vivem no **perfil**, sob as definições do plugin do
jogo, e não no separador Engenheiro — porque descrevem o jogo e não o seu gosto:

- **Trocar os lados do spotter** — se «esquerda» significa um carro à sua direita
- **Sobreposição do spotter (metros)** — que distância ao longo da pista ainda
  conta como lado a lado. Um Hypercar tem cerca de 5 m
- **Largura do spotter (metros)** — até onde para o lado conta, antes de estarem
  simplesmente noutra parte do circuito

Os comprimentos dos carros e as convenções de eixos diferem entre simuladores, por
isso um número que serve num jogo está errado no seguinte.

## Bandeiras e incidentes

Um comportamento próprio, e separado do spotter deliberadamente. As próprias
pastas de sons do Crew Chief traçam a linha e é a linha certa: `car_left`,
`still_there` e `clear_all_round` estão em `spotter/`, ao passo que
`stopped_car_in_turn_3`, `slow_car_ahead` e `local_yellow_ahead` estão em
`flags/`. O spotter responde a «quem está ao meu lado», que é geometria. As
bandeiras respondem a «o que aconteceu à pista», que não é.

Derivar o segundo do primeiro é o que produzia um aviso em todas as zonas de
travagem: o SimPitRadio tinha uma regra que dizia que um carro muito mais lento do
que você era um perigo, e uma zona de travagem é precisamente onde o carro da
frente é muito mais lento do que você. Essa regra desapareceu.

**Três fontes, não igualmente fiáveis.**

A *bandeira amarela em todo o circuito* e a *azul* vêm do simulador e são fiáveis
— o `mGamePhase`, o `mYellowFlagState` e o `mFlag` por carro do LMU leem-se todos
sensatamente contra uma sessão ao vivo.

Os *amarelos locais são derivados*, porque o `mSectorFlag` do LMU não é utilizável.
Está documentado como «se há amarelos locais neste momento em cada setor» e lê
`[11, 11, 1]` sob bandeira verde, com os campos de ambos os lados corretos — não é
portanto um desvio que escorregou, o LMU publica simplesmente outra coisa ali.
Lido como booleanos, poria um amarelo permanente em todo o circuito. Assim, um
incidente aqui significa o que um comissário entende por isso: um carro parou na
estrada e está ali há dois segundos. É uma derivação a partir de dados que o
simulador publica honestamente, no mesmo espírito de encontrar as curvas no traço
de velocidade em vez de distribuir um mapa do traçado.

O custo é que o anúncio não pode preceder o incidente — um amarelo a sério está
fora no momento em que os comissários o veem, e este espera para ter a certeza. O
benefício é que nunca se engana quanto a uma pista verde, que é a falha que leva as
pessoas a desligar uma funcionalidade.

**Os incidentes são nomeados por curva, não por piloto.** À velocidade a que isto
importa, «curva seis» é algo sobre o qual um piloto pode agir e um nome é uma
contagem de sílabas sobre a qual não pode. A numeração é a do caderno de voltas,
para que um piloto ouça um só conjunto de números de curva em vez de uma
funcionalidade usar um e as bandeiras outro; as curvas são encontradas uma vez por
volta de referência e guardadas em cache, porque `find_corners` reamostra uma volta
inteira e isto corre várias vezes por segundo. Sem volta de referência ainda, é o
setor que é nomeado.

**Quando o incidente é você, os anúncios laterais param.** Descrever ao piloto de
um carro atravessado os carros que passam é ruído; a única pergunta útil é se há
espaço para arrancar, e [rejoin.py](../src/pitradio/engineer/rejoin.py)
responde-lhe — comparando *o tempo até estar em segurança* com *o tempo até chegar
o próximo carro*, e não distância com distância. Um carro parado precisa de
recuperar toda a sua aceleração antes da primeira chegada. É por isso que a
resposta ingénua de «três segundos de pista livre» faz com que as pessoas sejam
apanhadas.

Duas salvaguardas, ambas aprendidas e não presumidas: nada é dito na via das
boxes, onde estar parado é o objetivo, e nada antes de o carro alguma vez se ter
movido — estar na grelha antes dos semáforos é estar parado, na trajetória, com
todo o pelotão atrás, que é exatamente cada entrada que o conselho de regresso à
pista observa.

Veja [voicepacks.md](voicepacks.md) para gerar uma voz.

## Perguntas

Distintas dos comportamentos, e a distinção não é contabilidade. Um comportamento
é algo que o engenheiro *continua a fazer* — veja [O que ele lhe
diz](#o-que-ele-lhe-diz) — e traz um intervalo de repetição, porque um carro ao
lado deixa de estar ali sem que nada aconteça. Uma pergunta tem uma resposta, e
quando a resposta foi dada não há nada a correr. Modelar uma como a outra poria
«who has the fastest lap» na lista de Comportamentos, onde cada entrada tem um
intervalo de repetição, e não existe tal coisa como responder de novo a uma
pergunta a cada 1,2 segundos.

Três delas: a volta mais rápida, o setor mais rápido, e a sua própria melhor.

**O parâmetro segue a palavra-chave e nunca faz parte da expressão.** Aquilo por
que um piloto pode perguntar depende do simulador em que está — as classes desta
grelha, os setores que este circuito tem — e nada disso pertence a uma expressão
que alguém escreveu numa caixa de definições. «Who has the fastest sector» é a
expressão; «three in GT3» é o que veio a seguir, analisado contra a sessão. Uma
classe é reconhecida através de `mentions.class_aliases`, pelo que o «LMGT3» do
LMU responde a «GT3» exatamente como em todo o lado, e «LMP2» continua a recusar
responder a «P2» porque isso é uma posição.

**Um espaço de argumentos fechado é a defesa contra falsos positivos**, e melhor do
que contar palavras. `phrases.MIN_BARE_WORDS` protege os comandos falados exigindo
duas palavras à frente de um parâmetro aberto; aqui não chega, porque «who has the
fastest lap of my life that one» passa isso facilmente e seria tomado como uma
pergunta sobre uma classe chamada «of my life that one» — engolindo a mensagem. Mas
o argumento de uma pergunta só pode ser uma classe desta grelha, um setor entre um
e três, ou nada. Tudo o resto não era uma pergunta, seja lá com o que tenha
começado. Interpelado pelo nome é-o de qualquer maneira: quem disse o nome do
engenheiro estava a falar com ele.

**Nenhuma classe nomeada significa a sua própria classe**, porque é isso que
alguém num GT3 quer dizer ao perguntar «who has the fastest lap». Uma classe
nomeada em que ninguém está recebe essa informação em vez de ser silenciosamente
servida com o valor global — uma resposta errada dita com confiança é o modo de
falha sem sintoma.

Cada uma tem uma caixa no separador Engenheiro e mais nada. Aquilo sobre que uma
pergunta pode incidir está fixado pelo que o simulador publica, portanto uma caixa
de expressões editável ali daria a entender que podia inventar uma.

O interruptor merece o seu lugar por outra razão: **cada expressão que o engenheiro
escuta é uma expressão que pode ser retirada de uma mensagem destinada a toda a
sessão**, e quem nunca faz estas perguntas não tem motivo para correr esse risco.
Desligar uma remove as suas expressões do matcher por completo em vez de a
silenciar mais à frente — de outro modo «who has the fastest lap» continuaria a ser
retirada da mensagem e depois respondida com nada, que é o pior dos dois. Ausente da
configuração significa ligada, portanto acrescentar uma pergunta nunca exige uma
migração.

## O spotter, e de onde vêm os seus números

Cada limiar em `spotter.py` é o do Crew Chief, lido de uma instalação local em vez
de adivinhado — o seu `ui_text/en.txt` nomeia cada definição e o
`CrewChiefV4.exe.config` traz os valores predefinidos:

| O nosso | O do Crew Chief | Predefinição |
| --- | --- | --- |
| `DEFAULT_CAR_LENGTH` | `lmu_spotter_car_length` | 4,5 (5 para pcars2/ACC, 4,4 para AMS2) |
| `GAP_FOR_CLEAR` | `spotter_gap_for_clear` | 0,5 m |
| `OVERLAP_DELAY` | `spotter_overlap_delay` | 50 ms |
| `CLEAR_DELAY` | `spotter_clear_delay` | 150 ms |
| `MIN_SPEED` | `min_speed_for_spotter` | 10 m/s |
| `MAX_CLOSING_SPEED` | `max_closing_speed_for_spotter` | 12 m/s |
| o intervalo de repetição | `spotter_hold_repeat_frequency` | 3 s |

Três deles faltavam aqui por completo e cada um provocava uma falha que o piloto
conseguia sentir:

**O limite de velocidade de aproximação é o que apanha o carro que dobra.** Algo
que chega 12 m/s mais depressa atravessa toda a janela de sobreposição em bem menos
de um segundo, pelo que, quando o anúncio é dito, já passou — e o piloto mantém uma
trajetória por um carro que já não está lá.

**A velocidade mínima é o que trava a via das boxes e a grelha.** Abaixo de 10 m/s
os carros à sua volta estão parados ou passam a passo, e anunciá-los é a forma como
um spotter acaba desligado.

**Os dois atrasos de estabilização são o que trava a tagarelice.** Dois carros na
mesma curva entram e saem da sobreposição ao ritmo da respiração. São
deliberadamente de comprimentos diferentes: o atraso de sobreposição é curto porque
um aviso que chega tarde não vale nada, e o atraso de libertação é mais longo
porque se pode dar ao luxo de ter a certeza — um piloto que mantém a sua linha um
décimo mais do que o necessário não perdeu nada.

O alcance de libertação é `comprimento do carro + folga`, não um segundo múltiplo
do comprimento. A distinção importa nos extremos: para um kart, «mais um
comprimento de carro» são dois metros de histerese e o anúncio arrasta-se durante
demasiado tempo, ao passo que meio metro de luz é meio metro seja lá o que for que
conduza.

**O spotter fica calado sob bandeira amarela em todo o circuito** — o
`fcy_stop_spotter_immediately` do Crew Chief, ligado por predefinição. O pelotão
está agrupado ao passo e permanentemente sobreposto, pelo que todos os anúncios
seriam verdadeiros e inúteis.

### O que diz

O vocabulário é a pasta `Sounds/voice/spotter/` do Crew Chief, portanto um pacote
de voz construído para o Crew Chief di-lo todo sem mapeamento: `car_left`,
`car_right`, `still_there`, `hold_your_line`, `in_the_middle`, `clear_left`,
`clear_right`, `clear_all_round`, `three_wide_on_left`, `three_wide_on_right`.

Dois deles substituíram anúncios que enunciavam o mesmo facto pelo caminho mais
difícil:

* **«Three wide, you're on the right»** era «two cars left». Um piloto que ouve o
  antigo tem de calcular onde isso o deixa, enquanto está ocupado; o novo diz
  diretamente para que lado não há espaço.
* **«In the middle»** era «three wide», para um carro de cada lado.

Uma repetição diz `still there` de um lado e `hold your line` de ambos, porque são
instruções diferentes — uma significa não vá por ali, a outra significa não se
mexa. A chegada e as suas repetições partilham uma chave derivada das *contagens*,
para que o intervalo de repetição as governe; uma chave que mudasse com a
formulação faria do seguimento um anúncio novo, devido logo no tick seguinte.

**O conjunto de ovais está deliberadamente ausente** — `car_inside`,
`clear_outside`, `three_wide_on_inside`. Que lado é o interior é um facto sobre a
inclinação, que nenhum dos simuladores aqui publica e que o Crew Chief guarda por
pista. Adivinhá-lo é um anúncio confiantemente ao contrário.

### Combustível

«How much fuel do I need to finish the race when I pit on the next lap», ou
«...when I pit in five laps». **A resposta é uma percentagem**, porque é esse o
número no próprio ecrã de combustível do simulador e o piloto tem cerca de quatro
segundos a caminho da entrada das boxes para o marcar. Os litros são a conta.

**O consumo é medido, nunca presumido.** O consumo de um carro depende do circuito,
do mapa de motor, do tráfego e de como a pessoa o conduz, portanto os litros por
volta aqui são o que *este* carro tem gasto *nestas* voltas — uma média móvel
curta, para que acompanhe uma mudança de mapa em vez de ser puxada para trás por um
stint inteiro. Até uma volta estar completa não há resposta e ele di-lo. Um número
de combustível inventado do nada é a única resposta errada aqui que termina a
corrida de alguém.

Três pormenores que de outro modo seriam redescobertos:

* **As voltas antes da paragem não são abastecidas.** O que está no depósito agora
  cobre-as. Só as posteriores são a pergunta, e é por isso que isto nunca lê o
  nível atual.
* **`mMaxLaps` é `INT_MAX` numa sessão por tempo.** Tomado à letra, pede
  combustível para dois mil milhões de voltas. `SessionInfo` traz `max_laps` *ou*
  `ends_at`, nunca ambos, e é o plugin que decide qual — o engenheiro nunca
  adivinha o que falta. Uma corrida por tempo divide o relógio restante pela melhor
  volta do próprio piloto e arredonda **para cima**, porque a bandeira cai no fim da
  volta em que está quando o tempo acaba.
* **Um enchimento acima da capacidade do depósito é reportado, não cortado.**
  Significa que a paragem não pode ser a última, e um piloto a quem se diz «cem por
  cento» sem lhe dizer isso planeia uma corrida que não funciona.

Tudo o resto arredonda no sentido de mais combustível: ficar sem é uma desistência e
levar um litro a mais é um décimo por volta.

O combustível chega a `Car` **apenas para o carro do jogador** — os simuladores
publicam telemetria de depósito para o carro que está a conduzir e de mais ninguém —
e é ligado através da correspondência de `mID`, porque o vetor de telemetria do LMU
é indexado por `playerVehicleIdx` enquanto o vetor de classificação não é. Ligá-lo
por posição poria o seu depósito no carro que por acaso estivesse classificado
nessa casa.

## Estar longe do volante

O engenheiro não diz nada, e **não regista nada**, quando o piloto não está a
conduzir. Três estados, e precisam de três sinais diferentes:

* **Em pausa** — o relógio do simulador para enquanto o desta máquina não, e a
  diferença é o sinal. Não o `mGamePhase`: esse indicava *bandeira verde* durante
  toda uma sessão passada em pausa na garagem, com `mCurrentET` congelado em
  2218.0. A fase diz que tipo de sessão é, não se está a decorrer.
* **Na garagem** — aqui o relógio continua, portanto o relógio não pode ser o sinal.
  O `mInGarageStall` é. Distinto de `in_pits`, que cobre toda a via das boxes: um
  carro a cumprir uma paragem está a correr.
* **Entregue à IA** — `mControl` é 1, que é o aspeto de estar a assistir.

**Também nada é observado, não é apenas nada dito.** Um simulador em pausa
republica o mesmo fotograma para sempre, e dar isso ao caderno de voltas regista um
carro que não percorre distância nenhuma durante todo o tempo em que alguém deixar
o jogo ali parado — uma volta de referência corrompida em vez de uma volta em
falta. O estado do spotter é descartado à entrada pela mesma razão: um carro que
estava ao lado antes da pausa é um facto sobre um instante que já passou.

**Pôr em pausa uma corrida online não é detetado, e não pode ser.** O relógio ali
continua, porque a corrida continua — o menu está aberto nesta máquina e os carros
continuam a andar. Nada na memória partilhada separa isso de correr normalmente, e
inventar um sinal para tal calaria o engenheiro durante uma corrida a sério. O que
é o pior dos dois erros.
