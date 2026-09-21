# Pacchetti vocali

L'ingegnere suona come una persona solo se ha registrazioni di una. Un
pacchetto vocale è questo: una cartella di file WAV, una cartella per frase,
che l'ingegnere riproduce al posto di parlare con la voce di Windows. Nella
cartella di una frase possono stare più riprese, e l'ingegnere ne sceglie una
a caso, così la stessa chiamata due volte in uno stint non suona come una
macchina che si ripete.

Qualsiasi cosa dica che non è nel pacchetto viene comunque pronunciata dalla
voce di Windows: il tuo nome, un tempo sul giro, un pilota di cui non ha mai
sentito parlare. Un pacchetto non deve essere completo per valere la pena di
averlo.

## Tre modi per procurartene uno

**Installane uno pubblicato.** *Impostazioni → Voce* elenca i pacchetti
pubblicati per il download e ne installa uno su richiesta, verificandone il
checksum prima di scompattare qualsiasi cosa. Questa è la strada per una
lingua diversa dalla tua.

**Registralo tu stesso**, nella finestra. È la strada senza limiti ed è
quella attorno a cui è costruita l'app: *Impostazioni → Voce → Crea un
modello vocale*.

**Genera una base con Piper**, offline, e ri-registra sopra le parti che ti
interessano. Prendi questa via se vuoi qualcosa di corretto e piacevole già
oggi, o se non hai voglia di leggere 171 frasi prima di guidare.

Non si escludono a vicenda. Un pacchetto Piper è un pacchetto come un altro,
quindi qualsiasi sua frase può essere sostituita più tardi con una tua
ripresa.

### Perché non il cloning vocale

È stato provato per primo e abbandonato, ed è utile sapere perché prima di
mettersi a cercarlo.

Una voce clonata è stata generata per questo progetto a partire da quasi tre
minuti di audio di riferimento pulito. Rimessa nel riconoscitore vocale
dell'app stessa, ogni ripresa di «five» tornava come «bye», «four» come «boy»
e «zero» come «yo».

L'inventario è il perché. **141 delle sue 171 frasi sono di una o due
parole**, e il testo breve è esattamente dove un modello di cloning dà il
peggio di sé: XTTS genera in modo autoregressivo, decidendo da solo quando
fermarsi, e con una frase di due parole non c'è quasi nulla a vincolare quella
decisione. Piper è un modello in stile VITS, un solo passaggio in avanti dai
fonemi alla forma d'onda, senza un ciclo di campionamento che possa
divagare. Non può dire una parola diversa, il che su questo inventario conta
più del timbro.

Crew Chief risolve lo stesso problema allo stesso modo: i suoi pacchetti sono
*registrati*, e i suoi 11.176 nomi di piloti e 1.052 clip numeriche sono stati
letti da una persona.

## Registrare il proprio

*Impostazioni → Voce → Crea un modello vocale* apre un registratore: una
frase da leggere, un conto alla rovescia, una ripresa e il riascolto per
controllarla.

È meno lavoro di quanto sembri. L'intero inventario è **circa quaranta minuti
a tre riprese ciascuna**, e riprende da dove hai interrotto, quindi si può
fare a più sedute. Un pacchetto che copre metà delle frasi funziona dal
momento in cui lo salvi.

Poche cose decidono se il risultato è utilizzabile:

- **Di lato rispetto alla bocca**, un paio di dita di distanza, non davanti.
  Un microfono ad asta piazzato direttamente nel flusso d'aria taglia su ogni
  *p* e *b*, e il taglio non si può correggere in seguito.
- **Una stanza silenziosa.** Una ventola o un PC sotto la scrivania finisce
  in ogni clip, e ogni clip ti viene riprodotta a metà gara attraverso una
  cuffia.
- **Distanza costante.** Non spostarti tra una ripresa e l'altra. Clip
  registrate a quattro distanze diverse suonano come quattro persone diverse.
- **Disattiva il boost del microfono di Windows.** È un compressore, e alza
  il rumore ambientale tra una parola e l'altra.

Leggile come le direbbe un ingegnere alla radio: piatte, senza fretta,
leggermente annoiate. L'ingegnere non sta recitando.

## Generare una base con Piper

Piper gira offline, dagli script di packaging piuttosto che dentro l'app. I
percorsi qui sotto sono relativi ad `apps/client` in un checkout dei
sorgenti:

```
pip install -r packaging/requirements-voices.txt
python -m piper.download_voices --download-dir models/piper en_GB-alan-medium
python packaging/make_piper_pack.py --name Piper
```

Per costruirne uno con un modello specifico:

```
python packaging/make_piper_pack.py --name Piper --model models/piper/en_GB-alan-medium.onnx
```

**Offline, e non nell'app, di proposito.** Piper è abbastanza veloce su CPU
da tentare di chiamarlo al momento di parlare. Questo metterebbe un modello
da 63 MB e un runtime ONNX dentro una build i cui ultimi quattro rilasci
rotti sono stati tutti dipendenze native non raccolte. Un pacchetto è una
cartella di WAV; generarlo qui non costa nulla all'app e non può rompere una
build.

Non è *la tua* voce, e nulla finge il contrario. È una base corretta e
gradevole, sopra la quale ogni frase può essere ri-registrata nella finestra.

**Il giapponese serve un pacchetto in più, e fallisce in modo confuso senza
di esso.** Il modello giapponese chiede a Piper `pyopenjtalk` per trasformare
il testo in fonemi, e senza di esso ogni frase non produce audio. Quello che
viene segnalato è `wave.Error: # channels not specified`, che è il file di
output vuoto e non la causa reale. `pyopenjtalk` a monte distribuisce solo il
sorgente e richiede CMake e un compilatore C++; `pyopenjtalk-plus` è un fork
che distribuisce wheel con lo stesso nome di importazione, ed è nel file dei
requisiti sopra.

## Come si presenta un pacchetto

Un pacchetto è una cartella con dentro una sottocartella `voice`, e dentro
quella una cartella per frase che contiene le sue riprese. È il layout che
scrive `crew-chief-autovoicepack`, quindi **un pacchetto Crew Chief entra
così com'è**. La cartella esterna è separata così un pacchetto può portare
una licenza e le sue registrazioni sorgente senza che vengano scambiate per
frasi.

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

La cartella in cui sta un WAV è la frase, quindi la profondità fra `voice` e
quella cartella è libera. Il registratore scrive `pitradio/`; Crew Chief
scrive una cartella per categoria. Si leggono allo stesso modo.

Solo WAV. È ciò che ogni generatore emette, ciò che la libreria standard
legge, e non serve alcun decoder in una build che già combatte con
dipendenze native.

I nomi delle cartelle vengono dalla frase, in minuscolo, con la punteggiatura
**eliminata** invece che sostituita, così «that's enough» e «thats enough»
sono la stessa clip. Trasformare un apostrofo in un separatore darebbe
`that_s_enough`, e un pacchetto registrato contro una delle due grafie
mancherebbe silenziosamente l'altra.

## Dove vivono i pacchetti

**Impostazioni → Voce** è dove sono elencati tutti: cosa è installato, cosa è
incluso e cosa può essere scaricato. I pacchetti vivono accanto alla tua
configurazione, in `voices/`, non sotto la cartella di installazione. Un
aggiornamento sostituisce la cartella di installazione per intero, e un
pacchetto è molta audio che hai scelto di mettere lì. **Impostazioni → Voce →
Apri la cartella dei pacchetti vocali** la apre.

Trascina dentro una cartella, riapri la scheda, e appare nel selettore.

## L'elenco delle frasi

**Impostazioni → Voce → Scrivi l'elenco delle frasi** esporta ogni frase che
l'ingegnere può dire, come CSV, nella lingua dell'ingegnere stesso. Un
pacchetto si registra nella lingua in cui verrà parlato.

È generato dall'app invece che tenuto a mano, quindi non può allontanarsi da
ciò che l'ingegnere dice davvero. Usalo se registri fuori dall'app, o se
scrivi un tuo generatore.

## Non riproduce nulla

**Controlla che sia selezionato un pacchetto.** *Ingegnere → Voce → Voce*
deve puntare al pacchetto e non a *(nessun pacchetto)*.

**Controlla il dispositivo di uscita.** *Audio → Uscita* dovrebbe essere la
tua cuffia, la stessa che usi per la chat vocale e non l'uscita del
simulatore.

**Una frase mancante non è un difetto.** Tutto ciò che non è nel pacchetto
ripiega sulla voce di Windows, quindi un pacchetto registrato a metà suona
come due persone invece di fallire. È voluto: è ciò che rende un pacchetto
utilizzabile prima ancora che sia finito.
