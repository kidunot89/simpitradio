# Pacchetti voce

L'ingegnere suona come una persona solo se ha le registrazioni di una. Un
pacchetto voce è esattamente questo: una cartella di file WAV, uno per frase, che
l'ingegnere riproduce invece di parlare attraverso il sintetizzatore di Windows.

Tutto ciò che dice e che non è nel pacchetto — il tuo nome, un tempo sul giro, un
pilota di cui non ha mai sentito parlare — viene comunque pronunciato dalla voce
di Windows. Un pacchetto non deve essere completo per valere la pena.

## Tre modi per averne uno

**Installarne uno pubblicato.** *Impostazioni → Voce* elenca i pacchetti
pubblicati per il download e ne installa uno su richiesta, verificando il
checksum prima di scompattare qualsiasi cosa. È la strada per una lingua diversa
dalla tua.

**Registrarlo tu**, nella finestra. È la strada senza tetto e quella attorno a
cui l'app è costruita: *Impostazioni → Voce → Crea un modello vocale*.

**Generare una base con Piper**, offline, e ri-registrare le parti che ti stanno
a cuore. Utile se vuoi subito qualcosa di corretto e piacevole, o se preferisci
non leggere 171 frasi prima di guidare.

Non si escludono. Un pacchetto Piper è un pacchetto qualsiasi, quindi ogni frase
al suo interno può essere sostituita più tardi da una tua ripresa.

### Perché non la clonazione vocale

È stata provata per prima e abbandonata, e vale la pena conoscerne il motivo
prima di andarla a cercare.

Per questo progetto è stata generata una voce clonata da quasi tre minuti di
audio di riferimento pulito. Rimandata nel riconoscitore vocale dell'app stessa,
ogni ripresa di «five» tornava come «bye», «four» come «boy» e «zero» come «yo».

Il motivo è l'inventario. **141 delle sue 171 frasi sono di una o due parole**, e
il testo breve è esattamente il punto in cui un modello di clonazione va peggio:
XTTS genera in modo autoregressivo e decide da sé quando fermarsi, e con una
frase di due parole quasi nulla vincola quella decisione. Piper è un modello in
stile VITS: un solo passaggio dai fonemi alla forma d'onda, senza ciclo di
campionamento che possa divagare. Non può dire una parola diversa, e su questo
inventario conta più del timbro.

Crew Chief risolve lo stesso problema allo stesso modo: i suoi pacchetti sono
*registrati*, e i suoi 11.176 nomi di piloti e 1.052 clip di numeri sono stati
letti da una persona.

## Registrare il proprio

*Impostazioni → Voce → Crea un modello vocale* apre un registratore: una frase da
leggere, un conto alla rovescia, una ripresa e la riproduzione per controllarla.

È meno lavoro di quanto sembri. L'intero inventario sono **circa quaranta minuti
a tre riprese ciascuna**, e riprende da dove si era rimasti — si può quindi fare
in più sedute, e un pacchetto che copre metà delle frasi funziona dal momento in
cui lo salvi.

Poche cose decidono se il risultato è utilizzabile:

- **Di lato rispetto alla bocca**, a un paio di dita di distanza, non davanti. Un
  microfono ad archetto direttamente nel flusso d'aria satura su ogni *p* e *b*, e
  la saturazione non si annulla dopo.
- **Una stanza silenziosa.** Una ventola o un PC sotto la scrivania finisce in
  ogni clip, e ogni clip ti viene riprodotta in piena gara in cuffia.
- **Distanza costante.** Non spostarti fra una ripresa e l'altra. Clip registrate
  a quattro distanze diverse sembrano quattro persone diverse.
- **Disattiva il boost del microfono di Windows.** È un compressore, e alza il
  rumore della stanza fra una parola e l'altra.

Leggile come le direbbe un ingegnere alla radio: piatte, senza fretta, un po'
annoiate. L'ingegnere non sta recitando.

## Generare una base con Piper

Piper gira offline, dagli script di packaging e non dentro l'app:

```
pip install -r packaging/requirements-voices.txt
python -m piper.download_voices --download-dir models/piper en_GB-alan-medium
python packaging/make_piper_pack.py --name Piper
```

Per costruire con un modello preciso:

```
python packaging/make_piper_pack.py --name Piper --model models/piper/en_GB-alan-medium.onnx
```

**Offline e non nell'app, di proposito.** Piper è abbastanza veloce su una CPU da
far venire la tentazione di chiamarlo al momento di parlare. Questo metterebbe un
modello da 63 MB e un runtime ONNX dentro una build le cui ultime quattro
versioni rotte erano tutte dipendenze native non raccolte. Un pacchetto è una
cartella di WAV; generarlo qui non costa nulla all'app e non può rompere una
build.

Non è la *tua* voce, e nulla finge il contrario. È una base corretta e piacevole,
sopra la quale qualsiasi frase può essere ri-registrata nella finestra.

**Il giapponese richiede un pacchetto in più e senza fallisce in modo
confuso.** Il modello giapponese chiede a Piper `pyopenjtalk` per trasformare
il testo in fonemi, e senza di esso ogni frase non produce alcun audio —
segnalato come `wave.Error: # channels not specified`, che è il file di output
vuoto e non la causa reale. Il `pyopenjtalk` originale pubblica solo i sorgenti
e vuole CMake e un compilatore C++; `pyopenjtalk-plus` è un fork che pubblica
wheel con lo stesso nome di import, ed è nel file dei requisiti qui sopra.

## Com'è fatto un pacchetto

Un pacchetto è una cartella con dentro una sottocartella `voice` che contiene i
WAV — la disposizione che scrive `crew-chief-autovoicepack`, quindi **un
pacchetto di Crew Chief entra direttamente**. La cartella esterna è separata così
che un pacchetto possa portare una licenza e le sue registrazioni sorgente senza
che vengano scambiate per frasi.

```
voices/
  Norman/
    voice/
      go_ahead.wav
      box_this_lap.wav
      ...
```

Solo WAV. È ciò che emette ogni generatore, ciò che legge la libreria standard, e
non richiede alcun decoder in una build che già combatte con dipendenze native.

I nomi dei file vengono dalla frase, in minuscolo, con la punteggiatura
**eliminata** anziché sostituita — così «that's enough» e «thats enough» sono la
stessa clip. Trasformare un apostrofo in separatore darebbe `that_s_enough`, e un
pacchetto registrato su una delle due grafie mancherebbe l'altra in silenzio.

## Dove stanno i pacchetti

**Impostazioni → Voce** è il posto in cui sono elencati tutti: cosa è installato,
cosa è incluso e cosa si può scaricare. I pacchetti stanno accanto alla tua
configurazione, in `voices/`, non sotto la cartella di installazione: un
aggiornamento sostituisce quella cartella per intero, e un pacchetto è molto
audio che hai scelto di metterci. **Impostazioni → Voce → Apri cartella dei
pacchetti voce** la apre.

Metti dentro una cartella, riapri la scheda, e compare nel selettore.

## L'elenco delle frasi

**Impostazioni → Voce → Scrivi elenco frasi** esporta ogni frase che l'ingegnere
può dire, in CSV, nella lingua dell'ingegnere — perché un pacchetto si registra
nella lingua in cui verrà parlato.

È generato dall'app invece che tenuto a mano, quindi non può discostarsi da ciò
che l'ingegnere dice davvero. Usalo se registri fuori dall'app o se ti scrivi un
generatore tuo.

## Non si sente nulla

**Controlla che sia selezionato un pacchetto.** *Ingegnere → Voce → Voce* deve
puntare al pacchetto e non a *(nessun pacchetto)*.

**Controlla il dispositivo di uscita.** *Audio → Uscita* dovrebbe essere le tue
cuffie, le stesse che usi per la chat vocale, non l'uscita del simulatore.

**Una frase mancante non è un guasto.** Tutto ciò che non è nel pacchetto ricade
sulla voce di Windows, così un pacchetto registrato a metà suona come due persone
invece di fallire. È voluto: è ciò che rende un pacchetto utilizzabile prima di
essere finito.
