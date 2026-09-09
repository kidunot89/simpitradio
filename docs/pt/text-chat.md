# Chat de texto

Aquilo para que o SimPitRadio foi construído. Mantém uma tecla, diz o que queres
dizer, larga — e aparece na caixa de chat do jogo, escrito, sem as tuas mãos
saírem do volante.

Todo o resto na aplicação cresceu a partir disto. O engenheiro, o treinador e o
chat de voz partilham a mesma tecla e a mesma gravação; o chat de texto é o que
acontece às palavras quando mais nada as reclamou.

## O que acontece enquanto manténs a tecla

1. **A tecla é engolida.** O jogo nunca vê o acionador, por isso pode ser uma
   tecla que o jogo também use.
2. **A gravação começa de imediato** — antes de a caixa de chat abrir, não
   depois. Abri-la leva algumas centenas de milissegundos e tudo o que fosse dito
   nesse intervalo perder-se-ia.
3. **As teclas de chat são acionadas** para abrir a caixa de chat do jogo, e a
   aplicação espera `pre_delay_ms` até que esta ganhe o foco.
4. **Largas.** A gravação para e o excerto vai para o Whisper, no teu próprio
   processador.
5. **O texto é escrito** e depois são acionadas as teclas de envio.

Se as palavras se revelarem um comando para o engenheiro ou o treinador, é a esse
que se responde e nada é escrito. Essa decisão é deliberadamente estreita — ver
[Falar com ele](engineer.md#falar-com-ele) — porque a mesma tecla envia mensagens
a toda a gente na tua sessão, e um comando que a aplicação invente é uma mensagem
que em silêncio nunca chega.

## Desligar

**Chat de texto → Enviar para o jogo** é o interruptor a que se recorre a meio de
uma corrida quando uma sessão se torna pública. Desligado, o acionador fica só
para a voz e o engenheiro: sem teclas de chat, sem escrita, sem nada enviado.

Há um segundo interruptor por jogo, em Perfis. «Este jogo tem caixa de chat?» é um
facto sobre o jogo e não uma decisão a tomar em cada sessão — o Assetto Corsa
offline não tem chat para abrir, por isso cada pressão mandava para o jogo um
Enter que ali significava outra coisa. Define-o uma vez e esquece. O interruptor
geral continua a mandar: desligado ali é desligado em todo o lado.

## Rever uma mensagem antes de sair

Por predefinição a mensagem é enviada assim que é escrita. O Whisper engana-se, e
numa sessão pública um erro é problema de toda a gente — por isso cada perfil tem
um interruptor **Enviar automaticamente**.

Com ele desligado, a mensagem é escrita na caixa de chat e fica lá. O teu
acionador decide então o que lhe acontece, sem largar o volante:

| Gesto | O que faz |
| --- | --- |
| **Toque** | Envia |
| **Dois toques** | Apaga |
| **Manter** | Apaga e grava outra |

O separador Estado mostra **à espera de envio** enquanto uma mensagem ali estiver.

Se tiveres botões a mais, **Definições → Acionador** também atribui teclas
diretamente a *Enviar mensagem em espera* e *Apagar mensagem em espera*. Agem de
imediato, sem janela de duplo toque para aguardar, e convivem com os gestos em vez
de os substituírem.

**Um toque não pode ser executado logo**, porque até a janela de duplo toque
fechar pode ser a primeira metade de um. Essa espera é `review.double_tap_ms`,
cerca de um terço de segundo. Põe-na a `0` na configuração para enviar de imediato
e abdicar de apagar com duplo toque. `review.tap_ms` é a fronteira entre um toque
e um manter.

**Uma pressão com uma mensagem pendente começa logo a gravar**, antes de se saber
se será toque ou manter. Esperar para descobrir comeria as primeiras palavras de
uma regravação; o buffer é deitado fora se afinal era um toque.

## Perfis

Qual perfil se aplica é decidido pelo executável que tem o foco, por isso vários
simuladores podem estar configurados ao mesmo tempo e é usado o certo sem
perguntar.

A definição que mais importa é **Atraso de abertura do chat** (`pre_delay_ms`). A
caixa de chat precisa de alguns fotogramas para abrir e ganhar o foco, e escrever
cedo de mais perde os primeiros caracteres. Começa em 350 ms e sobe se as
mensagens chegarem truncadas.

| Definição | Para que serve |
| --- | --- |
| **Atraso de abertura do chat** | Quanto esperar depois de abrir o chat antes de escrever. A que se sobe se as mensagens chegarem truncadas |
| **Teclas de abrir chat** | O que abre o chat. Enter na maioria dos simuladores |
| **Teclas de envio** | O que a envia. Normalmente Enter outra vez |
| **Teclas de cancelar** | O que fecha a caixa sem enviar, para apagar uma mensagem em espera |
| **Retenção de tecla** | Quanto tempo cada tecla é mantida. Os jogos leem a entrada uma vez por fotograma, por isso uma pressão mais curta do que um fotograma é uma pressão que o jogo nunca vê |
| **Atraso de escrita** | O intervalo entre caracteres |
| **Máximo de caracteres** | Mensagens mais longas são cortadas. A maioria dos simuladores tem um limite próprio |
| **Enviar automaticamente** | Desligado para rever antes de enviar — ver acima |
| **Plugin de sessão** | Lê quem está na sessão para que os nomes sejam transcritos corretamente e se tornem menções. Deixa em *automático* |

### Unicode ou códigos de varrimento

**Modo de escrita** decide como os caracteres chegam ao jogo. *Unicode* envia o
próprio caractere e lida com qualquer disposição de teclado e qualquer alfabeto.
Alguns jogos ignoram-no porque leem códigos de varrimento do hardware; para esses,
muda para *scancode*, que escreve como se as teclas tivessem sido premidas
fisicamente.

Os códigos de varrimento limitam-se ao que um teclado americano consegue
produzir, por isso caracteres acentuados e alfabetos não latinos não sobrevivem.
Experimenta primeiro unicode; a definição existe porque «o jogo ignora o que
escrevemos» tinha de ser uma alteração de configuração e não de código.

Os dois também têm temporizações diferentes, e é por isso que são modos
separados. As teclas em scancode são mantidas `key_hold_ms` porque os jogos leem a
entrada uma vez por fotograma. O texto escrito não: passa pela fila de mensagens,
e 40 ms por caractere faria uma mensagem de 200 caracteres demorar oito segundos.

## Nomes e vocabulário

O Whisper transcreve o que ouve, e os nomes dos pilotos são exatamente aquilo em
que é pior. O plugin de sessão lê quem está de facto na tua sessão e alimenta
esses nomes, para que «Estre» saia como «Estre» e não como «Ester».

**Vocabulário** acrescenta as tuas próprias palavras por cima: nomes de
patrocinadores, o nome de uma equipa, como se escrevem mesmo os nicks dos teus
amigos. Tudo o que te apanhas a corrigir vale a pena acrescentar.

## Não é escrito nada

**Vê primeiro o separador Estado.** Mostra com o que o hook está armado neste
momento e quando o acionador foi visto pela última vez. Se *Último acionamento*
nunca se atualizar, o problema é a tecla ou o hook, não a transcrição.

**Tem de correr como administrador.** O Windows descarta entrada injetada dirigida
a um processo com um nível de integridade mais alto do que o de quem a envia, e os
simuladores correm muitas vezes elevados. A versão instalada pede isso
automaticamente.

**Confirma que o perfil corresponde.** O separador Estado regista o nome do
executável em foco; se não for um dos teus perfis, está a ser usado o perfil
predefinido e as teclas de chat dele podem não servir para esse jogo.

**Confirma o atraso de abertura do chat.** Mensagens que chegam sem os primeiros
caracteres são, sempre, um `pre_delay_ms` demasiado baixo.

**Confirma que o jogo não ignora unicode.** Se a caixa de chat abrir e não
aparecer nada lá dentro, experimenta o modo de escrita *scancode*.
