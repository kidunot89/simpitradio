# O engenheiro

Uma voz com nome que acompanha o simulador e fala contigo: os teus tempos de
volta, os carros ao lado, e respostas quando lhe perguntas alguma coisa.

Partilha o acionamento com tudo o resto que o SimPitRadio faz. Mantém o
acionamento, diz «Chief, concentra-te em P3», larga — isso vai para o
engenheiro em vez de ir para a caixa de chat, e é o engenheiro que responde.

**Está desligado até o ligares.** Nada é dito até ires a Definições →
Engenheiro e marcares a caixa.

---

## Começo rápido

1. Abre **Definições → Engenheiro** e marca **Engenheiro ligado**.
2. Escolhe um dos quatro engenheiros. Isso define o nome, a voz e o quanto ele
   fala.
3. Carrega em **Testar**. Deves ouvi-lo repetir o próprio nome.
4. Define o **Dispositivo de saída** para os teus auscultadores — os mesmos
   que usas para o chat de voz, não a saída do simulador.
5. Conduz. Ele lê o teu tempo de volta na linha.
6. Mantém o acionamento e diz **«Chief, concentra-te em P3»** para seres
   medido contra quem estiver em terceiro.

Se o Testar não disser nada, vê [Nada é dito](#nada-é-dito) no fim.

---

## Falar com ele

Duas formas de uma frase se tornar um comando, e ambas são deliberadamente
estreitas. A mesma tecla envia mensagens a toda a gente na tua sessão, por
isso um comando que o engenheiro *invente* é uma mensagem que, em silêncio,
nunca chega.

**Diz o nome dele primeiro.** «Chief, concentra-te em P3.» O nome vem
primeiro, a expressão vem logo a seguir. `hey`, `ok` e `right` são permitidos
antes do nome.

**Ou diz uma expressão sozinha**, desde que tenha duas palavras e não leve um
piloto. «treina-me» funciona sem nada à frente. «estuda» tem uma só palavra,
podia abrir uma frase vulgar, e tudo o que vem a seguir é o nome do piloto,
por isso precisa do nome do engenheiro primeiro. Dita sozinha, *estuda P2*
foi para a caixa de chat oito vezes numa sessão, interpretada como uma menção
a um piloto e enviada a toda a gente.

Dizer só o nome dá «pode falar», tal como um rádio a sério, e mantém um
«Chief» perdido fora de uma mensagem para outras vinte pessoas.

**«Stop»** funciona sempre, seja o que for que esteja a decorrer e seja o que
for que o tenha iniciado. O mesmo vale para «stand down», «cancel», «that's
enough» e «forget it».

Tudo o que o engenheiro não reconhece é uma mensagem, e vai para a caixa de
chat exatamente como antes.

---

## Escolher um engenheiro

Vêm quatro com a aplicação:

| | Voz | Estilo |
| --- | --- | --- |
| **Chief** | masculina | Calmo e completo. «Curva quatro, o Tandy foi mais rápido à saída, dois décimos.» |
| **Ada** | feminina | Seca. Omite o número da curva: «Tandy, saída mais rápida, dois décimos.» |
| **Marshall** | masculina | Mais lento e mais completo, se os outros parecerem apressados. |
| **Vic** | feminina | Rápida e curta. A que menos fala dos quatro. |

Cada um é uma predefinição: um nome, uma voz do Windows preferida, um ritmo, e
o quanto diz. Nenhum deles é uma gravação. Um pacote de voz gerado tem um a
dois gigabytes, por isso quatro conjuntos de áudio seriam um download de oito
gigabytes para substituir algo que já está de graça em qualquer máquina
Windows.

Cada um escolhe a melhor voz do Windows instalada que corresponda à sua
preferência e ao teu idioma. Uma instalação normal do Windows 11 tem
normalmente duas ou três, por isso dois engenheiros podem partilhar uma voz e
distinguir-se pelo ritmo e pela formulação. Define **Voz do Windows** para
sobrepor a predefinição.

**Chama-se** é aquilo a que ele responde. Põe o que quiseres — o nome só
serve para o interpelar, e «Bob, concentra-te em P3» funciona exatamente
igual.

---

## O que ele te diz

### Tempos de volta

Lê a tua volta quando cruzas a linha, e diz quando foi a tua melhor. Ligado
por predefinição.

### Spotter

Anuncia carros ao lado: «carro à esquerda», «carro à direita», «no meio»
quando há um de cada lado, e depois «livre» assim que se afastam. Desligado
por predefinição, e há uma coisa a saber sobre ele.

**Qual o lado certo não pôde ser verificado sem um carro numa pista.** As
posições vêm das coordenadas de mundo do próprio simulador, e se as contas
dão esquerda ou direita depende de uma convenção de orientação que este
projeto não conseguiu confirmar a partir de uma máquina de desenvolvimento.
Se ele chamar «esquerda» a um carro à tua direita, liga **Trocar os lados do
spotter** em Perfis, nas definições do plugin de sessão do jogo. É uma marca,
uma vez.

Tudo o resto no spotter é exato. Usa as posições no jogo, descarta a altura —
para que uma ponte ou as esses de Le Mans não ponham ninguém encostado à tua
porta — e não anuncia carros numa reta adjacente.

### Danos

Diz o que se partiu e se deves entrar por causa disso. Ligado por
predefinição, e precisa de um simulador que publique o estado do carro —
hoje, é o Le Mans Ultimate.

> *Perdeste carroçaria. Às boxes nesta volta.*

**Fala no momento em que o carro piora, depois cala-se.** Um piloto que
carrega uma traseira esquerda amolgada durante meia hora não precisa de ser
lembrado disso a cada passagem. Cada parte da leitura é vigiada, e não só a
pior, por isso uma segunda peça a soltar-se de um carro já amolgado é
novidade, mesmo que a gravidade não tenha mudado.

**O que diz é onde, e depois se.** Já sabes que bateste em qualquer coisa. O
que não vês do banco é o quão mau é e se há tempo para reparar, por isso
nomeia o sítio: o nariz, a traseira, todo o lado esquerdo. Depois dá uma de
três respostas.

| | |
| --- | --- |
| **Às boxes nesta volta** | o carro não pode ser corrido, só trazido devagar: uma peça pendurada, um furo, uma roda perdida ou um nariz partido. O tempo que resta não muda isto — a alternativa é bandeira negra ou um muro |
| **Às boxes quando puderes** | vale a pena reparar. Sempre em treinos e qualificação, onde uma paragem não custa nada e o objetivo de estar em pista é ter um carro que funcione |
| **Fica fora, vivemos com isso** | uma corrida com menos de um quinto por correr. A três voltas do fim, é melhor levar um carro maltratado à bandeira do que devolver um minuto |

Um dano ligeiro recebe a primeira metade e nenhum conselho. Ouvir que deves
pesar uma paragem por um guarda-lamas traseiro riscado é pior do que não
ouvir nada.

Nunca fala por cima do treinador. Os danos são urgentes — queres saber que a
asa se foi antes da curva seguinte, não depois — mas uma crítica que pediste
ainda não merece ser cortada por um carro que daqui a quatro segundos vai
estar igualmente partido. O spotter é o único anúncio que fala por cima de
seja o que for.

---

## Quem ele observa

O engenheiro mantém um **foco**: um piloto contra quem te mede. Não tens de o
definir. Por predefinição é **o carro à frente na tua classe**, ou o carro
atrás quando és tu a liderá-la — porque não há ninguém à frente para
perseguir, e a pergunta passa a ser se os estás a manter atrás.

Só segue uma mudança depois de a posição se **manter oito segundos**. As
posições fervilham: medido num arranque de corrida real, quinze pilotos
diferentes foram o carro da frente em noventa segundos, e cada troca deitava
fora as voltas acumuladas, por isso nunca tinha o suficiente para dizer fosse
o que fosse.

Diz-lhe se quiseres outra pessoa:

- `concentra-te em {piloto}` — ou «fica de olho em», «vigia», «estuda»,
  «observa»
- `alvo por omissão` — de volta a escolher sozinho
- `deixa de te concentrar` — desligado, e fica desligado até seres chamado de
  novo

Um piloto que nomeies nunca é ignorado. Voltar duas curvas depois para quem
está à frente é a aplicação a discordar de ti.

O separador Estado mostra quem está a ser observado, e `quem estamos a
observar` pergunta-o.

---

## Perguntar-lhe coisas

Cada pergunta tem uma caixa de expressões em Definições → Engenheiro, uma por
linha, e o que escreveres substitui os valores predefinidos. Cada uma pode
ser desligada; uma pergunta desligada não contribui com expressão nenhuma,
por isso as suas palavras chegam à caixa de chat como quaisquer outras em vez
de serem apanhadas e respondidas com nada.

- **O teu carro**: `qual é a minha melhor volta`, `como estão os pneus`,
  `quais são os danos`, `como está o combustível`, `quanto combustível
  preciso para acabar a corrida se entrar nas boxes na próxima volta`
- **A sessão**: `quem tem a volta mais rápida`, `quem é o mais rápido`,
  `quem tem o melhor sector`, `quem vai na frente`, `quem vai à frente`
- **Onde se perde o tempo**: `onde sou mais lento`, `onde sou mais rápido`,
  qualquer uma delas com `than {piloto}` no fim

**As perguntas passam à frente na fila.** Uma pergunta feita a meio de um
anúncio do engenheiro costumava ficar atrás dele ou ser descartada de vez,
porque a fila guarda seis e uma volta movimentada enche-a. Perguntavas,
ouvia-lo a falar de outra coisa, e não obtinhas resposta. Uma resposta agora
limpa o tráfego vulgar, corta o que está a ser dito, e não pode ser empurrada
para fora. Continua a ceder ao spotter, porque um carro ao lado é uma questão
de não bater.

**Uma pergunta a que ele não sabe responder fica fora da caixa de chat.**
*«Quem é o mais rápido?»* não é uma expressão que ele conheça, e costumava
passar e ir para a sessão. Tudo o que se lê como pergunta — que acaba em
ponto de interrogação, ou começa por um interrogativo — recebe «repete» em
vez disso. Há uma caixa no separador Chat de texto se preferires o
comportamento antigo, e uma pergunta que tenhas desligado explicitamente
continua a chegar ao chat, porque desligá-la é a tua forma de dizeres que
aquelas palavras são tuas.

Podes pôr o nome do engenheiro em qualquer das pontas: «Bono, como estão os
pneus» e «como estão os pneus, Bono» funcionam ambas. É a vírgula que o marca
como nome, por isso `concentra-te em Bono` continua a focar um piloto chamado
Bono.

### Onde sou mais lento

A que vale mesmo a pena conhecer. Compara-te com o teu foco **curva a curva,
com média sobre todas as voltas desta sessão**, em vez de ser lida de uma só.
Uma volta isolada diz o que aconteceu naquela volta, e a pergunta é sobre o
que continua a acontecer.

> Chief, onde sou mais lento
>
> *Curva três, és mais lento à entrada, dois décimos.*
>
> *Curva sete, têm melhor saída, um décimo.*

Diz *como*, não só onde: entrada, saída, travar mais tarde, ou mais lento em
toda a curva. Onde existir um catálogo de curvas para o circuito, usa o nome
— «Eau Rouge» em vez de «curva três».

**Como encontra as curvas.** Não há mapa do traçado e não vai haver. Um mapa
precisaria de um ficheiro por circuito, ficaria desatualizado a cada mudança
de layout, e funcionaria nas quatro pistas a que alguém tivesse tido tempo de
chegar. Uma curva é um sítio onde a volta de referência abrandou e voltou a
acelerar, o que é verdade em todos os circuitos de todos os simuladores. As
chicanes contam como uma só curva.

**Descreve o que mediu.** *«Têm melhor saída»* é o que a aplicação sabe. Se
foi a trajetória, os pneus ou o vácuo, não tem forma de saber, e *«trava mais
tarde»* seria um palpite vestido de coaching.

**Se faltarem voltas, diz de quem.** Tuas ou deles, porque «sem voltas para
comparar» sozinho deixa-te a adivinhar quais.

### O que não usa como referência

- Uma volta com qualquer parte na via das boxes. Uma volta rápida que na
  verdade foi um atalho pelas boxes tornar-se-ia de outro modo o alvo com que
  todos são medidos, e nada nela pareceria errado.
- Uma volta a que te juntaste a meio.
- Uma volta para a qual o simulador não deu tempo, como uma volta de saída ou
  um carro que acabou de chegar.
- Qualquer coisa de outro circuito. Mudar de traçado limpa tudo.

Também se cala enquanto estás a assistir. Comentar uma volta que estás a ver
em vez de conduzir não faria sentido.

---

## Quando o teu simulador não consegue responder

Os simuladores publicam coisas diferentes, e o engenheiro di-lo em vez de
adivinhar. O Assetto Corsa original publica **o teu próprio carro e nada
sobre mais ninguém**: nem nome, nem posição, nem tempo de volta de outro
piloto. Nada que te compare com a grelha tem dados por via nenhuma ali.

Pergunta «quem vai na frente» e ele responde **«este jogo não diz»**. É uma
resposta diferente de «ninguém para observar», que significa que a grelha
está mesmo vazia. Dizer a um piloto em sétimo que não há ninguém à frente
dele é dizer-lhe algo falso.

Comportamentos que precisam de dados que o teu simulador não fornece são
ignorados com uma linha no registo em vez de ficarem ligados e mudos:

```
Spotter is on but this sim does not publish positions or spotter; it will stay quiet
```

`--telemetry` imprime o que o teu simulador está de facto a enviar. Vê a
última secção.

---

## Outros idiomas

O engenheiro fala o idioma que definiste para a **transcrição**, a não ser
que o fixes no separador Engenheiro. Os teus comandos chegam através do
Whisper, por isso um engenheiro à escuta de expressões inglesas enquanto o
Whisper produz espanhol nunca ouvirá uma única.

Tudo o que diz passa pelos mesmos catálogos de tradução da janela, e o mesmo
vale para as expressões que escuta. Acrescentar um idioma é um ficheiro JSON
em `src/pitradio/locale/`; vê o README principal.

**Os números são escritos por extenso em inglês e lidos como algarismos em
todo o resto.** A gramática dos números é específica de cada língua: o
alemão inverte dezenas e unidades, o espanhol funde os vintes, e uma
implementação feita a meio produziria disparates ditos com confiança na
língua de alguém. Os algarismos entregam o problema ao motor de voz dessa
língua, que já o resolve. Uma consequência: um pacote de voz não inglês não
consegue cobrir números, e estes saem sintetizados.

---

## Pacotes de voz

**De que pacote fala este engenheiro define-se aqui, no separador
Engenheiro**, e o treinador escolhe o seu no separador Coaching — são dois
trabalhos distintos, e um piloto pode razoavelmente querer ouvir qual dos
dois está a falar.

**Instalar, gravar e remover pacotes é em Definições → Voz.** Um pacote é
algo que a aplicação guarda. Qual deles cada voz usa é uma definição dessa
voz.

Vêm dois pacotes com a aplicação, **Norman** e **Claudia**, ambos gerados com
o Piper. Vê [voicepacks.md](voicepacks.md). Qualquer um pode ser substituído
por um pacote teu.

Um pacote de voz põe áudio gravado no lugar da voz do Windows: uma pasta de
ficheiros WAV, uma pasta por expressão, várias tomadas cada uma. O engenheiro
escolhe uma tomada ao acaso, o que é a maior parte da razão por que um pacote
soa a uma pessoa.

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

Um `<pacote>/<expressão>/*.wav` plano também funciona, e é o que se obtém ao
gravar o teu.

Por isso um pacote gerado pelo
[crew-chief-autovoicepack](https://github.com/cktlco/crew-chief-autovoicepack)
pode ser colocado tal como está. Para gerar um para as expressões do
SimPitRadio em vez das do Crew Chief:

1. Definições → **Voz** → **Escrever lista de expressões**. Isto escreve
   `phrase_inventory.csv` na pasta de vozes, no idioma do engenheiro.
2. Dá essa lista ao gerador em vez da dele.
3. Põe a pasta de saída sob `voices\` e escolhe-a no separador Engenheiro (ou
   usa **Definições → Voz → Abrir pasta de pacotes de voz** para lá
   chegares).

**Nomes e números nunca estão num pacote** e são sempre ditos pela voz do
Windows. Nenhum pacote consegue conter o nome de todos os pilotos nem todos
os tempos de volta, por isso um anúncio como *curva quatro, o Tandy foi mais
rápido à saída* é em parte gravado e em parte sintetizado. Essa costura
ouve-se. Continua a ser o compromisso certo, porque a alternativa é um pacote
que deixa de ser usado assim que um piloto é nomeado, o que é a maioria dos
anúncios.

Os pacotes são guardados ao lado da tua configuração, não na pasta de
instalação, para que uma atualização não apague um gigabyte de áudio que
escolheste instalar.

---

## Como tudo encaixa

O engenheiro corre na **sua própria thread**, separada das quatro que o
SimPitRadio já tem, e falar ganha uma thread abaixo dessa. Nenhuma pode
segurar o hook de teclado, o worker ou a janela.

Tudo o que faz tem o direito de falhar. O engenheiro ficar calado nunca te
pode custar um acionamento, uma transcrição ou uma mensagem na caixa de chat.
Se alguma coisa aqui se partir, as palavras vão para a caixa de chat como
sempre foram, e o problema fica uma linha no registo.

Lê o simulador dez vezes por segundo através do mesmo plugin que fornece os
nomes dos pilotos para as menções. Não há um segundo caminho de dados nem uma
ligação extra ao jogo.

---

## Nada é dito

**O Testar não faz nada.** O sintetizador corre num host de PowerShell usando
`System.Speech`, que faz parte da .NET Framework em todas as máquinas Windows
10 e 11. Procura `no speech host` no registo. Uma máquina bloqueada com o
PowerShell impedido é a causa habitual.

**Consegues ouvi-lo, mas não nos teus auscultadores.** Define o dispositivo
de saída no separador Áudio. Por predefinição usa o dispositivo do sistema,
que durante uma corrida é muitas vezes a coluna do volante.

**Lê tempos de volta e nunca faz coaching.** O treinador precisa de uma volta
de referência, e até o teu foco ter completado uma limpa, sem nenhuma parte
na via das boxes, não há nada com que comparar.

**Faz coaching e não diz nada nalgumas curvas.** Essas curvas custam menos
tempo do que o limiar, o que é o desenho pretendido. `engineer.coach_threshold`
em `config.json` é quanto tempo em meia curva vale a pena interromper por
ele, em segundos; baixa-o para mais chamadas. Não há controlo para isto na
janela.

**Não responde a nada do que dizes.** Confirma o nome no separador
Engenheiro, e lembra-te de que qualquer expressão que leve um piloto precisa
do nome à frente. Diz «Chief» sozinho. Se ouvires «pode falar», está a
ouvir-te e o problema é a expressão.

**Comeu uma mensagem.** Não devia. Se o engenheiro apanhou algo que querias
enviar, a linha do registo diz `that was for the engineer` juntamente com
aquilo com que correspondeu. Por favor abre um problema com essa linha: o
matcher a ser demasiado zeloso é o único bug desta funcionalidade que custa
algo real.

---

## Verificar o que o teu simulador está mesmo a enviar

Na maior parte das vezes em que o engenheiro não diz nada, o problema não é o
engenheiro. Inicia o jogo, põe-te **em pista e em movimento**, depois:

```bash
python -m pitradio --telemetry
```

Imprime cada carro tal como o engenheiro o vê: distância na volta, velocidade,
contagem de voltas, setor, tempos de volta, bandeira de boxes, posição no
mundo. Depois compara leituras consecutivas e diz-te se alguma coisa está a
mudar.

Essa segunda parte é a que importa ler. Um simulador em pausa ou parado num
menu continua a publicar um bloco que parece completamente saudável, com
carros, posições e velocidades plausíveis. Nada se mexe, por isso o
engenheiro não tem nada a dizer, e nenhuma imagem isolada mostra isso. Se
reportar

> Nothing changed across 4 reads, including the sim's own clock.

então o jogo está em pausa, num menu, ou a sessão terminou. Nada está
avariado.

O que observar quando *está* ao vivo:

| Coluna | Alimenta |
| --- | --- |
| `lapdist`, `speed` | a deteção de curvas, e onde se perde o tempo |
| `lap`, `last lap`, `best lap` | os anúncios de tempo de volta e volta mais rápida |
| `sec` — muda três vezes por volta | todos os anúncios de setor |
| `world x/y/z` — diferente por carro | o spotter |

A linha `provides:` no topo diz quais destas coisas o plugin de sessão afirma
fornecer. Um comportamento que precise de algo em falta é ignorado em vez de
ficar ligado e mudo, e o registo diz o que falta.

## O que cada simulador consegue fazer

Os simuladores publicam coisas muito diferentes, e um comportamento cujos
dados faltam é **ignorado com uma linha no registo** em vez de ficar ligado e
mudo.

| | Le Mans Ultimate | iRacing | Assetto Corsa / Competizione / Evo | Automobilista 2, Project CARS 2 / 3 |
| --- | --- | --- | --- | --- |
| Tempos de volta | sim | sim | sim | derivados |
| Nova volta mais rápida | sim | sim | — | sim |
| Anúncios de setor | sim | — | sim | — |
| Onde sou mais lento | qualquer piloto | qualquer piloto | a tua própria melhor | qualquer piloto |
| Quem está à frente / na liderança | sim | sim | — | sim |
| Spotter | geometria | o anúncio do próprio simulador | só o Competizione | geometria |
| Menções a pilotos, «P3» | sim | sim | — | sim |
| Danos | sim | — | — | — |
| Coaching e o diagrama de segmento | sim | — | — | — |

Cada lacuna nessa tabela é do jogo:

- **O iRacing** não publica tempos de setor por carro, por isso os anúncios
  de setor não têm com que trabalhar. O seu spotter é o melhor de todos: o
  `CarLeftRight` vem das carroçarias reais, por isso não precisa de definição
  de troca nem de estimativa de largura.
- **O Assetto Corsa** publica tempos de volta só para o teu carro e nenhum
  nome de piloto. Não há classificações nem menções ali, e «onde sou mais
  lento» persegue a tua própria melhor volta, que é para isso que serve uma
  sessão de treinos de qualquer forma.

  O jogo original vai mais longe e publica **nenhum outro carro**, nem
  sequer a posição. Verificado contra uma corrida real de oito carros, o
  vetor de coordenadas tinha o jogador na casa zero e memória intocada em
  todas as outras: zeros, um NaN, um desnormalizado. O spotter também não tem
  ali nada com que trabalhar. O plugin de sessão decide isto por sessão e não
  por jogo, porque o **Competizione publica** esse vetor, e o mesmo plugin
  reporta posições nele.
- **O Automobilista 2 e o Project CARS** trazem *contagens* de voltas em vez
  de tempos na parte do bloco em que vale a pena confiar, por isso os tempos
  são aqui medidos a cronómetro. Uma volta que atravesse uma pausa sai mais
  longa do que foi, o que falha para o lado seguro: uma volta inflacionada
  nunca se torna a referência que uma comparação persegue. O campo de setor
  deles é um enum que não foi possível determinar a partir de fora dos jogos,
  por isso os anúncios de setor não são oferecidos.

O Automobilista 2 tem entrada própria em vez de partilhar a do Project CARS,
para que possas escolher o jogo que estás mesmo a correr e para que os dois
mantenham definições de spotter e de proximidade separadas.

**O Le Mans Ultimate é o único verificado contra o jogo em execução.** Todos
os outros leitores não estão verificados: testados contra memória partilhada
construída à mão, o que apanha uma largura de campo errada, um nome mal
descodificado ou um erro de preenchimento, e não consegue apanhar um
pressuposto errado sobre o que o simulador põe onde. Corre `--telemetry` com
o jogo em pista antes de confiares em qualquer um deles, e sobretudo no
Assetto Corsa Evo, que ainda está em acesso antecipado e pode mudar a sua
disposição.

**O iRacing está marcado como experimental**, e aparece assim no seletor de
perfis. O código não é pior do que o resto. Ninguém a trabalhar no
SimPitRadio tem uma cópia, por isso é o único plugin de sessão que não vai
ser verificado contra o jogo real a não ser que alguém que o tenha corra
`--telemetry` e diga o que veio. Se fores tu, por favor fá-lo; a nota na
lista de plugins pede exatamente isso.

## Definições por simulador

Três dos números do engenheiro vivem no **perfil**, sob as definições do
plugin de sessão do jogo, porque descrevem o jogo e não o teu gosto:

- **Trocar os lados do spotter**, para quando um carro à tua direita é
  chamado à tua esquerda
- **Sobreposição do spotter (metros)**: que distância ao longo da pista ainda
  conta como lado a lado. Um Hypercar tem cerca de 5 m
- **Largura do spotter (metros)**: até onde para o lado conta, antes de
  estarem simplesmente noutra parte do circuito

Os comprimentos dos carros e as convenções de eixos diferem entre
simuladores, por isso um número que serve num jogo está errado no seguinte.

## Bandeiras e incidentes

Um comportamento próprio, separado do spotter deliberadamente. As próprias
pastas de sons do Crew Chief traçam a linha no sítio certo: `car_left`,
`still_there` e `clear_all_round` ficam em `spotter/`, enquanto
`stopped_car_in_turn_3`, `slow_car_ahead` e `local_yellow_ahead` ficam em
`flags/`. O spotter responde a quem está ao teu lado, que é geometria. As
bandeiras respondem ao que aconteceu à pista, que é outra coisa.

Derivar a segunda da primeira produzia um aviso em todas as zonas de
travagem. O SimPitRadio tinha uma regra que dizia que um carro muito mais
lento do que tu era um perigo, e uma zona de travagem é precisamente onde o
carro da frente é muito mais lento do que tu. Essa regra desapareceu.

**Três fontes, não igualmente fiáveis.**

A *bandeira amarela em todo o circuito* e a *azul* vêm do simulador e são
fiáveis. O `mGamePhase`, o `mYellowFlagState` e o `mFlag` por carro do LMU
leem-se todos com sentido contra uma sessão ao vivo.

Os *amarelos locais são derivados*, porque o `mSectorFlag` do LMU não é
utilizável. Está documentado como «se há amarelos locais neste momento em
cada setor» e lê `[11, 11, 1]` sob bandeira verde, com os campos de ambos os
lados corretos. Não escorregou nenhum desvio; o LMU publica simplesmente
outra coisa ali. Lido como booleanos, poria uma amarela permanente em todo o
circuito. Por isso um incidente aqui significa o que um comissário entende
por isso: um carro parou na estrada e está ali há dois segundos. É uma
derivação a partir de dados que o simulador publica honestamente, no mesmo
espírito de encontrar as curvas no traço de velocidade em vez de distribuir
um mapa do traçado.

O custo é que o anúncio não pode preceder o incidente. Uma amarela a sério
sai no momento em que os comissários a veem, e este espera para ter a
certeza. O benefício é que nunca se engana quanto a uma pista verde, que é a
falha que leva as pessoas a desligar uma funcionalidade.

**Os incidentes são nomeados por curva, não por piloto.** À velocidade a que
isto importa, «curva seis» é algo sobre o qual um piloto pode agir, e um nome
é uma contagem de sílabas que não pode dar-se ao luxo. A numeração é a do
caderno de voltas, para que um piloto ouça um só conjunto de números de curva
em toda a aplicação. As curvas são encontradas uma vez por volta de
referência e guardadas em cache, porque `find_corners` reamostra uma volta
inteira e isto corre várias vezes por segundo. Sem volta de referência ainda,
é o setor que é nomeado.

**Quando o incidente és tu, os anúncios laterais param.** Descrever ao
piloto de um carro atravessado os carros que passam é ruído. A única
pergunta útil é se há espaço para arrancar, e `rejoin.py` responde-lhe
comparando *o tempo até estar em segurança* com *o tempo até chegar o
próximo carro*. Um carro parado precisa de recuperar toda a sua aceleração
antes da primeira chegada, e é por isso que uma resposta assente em três
segundos de pista livre apanha as pessoas.

Duas salvaguardas, ambas aprendidas em vez de presumidas. Nada é dito na via
das boxes, onde estar parado é o objetivo. E nada é dito antes de o carro
alguma vez se ter mexido: estar na grelha antes dos semáforos é estar parado,
na trajetória de corrida, com todo o pelotão atrás, que é exatamente cada
entrada que o conselho de regresso à pista analisa.

Vê [voicepacks.md](voicepacks.md) para gerares uma voz.

## Perguntas

Comportamentos e perguntas são coisas diferentes, e a diferença aparece no
separador. Um comportamento é algo que o engenheiro *continua a fazer*,
listado em [O que ele te diz](#o-que-ele-te-diz), e traz um intervalo de
repetição, porque um carro ao lado deixa de estar ali sem que nada aconteça.
Uma pergunta tem uma resposta, e depois de dada não há nada a correr. Modelar
uma como a outra punha «quem tem a volta mais rápida» na lista de
Comportamentos, onde cada entrada se repete. Não existe isso de responder de
novo a uma pergunta a cada 1,2 segundos.

Três delas: a volta mais rápida, o setor mais rápido, e a tua própria melhor.

**O parâmetro segue a palavra-chave e nunca faz parte da expressão.** Aquilo
sobre que um piloto pode perguntar depende do simulador em que está: as
classes desta grelha, os setores que este circuito tem. Nada disso pertence a
uma expressão que alguém escreveu numa caixa de definições. «Quem tem o
melhor sector» é a expressão; *três na GT3* é o que veio a seguir, analisado
contra a sessão. Uma classe é reconhecida através de `mentions.class_aliases`,
por isso a *LMGT3* do LMU responde a *GT3* exatamente como em todo o lado, e
*LMP2* continua a recusar responder a *P2* porque isso é uma posição.

**Um espaço de argumentos fechado é a defesa contra falsos positivos**, e é
melhor do que contar palavras. `phrases.MIN_BARE_WORDS` protege os comandos
falados exigindo duas palavras à frente de um parâmetro aberto; aqui não
chega, porque *who has the fastest lap of my life that one* passaria isso
facilmente e seria tomado como uma pergunta sobre uma classe chamada *of my
life that one*, engolindo a mensagem. O argumento de uma pergunta só pode ser
uma classe desta grelha, um setor entre um e três, ou nada. Tudo o resto
nunca foi uma pergunta, seja lá com o que tenha começado. Interpelado pelo
nome é uma de qualquer forma, porque quem disse o nome do engenheiro estava a
falar com ele.

**Nenhuma classe nomeada significa a tua própria classe**, que é o que
alguém num GT3 quer dizer ao perguntar «quem tem a volta mais rápida». Uma
classe nomeada em que ninguém está recebe essa informação em vez de ser
silenciosamente respondida com o valor global. Uma resposta errada dita com
confiança é a falha sem sintoma.

Cada uma tem uma caixa no separador Engenheiro e mais nada. Aquilo sobre que
uma pergunta pode incidir é fixado pelo que o simulador publica, por isso uma
caixa de expressões editável ali daria a entender que podias inventar uma.

O interruptor merece o seu lugar por outra razão: **cada expressão que o
engenheiro escuta é uma expressão que pode ser retirada de uma mensagem
destinada a toda a sessão**, e quem nunca faz estas perguntas não tem motivo
para correr esse risco. Desligar uma remove as suas expressões do matcher por
completo, em vez de a silenciar mais à frente — de outro modo «quem tem a
volta mais rápida» continuaria a ser retirada da mensagem e depois respondida
com nada, o que é o pior dos dois. Ausente da configuração significa ligada,
por isso acrescentar uma pergunta nunca exige uma migração.

## O spotter, e de onde vêm os seus números

Cada limiar em `spotter.py` é o do Crew Chief, lido de uma instalação local
em vez de adivinhado. O seu `ui_text/en.txt` nomeia cada definição e o
`CrewChiefV4.exe.config` traz os valores predefinidos:

| Nosso | Do Crew Chief | Predefinição |
| --- | --- | --- |
| `DEFAULT_CAR_LENGTH` | `lmu_spotter_car_length` | 4,5 (5 para pcars2/ACC, 4,4 para AMS2) |
| `GAP_FOR_CLEAR` | `spotter_gap_for_clear` | 0,5 m |
| `OVERLAP_DELAY` | `spotter_overlap_delay` | 50 ms |
| `CLEAR_DELAY` | `spotter_clear_delay` | 150 ms |
| `MIN_SPEED` | `min_speed_for_spotter` | 10 m/s |
| `MAX_CLOSING_SPEED` | `max_closing_speed_for_spotter` | 12 m/s |
| o intervalo de repetição | `spotter_hold_repeat_frequency` | 3 s |

Três destes faltavam aqui por completo, e cada um provocava uma falha que o
piloto conseguia sentir:

**O limite de velocidade de aproximação é o que apanha o carro que dobra.**
Algo que chega 12 m/s mais depressa atravessa toda a janela de sobreposição
em bem menos de um segundo, por isso, quando o anúncio é dito, já foi embora,
e o piloto mantém uma trajetória por um carro que já lá não está.

**A velocidade mínima é o que trava a via das boxes e a grelha.** Abaixo de
10 m/s os carros à tua volta estão parados ou passam a passo, e anunciá-los é
a forma como um spotter acaba desligado.

**Os dois atrasos de estabilização são o que trava a tagarelice.** Dois
carros na mesma curva entram e saem da sobreposição ao ritmo da respiração.
São deliberadamente de comprimentos diferentes: o atraso de sobreposição é
curto porque um aviso que chega tarde não vale nada, e o atraso de libertação
é mais longo porque se pode dar ao luxo de ter a certeza. Um piloto que
mantém a sua trajetória um décimo mais do que o necessário não perdeu nada.

O alcance de libertação é `comprimento do carro + folga`, não um segundo
múltiplo do comprimento. A distinção importa nos extremos: para um kart,
«mais um comprimento de carro» são dois metros de histerese e o anúncio
arrasta-se durante demasiado tempo, enquanto meio metro de folga é meio metro
seja lá o que for que conduzas.

**O spotter fica calado sob bandeira amarela em todo o circuito**, o
`fcy_stop_spotter_immediately` do Crew Chief, ligado por predefinição. O
pelotão está agrupado ao passo e permanentemente sobreposto, por isso todos
os anúncios seriam verdadeiros e inúteis.

### O que diz

O vocabulário é a pasta `Sounds/voice/spotter/` do Crew Chief, por isso um
pacote de voz construído para o Crew Chief di-lo todo sem mapeamento:
`car_left`, `car_right`, `still_there`, `hold_your_line`, `in_the_middle`,
`clear_left`, `clear_right`, `clear_all_round`, `three_wide_on_left`,
`three_wide_on_right`.

Dois deles substituíram anúncios que diziam o mesmo facto pelo caminho mais
difícil:

* **«três lado a lado, estás à direita»** era *dois carros à esquerda*. Um
  piloto que ouve o antigo tem de calcular onde isso o deixa, enquanto está
  ocupado. O novo diz diretamente para que lado não há espaço.
* **«no meio»** era *três lado a lado*, para um carro de cada lado.

Uma repetição diz «ainda está lá» de um lado e «mantém a tua trajetória» de
ambos, porque são instruções diferentes: uma significa não vás por ali, a
outra significa não te mexas. A chegada e as suas repetições partilham uma
chave derivada das *contagens*, para que o intervalo de repetição as governe.
Uma chave que mudasse com a formulação faria do seguimento um anúncio novo,
devido logo no tick seguinte.

**O conjunto de ovais está deliberadamente ausente**: `car_inside`,
`clear_outside`, `three_wide_on_inside`. Que lado é o interior é um facto
sobre a inclinação, que nenhum dos simuladores aqui publica e que o Crew
Chief guarda por pista. Adivinhá-lo é um anúncio confiantemente ao contrário.

### Combustível

«quanto combustível preciso para acabar a corrida se entrar nas boxes» leva a
paragem como argumento: *na próxima volta*, ou *daqui a cinco voltas*. **A
resposta é uma percentagem**, porque é esse o número no próprio ecrã de
combustível do simulador e o piloto tem cerca de quatro segundos a caminho da
entrada das boxes para o marcar. Os litros são a conta interna.

**O consumo é medido.** O consumo de um carro depende do circuito, do mapa de
motor, do tráfego e de como a pessoa o conduz, por isso os litros por volta
aqui são o que *este* carro tem gasto *nestas* voltas. É uma média móvel
curta, para que acompanhe uma mudança de mapa de motor em vez de ser puxada
para trás por um stint inteiro. Até uma volta estar completa não há resposta,
e ele di-lo. Um número de combustível inventado do nada é a única resposta
errada aqui que acaba com a corrida de alguém.

Três pormenores que vale a pena escrever:

* **As voltas antes da paragem não são abastecidas.** O que está no depósito
  agora cobre-as. Só as voltas depois dela são a pergunta, e é por isso que
  isto nunca lê o nível atual.
* **`mMaxLaps` é `INT_MAX` numa sessão por tempo.** Tomado à letra, pede
  combustível para dois mil milhões de voltas. `SessionInfo` traz `max_laps`
  *ou* `ends_at`, nunca ambos, e é o plugin de sessão que decide qual — o
  engenheiro nunca adivinha o que falta. Uma corrida por tempo divide o
  relógio restante pela melhor volta do próprio piloto e arredonda **para
  cima**, porque a bandeira cai no fim da volta em que estás quando o tempo
  acaba.
* **Um enchimento acima da capacidade do depósito é reportado, não
  cortado.** Significa que a paragem não pode ser a última, e um piloto a
  quem se diz que o depósito enche a cem por cento sem lhe dizerem isso
  planeia uma corrida que não funciona.

Tudo o resto arredonda no sentido de mais combustível: ficar sem é uma
desistência e levar um litro a mais é um décimo por volta.

O combustível chega a `Car` **só para o carro do piloto**, porque os
simuladores publicam telemetria de depósito para o carro que estás a
conduzir e de mais ninguém. É ligado através da correspondência de `mID`,
porque o vetor de telemetria do LMU é indexado por `playerVehicleIdx`
enquanto o vetor de classificação não é. Ligá-lo por posição poria o teu
depósito no carro que por acaso estivesse classificado nessa casa.

## Estar longe do volante

O engenheiro não diz nada, e **não regista nada**, quando o piloto não está a
conduzir. Três estados, e precisam de três sinais diferentes:

* **Em pausa.** O relógio do simulador para enquanto o desta máquina não, e a
  diferença é o sinal. O `mGamePhase` lia *bandeira verde* ao longo de toda
  uma sessão passada em pausa na garagem, com `mCurrentET` congelado em
  2218.0. A fase diz que tipo de sessão é. Não diz se a sessão está a
  decorrer.
* **Na garagem.** Aqui o relógio continua, por isso o relógio não pode ser o
  sinal. O `mInGarageStall` é. Cobre menos terreno do que `in_pits`, que é
  toda a via das boxes: um carro a cumprir uma paragem está a correr.
* **Entregue à IA.** `mControl` é 1, que é o aspeto de estar a assistir.

**Também nada é observado.** Um simulador em pausa republica o mesmo
fotograma para sempre, e dar isso ao caderno de voltas regista um carro que
não percorre distância nenhuma durante todo o tempo em que alguém deixar o
jogo ali parado. Isso é uma volta de referência corrompida, não uma volta em
falta. O estado do spotter é descartado à entrada pela mesma razão: um carro
que estava ao lado antes da pausa é um facto sobre um instante que já
passou.

**Pôr em pausa uma corrida online não é detetado, e não pode ser.** O
relógio ali continua, porque a corrida continua. O menu está aberto nesta
máquina e os carros continuam a andar. Nada na memória partilhada separa
isso de correr normalmente, e inventar um sinal para tal calaria o
engenheiro durante uma corrida a sério, que é o pior dos dois erros.
