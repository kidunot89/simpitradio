# Pacotes de voz

O engenheiro só soa como uma pessoa se tiver gravações de uma. Um pacote de voz é
exatamente isso: uma pasta de ficheiros WAV, um por frase, que o engenheiro
reproduz em vez de falar pela voz do Windows. Várias gravações da mesma frase
podem estar na mesma pasta, e o engenheiro escolhe uma ao acaso, para que a
mesma chamada duas vezes num stint não soe a uma máquina a repetir-se.

Tudo o que diz e não está no pacote — o teu nome, um tempo por volta, um piloto de
quem nunca ouviu falar — continua a ser dito pela voz do Windows. Um pacote não
tem de estar completo para valer a pena.

## Três formas de arranjar um

**Instalar um publicado.** *Definições → Voz* lista os pacotes publicados para
transferência e instala um quando pedes, verificando a soma de controlo antes de
descompactar seja o que for. É este o caminho para um idioma que não o teu.

**Gravá-lo tu**, na janela. É o caminho sem teto e aquele à volta do qual a
aplicação foi construída: *Definições → Voz → Criar um modelo de voz*.

**Gerar uma base com o Piper**, sem ligação, e voltar a gravar as partes que te
interessam. Útil se quiseres já algo correto e agradável, ou se preferires não
ler 171 frases antes de conduzir.

Não são exclusivos. Um pacote do Piper é um pacote como outro qualquer, por isso
qualquer frase nele pode ser substituída mais tarde pela tua própria gravação.

### Porquê não clonagem de voz

Foi a primeira coisa que se tentou e foi abandonada, e vale a pena conhecer a
razão antes de a ires procurar.

Gerou-se para este projeto uma voz clonada a partir de quase três minutos de
áudio de referência limpo. Devolvida ao reconhecedor de voz da própria aplicação,
cada gravação de «five» voltava como «bye», «four» como «boy» e «zero» como «yo».

O inventário é a razão. **141 das suas 171 frases têm uma ou duas palavras**, e
texto curto é exatamente onde um modelo de clonagem é pior: o XTTS gera de forma
autorregressiva e decide por si quando parar, e numa frase de duas palavras quase
nada limita essa decisão. O Piper é um modelo ao estilo VITS — uma única passagem
de fonemas a forma de onda, sem ciclo de amostragem que se possa desviar. Não
consegue dizer outra palavra, e neste inventário isso importa mais do que o
timbre.

O Crew Chief resolve o mesmo problema do mesmo modo: os seus pacotes são
*gravados*, e os seus 11 176 nomes de pilotos e 1 052 excertos de números foram
lidos por uma pessoa.

## Gravar o teu

*Definições → Voz → Criar um modelo de voz* abre um gravador: uma frase para ler,
uma contagem decrescente, uma gravação e a reprodução para a verificares.

É menos trabalho do que parece. O inventário inteiro são **cerca de quarenta
minutos a três gravações cada**, e retoma de onde ficou — pode portanto fazer-se
por sessões, e um pacote que cubra metade das frases funciona a partir do momento
em que o guardas.

Poucas coisas decidem se o resultado é utilizável:

- **Ao lado da boca**, a dois dedos de distância, não à frente. Um microfone de
  haste diretamente no fluxo de ar satura em cada *p* e *b*, e a saturação não se
  desfaz depois.
- **Uma sala silenciosa.** Uma ventoinha ou um PC debaixo da secretária acaba em
  cada excerto, e cada excerto é-te reproduzido a meio da corrida através de uns
  auscultadores.
- **Distância constante.** Não te inclines entre gravações. Excertos gravados a
  quatro distâncias diferentes soam a quatro pessoas diferentes.
- **Desliga o reforço do microfone do Windows.** É um compressor, e levanta o
  ruído da sala entre as palavras.

Lê-as como um engenheiro as diria no rádio — planas, sem pressa, ligeiramente
aborrecidas. O engenheiro não está a representar.

## Gerar uma base com o Piper

O Piper corre sem ligação, a partir dos scripts de empacotamento e não dentro da
aplicação. Os caminhos abaixo são relativos a `apps/client` numa cópia do
código:

```
pip install -r packaging/requirements-voices.txt
python -m piper.download_voices --download-dir models/piper en_GB-alan-medium
python packaging/make_piper_pack.py --name Piper
```

Para construir com um modelo específico:

```
python packaging/make_piper_pack.py --name Piper --model models/piper/en_GB-alan-medium.onnx
```

**Sem ligação, e fora da aplicação, de propósito.** O Piper é suficientemente
rápido num CPU para dar vontade de o chamar na hora de falar. Isso meteria um
modelo de 63 MB e um runtime ONNX dentro de uma compilação cujas últimas quatro
versões avariadas foram todas dependências nativas que não foram recolhidas. Um
pacote é uma pasta de WAV; gerá-lo aqui não custa nada à aplicação e não pode
partir uma compilação.

Não é a *tua* voz, e nada finge o contrário. É uma base correta e agradável, sobre
a qual qualquer frase pode ser regravada na janela.

**O japonês precisa de mais um pacote e falha de forma confusa sem ele.** O
modelo japonês pede a Piper o `pyopenjtalk` para transformar texto em fonemas,
e sem ele nenhuma frase produz áudio — reportado como
`wave.Error: # channels not specified`, que é o ficheiro de saída vazio e não a
causa real. O `pyopenjtalk` original publica apenas o código-fonte e exige
CMake e um compilador C++; `pyopenjtalk-plus` é um fork que publica wheels com
o mesmo nome de importação, e está no ficheiro de requisitos acima.

## Como é um pacote

Um pacote é uma pasta com uma subpasta `voice` lá dentro, e dentro dela uma
pasta por frase a guardar as suas gravações. É essa a disposição que o
`crew-chief-autovoicepack` escreve, por isso **um pacote do Crew Chief entra
diretamente**. A pasta exterior é separada para que um pacote possa levar uma
licença e as suas gravações de origem sem que estas sejam confundidas com
frases.

```
voices/
  Norman/
    voice/
      pitradio/
        go_ahead/
          1.wav
          2.wav
        box_this_lap/
          1.wav
        ...
```

A pasta onde um WAV está é a frase, por isso a profundidade entre `voice` e
essa pasta é livre. O gravador escreve `pitradio/`; o Crew Chief escreve uma
pasta por categoria. Qualquer uma delas é lida da mesma forma.

Só WAV. É o que qualquer gerador produz, o que a biblioteca padrão lê, e não
precisa de descodificador numa compilação que já luta com dependências nativas.

Os nomes das pastas vêm da frase, em minúsculas, com a pontuação **retirada** em
vez de substituída — assim «that's enough» e «thats enough» são o mesmo excerto.
Transformar um apóstrofo num separador daria `that_s_enough`, e um pacote gravado
contra uma das grafias falharia a outra em silêncio.

## Onde vivem os pacotes

**Definições → Voz** é onde estão todos listados: o que está instalado, o que vem
incluído e o que se pode transferir. Os pacotes vivem ao lado da tua
configuração, em `voices/`, não sob o diretório de instalação — uma atualização
substitui esse diretório por inteiro, e um pacote é muito áudio que escolheste pôr
lá. **Definições → Voz → Abrir pasta de pacotes de voz** abre-a.

Larga lá uma pasta, reabre o separador, e aparece no seletor.

## A lista de frases

**Definições → Voz → Escrever lista de frases** exporta todas as frases que o
engenheiro consegue dizer, em CSV, no idioma do próprio engenheiro — porque um
pacote é gravado no idioma em que vai ser falado.

É gerada a partir da aplicação em vez de mantida à mão, por isso não pode
afastar-se do que o engenheiro realmente diz. Usa-a se gravares fora da aplicação
ou se escreveres um gerador teu.

## Não se ouve nada

**Confirma que há um pacote selecionado.** *Engenheiro → Voz → Voz* tem de apontar
para o pacote e não para *(sem pacote)*.

**Confirma o dispositivo de saída.** *Áudio → Saída* deve ser os teus
auscultadores — os mesmos que usas para o chat de voz, não a saída do simulador.

**Uma frase em falta não é uma avaria.** Tudo o que não estiver no pacote recai
sobre a voz do Windows, por isso um pacote gravado a meio soa a duas pessoas em
vez de falhar. É intencional: é o que torna um pacote utilizável antes de estar
terminado.
