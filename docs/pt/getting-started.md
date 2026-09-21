# Primeiros passos

Instala, diz-lhe que tecla deve escutar e diz alguma coisa. Tudo o resto nestas
páginas é opcional.

![A janela do SimPitRadio no separador Estado](images/window.png)

## Instalação

Descarrega o instalador da
[página de versões](https://github.com/kidunot89/simpitradio/releases/latest) e
executa-o. O Windows vai avisar: as compilações não estão assinadas, por isso o
SmartScreen mostra «O Windows protegeu o seu PC» e tens de escolher **Mais
informações → Executar mesmo assim**. É assim que um instalador não assinado se
apresenta, e assinar custa dinheiro que este projeto não gasta.

A instalação faz uma única pergunta — **que idioma** — com o do teu Windows já
escolhido. Isso fixa três coisas ao mesmo tempo: a janela, o modelo de voz e o
idioma em que o engenheiro fala e escuta. O separador Idioma muda-o mais
tarde.

**Instala-se como administrador, de propósito.** O Windows descarta as teclas
injetadas dirigidas a um programa que corre com mais privilégios do que quem as
envia, e os simuladores correm muitas vezes elevados. Sem isto, tudo parece
funcionar e nada chega alguma vez ao jogo.

### O primeiro arranque transfere duas coisas

No instalador não viaja nada de grande, por isso, na primeira vez que o abres,
pede-te para ir buscar:

- **o modelo de voz**, cerca de 250 MB, que é o que transforma a tua voz em texto
- **um pacote de voz** para o engenheiro, cerca de 45 MB, quando há um
  publicado no teu idioma

Ambas uma só vez. O modelo fica fora da pasta de instalação, para que uma
atualização nunca o volte a custar. Se disseres «agora não», os separadores
Idioma e Definições vão buscá-los quando quiseres.

A versão portátil não tem instalador nem pergunta de idioma, por isso pergunta
no primeiro arranque.

## Escolhe uma tecla

**Definições → Acionamento.** Carrega em *Prime uma tecla…* e depois na que
quiseres.

![A secção Acionamento do separador Definições](images/trigger.png)

A tecla é **engolida de passagem**, por isso o jogo nunca a vê. Associa uma que
o jogo já use e nada se parte. `F13` é a predefinição porque a maioria dos
teclados não a tem e mais nada está à escuta dela.

**Um botão do volante também serve.** Na linha **Botão do volante**, carrega em
*Prima um botão…* e depois no botão que quiseres. O SimPitRadio abre o volante
sem o tirar ao jogo, por isso o simulador continua a ler todos os botões,
incluindo esse. Mantém-no premido para falar, tal como farias com a tecla. Os
dois ficam armados ao mesmo tempo, para poderes associar cada um e usar o que
estiver mais perto.

A outra via é o software do teu próprio volante, ou o
[JoyToKey](https://joytokey.net/): põe `F13` num botão e associa `F13` aqui.
Recorre a isto se o volante já estiver a correr um software em que confias, ou
se o SimPitRadio não conseguir abrir o dispositivo.

## Configura o microfone

**Áudio → Microfone.** Escolhe a entrada, mantém o acionamento premido e
observa a barra de nível. Mostra o sinal *depois* do ganho, que é o que o
modelo de voz recebe. Aponta a um pico por volta de três quartos.

![O separador Áudio](images/audio.png)

**A saída não deve ser o dispositivo do teu simulador.** O engenheiro, o treinador
e o sinal de gravação tocam todos aqui; apontá-la para a mesma saída que o jogo
usa mete o apito dentro da gravação.

Carrega em **Gravar 4 s e transcrever** para ouvires o que foi percebido. Durante
um teste não se escreve nada em lado nenhum.

## Diz alguma coisa

Mantém o acionamento, diz o que queres, larga.

1. A tecla é engolida.
2. A gravação começa **de imediato**, antes de a caixa de chat abrir. Nada do
   que dizes nas primeiras centenas de milissegundos se perde.
3. As teclas de chat abrem a caixa de chat do jogo.
4. Ao largar, o excerto vai para o modelo de voz, no teu próprio processador.
5. O texto é escrito e as teclas de envio são acionadas.

O separador Estado mostra com o que o hook está armado e quando o acionamento
foi visto pela última vez. Se *Último acionamento* nunca se atualizar, o
problema é a tecla ou o hook, não a transcrição.

![O cartão Estado](images/status.png)

## E depois, se quiseres mais

O engenheiro, o treinador e o chat de voz estão todos desligados até os
ligares.

| | |
| --- | --- |
| [Chat de texto](text-chat.md) | O ditado propriamente dito: perfis, rever antes de enviar, o que fazer quando nada é escrito |
| [O engenheiro](engineer.md) | Uma voz com nome que lê os teus tempos por volta, avisa de carros ao lado e responde a perguntas |
| [O treinador](coaching.md) | A tua trajetória contra a de um rival depois de cada curva, com o que mudar |
| [Voz no rádio](voice-chat.md) | Ouvir os outros pilotos da tua sessão, e só os que estão perto |
| [Pacotes de voz](voicepacks.md) | Gravar ou instalar a voz com que o engenheiro fala |

## Quando algo está errado

**Vê primeiro o separador Estado.** É o único sítio que mostra aquilo em que a
aplicação acredita: a tecla armada, o executável em foco, o perfil em uso e um
registo ao vivo.

![O registo no separador Estado](images/log.png)

- **Não é escrito nada** — ver [Não é escrito nada](text-chat.md#não-é-escrito-nada).
- **Não é dito nada** — ver [Não é dito nada](engineer.md#nada-é-dito).
- **Não é desenhado nada** — ver [Não é desenhado nada](coaching.md#não-é-desenhado-nada).

O registo também é escrito para um ficheiro. **Estado → Abrir pasta de registos**
leva-te lá, e é a primeira coisa que vale a pena anexar a um relato.
