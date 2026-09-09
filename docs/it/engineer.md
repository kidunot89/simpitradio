# L'ingegnere

Una voce con un nome che osserva il simulatore e ti parla: i tuoi tempi sul giro,
le auto affiancate e risposte quando gli chiedi qualcosa.

Condivide il tasto push-to-talk con tutto il resto di SimPitRadio. Tieni premuto
il trigger, di' « Chief, target P3 », rilascia — e invece di finire nella
finestra di chat, risponde l'ingegnere.

**È spento finché non lo accendi.** Non viene detto nulla finché non vai in
Impostazioni → Ingegnere e spunti la casella.

---

## Avvio rapido

1. Apri **Impostazioni → Ingegnere** e spunta **Ingegnere attivo**.
2. Scegli uno dei quattro ingegneri. Questo imposta il nome, la voce e quanto
   parla.
3. Premi **Test**. Dovresti sentirlo ripetere il proprio nome.
4. Imposta il **Dispositivo di uscita** sulle tue cuffie — le stesse che usi per
   la chat vocale, non l'uscita del simulatore.
5. Guida. Ti leggerà il tempo sul giro al traguardo.
6. Tieni premuto il trigger e di' **« Chief, target P3 »** per avviare il coach
   di curva contro chi è terzo.

Se Test non dice nulla, vedi [Non viene detto nulla](#non-viene-detto-nulla) in
fondo.

---

## Parlargli

Ci sono due modi in cui una frase diventa un comando, ed entrambi sono
volutamente stretti. Lo stesso tasto invia messaggi a tutti nella tua sessione,
quindi un comando che l'ingegnere *si inventa* è un messaggio che non arriva
mai, in silenzio.

**Di' prima il suo nome.** « Chief, target P3. » Il nome viene per primo, la
formula subito dopo. `hey`, `ok` e `right` sono ammessi davanti al nome.

**Oppure di' una formula da sola** — ma solo quelle che non prendono un pilota.
« initiate corner coaching » funziona senza nulla davanti. « target Verstappen »
no, perché « target » potrebbe iniziare una frase qualunque e il suo argomento
non ha fine: *« target time is a twenty three »* verrebbe altrimenti inghiottito
intero e non raggiungerebbe mai la finestra di chat.

Dire solo il nome ottiene « go ahead », come farebbe una radio vera — e tiene un
« Chief » sfuggito fuori da un messaggio diretto ad altre venti persone.

**« Stop »** funziona sempre, qualunque cosa sia in corso e qualunque cosa
l'abbia avviata. Lo stesso vale per « stand down », « cancel », « that's enough »
e « forget it ».

Tutto ciò che l'ingegnere non riconosce è un messaggio, e va nella finestra di
chat esattamente come prima.

---

## Scegliere un ingegnere

Quattro sono inclusi nell'applicazione:

| | Voce | Stile |
| --- | --- | --- |
| **Chief** | maschile | Pacato e completo. « Curva quattro, Tandy era più veloce in uscita, due decimi. » |
| **Ada** | femminile | Asciutta. Salta il numero di curva: « Tandy, uscita migliore, due decimi. » |
| **Marshall** | maschile | Più lento e più ricco, se gli altri sembrano frettolosi. |
| **Vic** | femminile | Rapida e breve. Quella che parla meno delle quattro. |

Sono **preimpostazioni, non registrazioni** — un nome, una voce Windows
preferita, un ritmo e quanto dicono. Vale la pena dirlo chiaramente, perché
« quattro voci » di solito significa quattro set di audio: un pacchetto voce
generato pesa uno o due gigabyte, e distribuirne quattro sarebbe un download da
otto gigabyte per sostituire qualcosa già presente gratis su ogni macchina
Windows.

Ognuno sceglie la migliore voce Windows installata che corrisponda alla propria
preferenza e alla tua lingua. Su un'installazione standard di Windows 11 di
solito ce ne sono due o tre, quindi due ingegneri possono condividere una voce e
distinguersi per ritmo e formulazione. Se ne vuoi una precisa, imposta **Voce
Windows** e questa ha la precedenza sulla preimpostazione.

**Chiamato** è ciò a cui risponde. Impostalo come vuoi — il nome serve solo per
rivolgersi a lui, e « Bob, target P3 » funziona altrettanto bene.

---

## Cosa ti dice

### Tempi sul giro

Legge il tuo giro mentre tagli il traguardo, e dice quando è stato il tuo
migliore. Attivo per impostazione predefinita.

### Spotter

Annuncia le auto affiancate: « car left », « car right », « cars both sides »,
poi « clear » quando se ne sono andate. Disattivato per impostazione predefinita,
e c'è una cosa da sapere.

**Quale lato sia quale non è stato possibile verificarlo senza un'auto in
pista.** Le posizioni provengono dalle coordinate del mondo del simulatore, e se
il calcolo risulti sinistra o destra dipende da una convenzione di orientamento
che questo progetto non ha potuto controllare da una macchina di sviluppo.
Quindi se annuncia « sinistra » per un'auto alla tua destra, attiva **Inverti i
lati dello spotter** in Profili → impostazioni del plugin del gioco. Una spunta,
una volta sola.

Tutto il resto dello spotter è esatto: usa le posizioni di gioco, scarta
l'altezza (così un ponte o le esse di Le Mans non mettono qualcuno contro la tua
portiera) e non annuncia auto su un rettilineo adiacente.

### Danni

Dice cosa si è rotto e se rientrare per questo. Attivo per impostazione
predefinita, e richiede un simulatore che pubblichi le condizioni dell'auto —
oggi è Le Mans Ultimate.

> *Hai perso carrozzeria. Ai box questo giro.*

**Detto quando cambia, non finché dura.** Un pilota che si trascina un
posteriore sinistro ammaccato per mezz'ora non ha bisogno che glielo si ricordi a
ogni passaggio, quindi parla nel momento in cui peggiora e poi tace. Ogni parte
della lettura è sorvegliata, non solo la peggiore — una seconda cosa che si
stacca da un'auto già ammaccata è una notizia anche se la gravità non è
cambiata.

**Quello che dice è dove, poi se.** Sai già di aver colpito qualcosa; quello che
non vedi dall'abitacolo è quanto sia grave e se ci sia tempo per ripararlo. Così
nomina il punto — il muso, la coda, tutta la fiancata sinistra — e poi dà una di
tre risposte:

| | |
| --- | --- |
| **Ai box questo giro** | l'auto non può essere corsa, solo riportata dentro: un pezzo che pende, una foratura, una ruota persa, un muso rotto. Il tempo rimanente non cambia nulla — l'alternativa è una bandiera nera o un muro |
| **Ai box appena puoi** | vale la riparazione. Sempre nelle prove e in qualifica, dove una sosta non costa nulla e il senso di essere fuori è avere un'auto che funziona |
| **Resta fuori, ce la faremo così** | una gara con meno di un quinto da correre. A tre giri dalla fine è meglio portare a casa un'auto malandata che restituire un minuto |

I danni leggeri ricevono la prima metà e nessun consiglio. Sentirsi chiedere di
valutare una sosta per un parafango posteriore graffiato è peggio che non sentire
nulla.

Non parla mai sopra il coach. I danni sono urgenti — vuoi sapere che l'ala se n'è
andata prima della curva successiva e non dopo — ma una critica che hai chiesto
tu non merita di essere interrotta per un'auto che sarà ancora rotta fra quattro
secondi. Lo spotter è l'unico annuncio che parla sopra qualsiasi cosa.

---

## Chi osserva

L'ingegnere mantiene un **focus**: un pilota con cui ti confronta. Non devi
impostarlo. Per impostazione predefinita è **l'auto davanti nella tua classe**, o
quella dietro quando sei in testa — perché non c'è nessuno davanti da inseguire,
e la domanda diventa se riesci a tenerli dietro.

Segue un cambiamento solo dopo che la posizione è stata **mantenuta per otto
secondi**. Le posizioni si rimescolano di continuo: misurato a una vera partenza
di gara, quindici piloti diversi sono stati l'auto davanti in novanta secondi, e
ogni scambio buttava via i giri raccolti, tanto che non ne aveva mai abbastanza
per dire alcunché.

Dillo se vuoi qualcun altro:

- `focus on {pilota}` — oppure « keep an eye on », « keep tabs on », « study »,
  « watch »
- `default focus` — torna a scegliere da solo
- `stop focusing` — spento, e resta spento finché non lo richiami

Un pilota che nomini tu non viene mai scavalcato. Tornare due curve dopo su chi è
davanti sarebbe l'applicazione che ti contraddice.

La scheda Stato mostra chi viene osservato, e `what are we watching` lo chiede.

---

## Chiedergli cose

Ogni domanda ha una casella di formule in Impostazioni → Ingegnere, una per
riga, e quello che scrivi sostituisce i valori predefiniti. Ognuna può essere
disattivata; una domanda disattivata non contribuisce con alcuna formula, quindi
le sue parole raggiungono la finestra di chat come tutte le altre invece di
essere prese e risposte con nulla.

- **La tua auto** — `what's my best lap`, `how are the tyres`, `what's the
  damage`, `how's the fuel`, `how much fuel do I need to finish the race when I
  pit on the next lap`
- **La sessione** — `who has the fastest lap`, `who's fastest`,
  `who has the fastest sector`, `who's in the lead`, `who's ahead`
- **Dove va il tempo** — `where am I slower`, `where am I faster`, l'una o
  l'altra con `than {pilota}` in fondo

**Le domande saltano la coda.** Una domanda posta mentre l'ingegnere era a metà
di un annuncio aspettava dietro o veniva scartata del tutto — la coda ne tiene
sei e un giro affollato la riempie — quindi chiedevi, lo sentivi parlare
d'altro, e non ottenevi risposta. Una risposta ora sgombra il traffico ordinario,
interrompe quello che si sta dicendo e non può essere spinta fuori. Cede sempre
allo spotter, perché un'auto affiancata riguarda il non schiantarsi.

**Una domanda a cui non può rispondere resta fuori dalla finestra di chat.**
« Who's faster? » non è una formula che conosce, e prima passava attraverso e
finiva alla sessione. Tutto ciò che si legge come una domanda — finisce con un
punto interrogativo, o inizia con un interrogativo — riceve invece « say again ».
C'è una casella nella scheda Chat testuale se preferisci il vecchio
comportamento, e una domanda che hai esplicitamente disattivato raggiunge
comunque la chat, perché disattivarla è il tuo modo di dire che quelle parole
sono tue.

Puoi mettere il nome dell'ingegnere a un'estremità o all'altra: « Bono, how are
the tyres » e « how are the tyres, Bono » funzionano entrambi. È la virgola a
segnarlo come nome, quindi `focus on Bono` punta ancora a un pilota di nome
Bono.

### Dove sono più lento

Quella che vale la pena conoscere. Ti confronta con il tuo focus **curva per
curva, mediato su ogni giro di questa sessione** invece che letto da uno solo —
un singolo giro dice cosa è successo in quel giro, e la domanda riguarda ciò che
continua a succedere.

> Chief, where am I slower
>
> *Curva tre, sei più lento in ingresso, due decimi.*
>
> *Curva sette, ha un'uscita migliore, un decimo.*

Dice *come*, non solo dove: ingresso, uscita, frenata più tardi, o più lento in
tutta la curva. Dove esiste un catalogo di curve per il circuito usa il nome —
« Eau Rouge » invece di « curva tre ».

**Come trova le curve.** Non c'è una mappa del circuito e non ci sarà —
servirebbe un file per tracciato, invecchierebbe a ogni cambio di configurazione,
e funzionerebbe sui quattro circuiti che qualcuno ha fatto in tempo a fare. Una
curva è un punto dove il giro di riferimento ha rallentato ed è tornato ad
accelerare, il che è vero su ogni circuito di ogni simulatore. Le chicane
contano come una sola curva.

**Descrive, non istruisce.** « Ha un'uscita migliore » è ciò che l'applicazione
sa. Non sa se sia stata la traiettoria, le gomme o la scia, e « frena più tardi »
sarebbe un'ipotesi travestita da coaching.

**Se mancano dei giri dice di chi.** Tuoi o suoi — altrimenti « nessun giro da
confrontare » ti lascia indovinare quale.

### Cosa non userà come riferimento

- Un giro con una qualsiasi parte nella corsia box. Un giro veloce che in realtà
  era una scorciatoia attraverso i box diventerebbe altrimenti il bersaglio con
  cui tutti vengono misurati, e nulla sembrerebbe sbagliato.
- Un giro a cui ti sei unito a metà.
- Un giro per cui il simulatore non ha dato alcun tempo — un giro di uscita, o
  un'auto appena arrivata.
- Qualsiasi cosa da un circuito diverso. Cambiare tracciato azzera tutto.

Tace anche mentre sei spettatore. Commentare un giro che stai guardando invece
che guidando non avrebbe senso.

---

## Quando il tuo simulatore non può rispondere

Non tutti i simulatori pubblicano le stesse cose, e l'ingegnere lo dice invece di
indovinare. Assetto Corsa originale, per esempio, pubblica **la tua auto e nulla
su nessun altro** — nessun nome, posizione o tempo sul giro di un altro pilota —
quindi qualunque cosa ti confronti con la griglia non ha dati per nessuna via.

Chiedigli « who's leading » e risponde **« questo gioco non lo dice »**. È voluto
e non è la stessa cosa di « nessuno da osservare », che significa che la griglia
è davvero vuota. Dire a un pilota che è settimo che non c'è nessuno davanti a lui
non è una risposta inutile, è una risposta falsa.

I comportamenti che hanno bisogno di dati che il tuo simulatore non fornisce
vengono saltati con una riga nel registro invece di essere lasciati attivi e
muti:

```
Spotter is on but this sim does not publish positions or spotter; it will stay quiet
```

`--telemetry` stampa cosa sta effettivamente inviando il tuo simulatore — vedi
l'ultima sezione.

---

## Altre lingue

L'ingegnere parla la lingua che hai impostato per la **trascrizione**, a meno che
non la fissi nella scheda Ingegnere. È il valore predefinito giusto e non
arbitrario: i tuoi comandi arrivano attraverso Whisper, quindi se Whisper produce
spagnolo, un ingegnere in ascolto di formule inglesi non ne sentirà mai nemmeno
una.

Tutto ciò che dice — comprese le formule di attivazione — passa per gli stessi
cataloghi di traduzione della finestra. Aggiungere una lingua è un file JSON in
`src/pitradio/locale/`; vedi il README principale.

**I numeri sono scritti per esteso in inglese e letti come cifre ovunque
altrove.** Non per pigrizia: la grammatica dei numeri è davvero specifica per
lingua — il tedesco inverte decine e unità, lo spagnolo fonde le ventine — e
un'implementazione fatta a metà produrrebbe assurdità dette con sicurezza nella
lingua di qualcuno. Le cifre passano il problema alla voce sintetica di quella
lingua, che lo risolve già correttamente. La conseguenza è che un pacchetto voce
non inglese non può coprire i numeri, e questi escono sintetizzati.

---

## Pacchetti voce

**Da quale pacchetto parla questo ingegnere si imposta qui, nella scheda
Ingegnere**, e il coach sceglie il suo nella scheda Coaching — sono due mestieri
distinti e un pilota può ragionevolmente voler sentire quale dei due sta
parlando.

**Installare, registrare e rimuovere pacchetti è Impostazioni → Voce.** Un
pacchetto è qualcosa che l'applicazione possiede; quello da cui una persona parla
è un'impostazione di quella persona.

Due pacchetti sono inclusi: **Norman** e **Claudia**. Entrambi sono stati
generati con Piper — vedi [voicepacks.md](voicepacks.md) — ed entrambi possono
essere sostituiti da un pacchetto tuo.

Un pacchetto voce sostituisce il sintetizzatore con audio registrato: una
cartella di file WAV, una cartella per frase, diverse prese ciascuna.
L'ingegnere sceglie una presa a caso, ed è per questo soprattutto che un
pacchetto suona come una persona e la sintesi vocale no.

**La disposizione è quella di Crew Chief**, di proposito:

```
%APPDATA%\pitradio\voices\
  Ada\
    voice\
      corners\
        two_tenths\
          a.wav
          b.wav
```

Anche un `<pacchetto>/<frase>/*.wav` piatto funziona, ed è quello che ottieni
registrando tu stesso.

Quella disposizione fa sì che un pacchetto generato da
[crew-chief-autovoicepack](https://github.com/cktlco/crew-chief-autovoicepack)
possa essere inserito così com'è. Per generarne uno per le frasi di SimPitRadio
invece che per quelle di Crew Chief:

1. Impostazioni → **Voce** → **Scrivi l'elenco delle frasi**. Questo scrive
   `phrase_inventory.csv` nella cartella delle voci, nella lingua
   dell'ingegnere.
2. Dai quell'inventario al generatore al posto del suo.
3. Metti la cartella di output sotto `voices\` e scegliela nella scheda Ingegnere
   (o usa **Impostazioni → Voce → Apri la cartella dei pacchetti voce** per
   arrivarci).

**Nomi e numeri non sono mai in un pacchetto** e vengono sempre detti dalla voce
Windows. Non c'è modo di aggirarlo — nessun pacchetto può contenere il nome di
ogni pilota o ogni tempo sul giro — quindi un annuncio come « curva quattro,
Tandy era più veloce in uscita » è in parte registrato e in parte sintetizzato.
Quella cucitura si sente. Resta comunque il compromesso giusto: l'alternativa è
un pacchetto che resta inutilizzato appena si nomina un pilota, cioè nella
maggior parte degli annunci.

I pacchetti sono conservati accanto alla tua configurazione, non nella cartella
di installazione, così un aggiornamento non cancella un gigabyte di audio che hai
scelto di installare.

---

## Come sta insieme

L'ingegnere gira su **un thread proprio**, separato dai quattro che SimPitRadio
ha già, e il parlato ottiene un thread sotto di quello. Nessuno dei due può
trattenere l'hook della tastiera, il worker o la finestra.

Tutto ciò che fa può fallire. Che l'ingegnere ammutolisca non deve mai costarti
un trigger, una trascrizione o un messaggio nella chat — quindi se qui dentro si
rompe qualcosa, le parole vanno alla chat come sempre e il problema è una riga
nel registro.

Legge il simulatore dieci volte al secondo attraverso lo stesso plugin che
fornisce i nomi dei piloti per le menzioni. Non c'è un secondo percorso dati né
una connessione aggiuntiva al gioco.

---

## Non viene detto nulla

**Test non fa nulla.** Il sintetizzatore gira in un host PowerShell usando
`System.Speech`, che fa parte del .NET Framework su ogni macchina Windows 10 e
11. Cerca `no speech host` nel registro — una macchina bloccata con PowerShell
disabilitato è la causa abituale.

**Lo senti, ma non nelle cuffie.** Imposta il dispositivo di uscita nella scheda
Audio. Per impostazione predefinita è il dispositivo di sistema, che durante una
gara è spesso l'altoparlante del volante.

**Legge i tempi sul giro ma non fa mai coaching.** Il coach di curva ha bisogno
di un giro di riferimento. Finché il pilota che hai preso di mira non ne ha
completato uno — pulito, non attraverso i box — non c'è nulla con cui
confrontare. La riga di stato della scheda Ingegnere dice quante curve ha
mappato.

**Fa coaching ma non dice nulla in alcune curve.** È il progetto: quelle curve
erano entro la soglia. Abbassa **Soglia di curva** se ne vuoi di più.

**Non risponde a nulla di quello che dici.** Controlla il nome nella scheda
Ingegnere, e ricorda che ogni formula che prende un pilota ha bisogno del nome
davanti. Di' « Chief » da solo — se ottieni « go ahead », sta ascoltando e il
problema è la formula.

**Ha mangiato un messaggio.** Non dovrebbe. Se l'ingegnere ha preso qualcosa che
volevi inviare, la riga del registro dice `that was for the engineer` insieme a
ciò che ha riconosciuto — per favore apri una segnalazione con quella riga,
perché un matcher troppo zelante è l'unico bug di questa funzione che costa
qualcosa di reale.

---

## Controllare cosa sta davvero inviando il tuo simulatore

La maggior parte dei problemi « l'ingegnere non dice nulla » non è l'ingegnere.
Avvia il gioco, mettiti **in pista e in movimento**, poi:

```bash
python -m pitradio --telemetry
```

Stampa ogni auto come la vede l'ingegnere — distanza sul giro, velocità, numero
di giri, settore, tempi, flag box, posizione nel mondo — e, cosa più utile,
confronta letture consecutive e ti dice se qualcosa sta cambiando.

Quest'ultima parte conta più di quanto sembri. Un simulatore in pausa o fermo in
un menu continua a pubblicare un blocco che sembra del tutto sano: auto,
posizioni, velocità, tutto plausibile. Nulla si muove, quindi l'ingegnere non ha
nulla da dire, e nessuna singola istantanea lo mostra. Se segnala

> Nothing changed across 4 reads, including the sim's own clock.

allora il gioco è in pausa, in un menu, o la sessione è finita — non è rotto.

Cosa guardare quando *è* vivo:

| Colonna | Alimenta |
| --- | --- |
| `lapdist`, `speed` | il rilevamento delle curve, e dove va il tempo |
| `lap`, `last lap`, `best lap` | gli annunci di tempo sul giro e giro veloce |
| `sec` — cambia tre volte a giro | ogni annuncio di settore |
| `world x/y/z` — diverso per auto | lo spotter |

La riga `provides:` in cima dice quali di queste cose il plugin dichiara di
fornire. Un comportamento che ha bisogno di qualcosa di assente viene saltato
invece di essere lasciato attivo e muto, e il registro dice quale capacità
manca.

## Cosa sa fare ogni simulatore

I simulatori pubblicano cose molto diverse, e un comportamento i cui dati mancano
viene **saltato con una riga nel registro** invece di essere lasciato attivo e
muto.

| | Le Mans Ultimate | iRacing | Assetto Corsa / Competizione / Evo | Automobilista 2, Project CARS 2 / 3 |
| --- | --- | --- | --- | --- |
| Tempi sul giro | sì | sì | sì | derivati |
| Nuovo giro veloce | sì | sì | — | sì |
| Annunci di settore | sì | — | sì | — |
| Dove sono più lento | qualsiasi pilota | qualsiasi pilota | il tuo migliore | qualsiasi pilota |
| Chi è davanti / in testa | sì | sì | — | sì |
| Spotter | geometria | l'annuncio del simulatore stesso | solo Competizione | geometria |
| Menzioni di piloti, « P3 » | sì | sì | — | sì |
| Danni | sì | — | — | — |
| Coaching e diagramma di segmento | sì | — | — | — |

Le lacune sono dei giochi, non dell'applicazione:

- **iRacing** non pubblica i tempi per settore e per auto, quindi gli annunci di
  settore non hanno nulla su cui lavorare. Il suo spotter è il migliore di tutti
  — `CarLeftRight` viene dalle carrozzerie reali, quindi non serve né
  l'impostazione di inversione né una stima della larghezza.
- **Assetto Corsa** pubblica i tempi solo per la tua auto e nessun nome di
  pilota. È per questo che non ci sono classifiche né menzioni, e perché « dove
  sono più lento » insegue il tuo miglior giro — che è comunque a cosa serve una
  sessione di prove.

  Il gioco originale va oltre: non pubblica **nessun'altra auto**, nemmeno una
  posizione. Verificato contro una vera gara a otto auto, l'array di coordinate
  conteneva il giocatore nello slot zero e memoria intatta in ogni altro — zeri,
  un NaN, un denormale. Quindi neanche lì lo spotter ha qualcosa su cui lavorare,
  e il plugin lo dice per sessione e non per gioco: **Competizione pubblica**
  quell'array, e lo stesso plugin vi riporta le posizioni.
- **Automobilista 2 e Project CARS** portano *conteggi* di giri invece dei tempi
  nella parte del loro blocco degna di fiducia, quindi i tempi qui sono misurati
  a cronometro. Un giro che attraversa una pausa risulta più lungo di quanto sia
  stato; questo fallisce dalla parte giusta, dato che un giro gonfiato non
  diventa mai il riferimento che un confronto insegue. Il loro campo settore è un
  enum che non si è potuto determinare dall'esterno dei giochi, quindi gli
  annunci di settore non sono offerti.

Automobilista 2 ha una voce propria invece di condividere quella di Project CARS,
così puoi scegliere il gioco che stai effettivamente usando e così i due
mantengono impostazioni separate di spotter e prossimità.

**Le Mans Ultimate è l'unico verificato contro il gioco in esecuzione.** Ogni
altro lettore è testato contro memoria condivisa costruita a mano, il che
intercetta una larghezza di campo sbagliata, un nome decodificato male o un
errore di riempimento — e non può intercettare un'ipotesi sbagliata su cosa il
simulatore metta dove. Esegui `--telemetry` con il gioco in pista prima di
fidarti di uno qualsiasi di essi, e soprattutto di Assetto Corsa Evo, ancora in
accesso anticipato e che potrebbe spostare la propria disposizione.

**iRacing è marcato sperimentale**, e appare come tale nel selettore dei profili.
Non perché sia codice peggiore degli altri, ma perché nessuno che lavora a
SimPitRadio ne possiede una copia — quindi, a differenza del resto, non verrà
verificato contro la realtà a meno che qualcuno che ce l'ha esegua `--telemetry`
e dica cosa è tornato. Se sei tu, fallo pure; la nota nell'elenco dei plugin
chiede esattamente questo.

## Impostazioni per simulatore

Tre dei numeri dell'ingegnere vivono sul **profilo**, sotto le impostazioni del
plugin del gioco, e non nella scheda Ingegnere — perché descrivono il gioco
piuttosto che i tuoi gusti:

- **Inverti i lati dello spotter** — se « sinistra » indica un'auto alla tua
  destra
- **Sovrapposizione spotter (metri)** — quanta distanza lungo la pista conta
  ancora come affiancati. Una Hypercar è lunga circa 5 m
- **Larghezza spotter (metri)** — quanto di lato conta, prima che siano
  semplicemente su un'altra parte del circuito

Lunghezze delle auto e convenzioni degli assi differiscono tra simulatori, quindi
un numero che va bene per un gioco è sbagliato nel successivo.

## Bandiere e incidenti

Un comportamento a sé, e separato dallo spotter di proposito. Le cartelle di
suoni di Crew Chief tracciano la linea ed è quella giusta: `car_left`,
`still_there` e `clear_all_round` sono in `spotter/`, mentre
`stopped_car_in_turn_3`, `slow_car_ahead` e `local_yellow_ahead` sono in
`flags/`. Lo spotter risponde a « chi è accanto a me », che è geometria. Le
bandiere rispondono a « cosa è successo alla pista », che non lo è.

Dedurre la seconda dalla prima è ciò che produceva un avviso in ogni zona di
frenata: SimPitRadio aveva una regola secondo cui un'auto molto più lenta di te
era un pericolo, e una zona di frenata è precisamente il punto in cui l'auto
davanti è molto più lenta di te. Quella regola non c'è più.

**Tre fonti, non ugualmente affidabili.**

La *bandiera gialla su tutto il circuito* e la *blu* vengono dal simulatore e
sono affidabili — `mGamePhase`, `mYellowFlagState` e il `mFlag` per auto di LMU
si leggono tutti sensatamente contro una sessione dal vivo.

I *gialli locali sono dedotti*, perché il `mSectorFlag` di LMU è inutilizzabile.
È documentato come « se ci sono gialli locali in questo momento in ciascun
settore » e legge `[11, 11, 1]` sotto bandiera verde, con i campi ai due lati
corretti — quindi non è uno scostamento che è slittato, LMU pubblica
semplicemente altro lì. Letto come booleani, metterebbe un giallo permanente su
tutto il circuito. Quindi un incidente qui significa ciò che intende un
commissario: un'auto si è fermata sulla strada e ci è da due secondi. È una
deduzione da dati che il simulatore pubblica onestamente, nello stesso spirito
del trovare le curve nella traccia di velocità invece di distribuire una mappa
del circuito.

Il costo è che l'annuncio non può precedere l'incidente — un giallo vero esce nel
momento in cui i commissari lo vedono, e questo aspetta di esserne sicuro. Il
beneficio è che non sbaglia mai su una pista verde, che è il guasto che spinge le
persone a disattivare una funzione.

**Gli incidenti sono nominati per curva, non per pilota.** Alla velocità a cui
questo conta, « curva sei » è qualcosa su cui un pilota può agire e un nome è un
conteggio di sillabe su cui non può. La numerazione è quella del quaderno dei
giri, così un pilota sente un solo insieme di numeri di curva invece di una
funzione che ne usa uno e le bandiere un altro; le curve vengono trovate una
volta per giro di riferimento e messe in cache, perché `find_corners`
ricampiona un giro intero e questo gira diverse volte al secondo. Senza ancora un
giro di riferimento viene nominato il settore.

**Quando l'incidente sei tu, gli annunci laterali si fermano.** Descrivere al
pilota di un'auto in testacoda le auto che passano è rumore; l'unica domanda
utile è se ci sia spazio per rientrare, e
[rejoin.py](../src/pitradio/engineer/rejoin.py) vi risponde — confrontando *il
tempo per essere al sicuro* con *il tempo prima dell'arrivo della prossima auto*,
non una distanza con una distanza. Un'auto ferma deve recuperare tutta la sua
accelerazione prima del primo arrivo. È per questo che la risposta ingenua « tre
secondi di pista libera » fa raccogliere le persone.

Due protezioni, entrambe apprese e non supposte: nulla viene detto nella corsia
box, dove stare fermi è lo scopo, e nulla prima che l'auto si sia mai mossa —
stare in griglia prima dei semafori significa essere fermi, sulla traiettoria,
con tutto il gruppo dietro, che è esattamente ciò che guarda il consiglio di
rientro.

Vedi [voicepacks.md](voicepacks.md) per generare una voce.

## Domande

Distinte dai comportamenti, e la distinzione non è contabilità. Un comportamento
è qualcosa che l'ingegnere *continua a fare* — vedi [Cosa ti
dice](#cosa-ti-dice) — e porta un intervallo di ripetizione, perché un'auto
affiancata smette di esserci senza che accada nulla. Una domanda ha una risposta,
e quando la risposta è stata data non c'è nulla in esecuzione. Modellare l'una
come l'altra metterebbe « who has the fastest lap » nell'elenco dei
Comportamenti, dove ogni voce ha un intervallo di ripetizione, e non esiste una
cosa come rispondere di nuovo a una domanda ogni 1,2 secondi.

Tre di esse: il giro veloce, il settore più veloce e il tuo migliore.

**Il parametro segue la parola chiave e non fa mai parte della formula.** Ciò che
un pilota può chiedere dipende dal simulatore in cui si trova — le classi di
questa griglia, i settori di questo circuito — e nulla di tutto ciò ha posto in
una formula che qualcuno ha digitato in una casella di impostazioni. « Who has
the fastest sector » è la formula; « three in GT3 » è ciò che è venuto dopo,
analizzato contro la sessione. Una classe è riconosciuta tramite
`mentions.class_aliases`, così il « LMGT3 » di LMU risponde a « GT3 » esattamente
come ovunque altrove, e « LMP2 » continua a rifiutare di rispondere a « P2 »
perché quella è una posizione.

**Uno spazio di argomenti chiuso è la difesa contro i falsi positivi**, e
migliore del contare le parole. `phrases.MIN_BARE_WORDS` protegge i comandi
parlati richiedendo due parole davanti a un parametro aperto; qui non basta,
perché « who has the fastest lap of my life that one » lo supera facilmente e
verrebbe preso come una domanda su una classe chiamata « of my life that one » —
inghiottendo il messaggio. Ma l'argomento di una domanda può essere solo una
classe di questa griglia, un settore fra uno e tre, o nulla. Tutto il resto non
era una domanda, qualunque cosa fosse all'inizio. Rivolta per nome lo è comunque:
chi ha detto il nome dell'ingegnere stava parlando con lui.

**Nessuna classe nominata significa la tua classe**, perché è ciò che intende
qualcuno su una GT3 che chiede « who has the fastest lap ». A una classe nominata
in cui non c'è nessuno viene detto questo invece di essere servita in silenzio
con la cifra generale — una risposta sbagliata data con sicurezza è il guasto
senza sintomo.

Ognuna ha una casella nella scheda Ingegnere e nient'altro. Ciò su cui una
domanda può vertere è fissato da ciò che il simulatore pubblica, quindi una
casella di formule modificabile là implicherebbe che tu possa inventarne una.

L'interruttore si guadagna il posto per un motivo diverso: **ogni formula che
l'ingegnere ascolta è una formula che può essere estratta da un messaggio
destinato a tutta la sessione**, e chi non fa mai queste domande non ha motivo di
correre quel rischio. Disattivarne una rimuove del tutto le sue formule dal
matcher invece di zittirla a valle — altrimenti « who has the fastest lap »
verrebbe comunque estratta dal messaggio e poi risposta con nulla, che è il
peggio di entrambi. Assente dalla configurazione significa attiva, quindi
aggiungere una domanda non richiede mai una migrazione.

## Lo spotter, e da dove vengono i suoi numeri

Ogni soglia in `spotter.py` è quella di Crew Chief, letta da un'installazione
locale invece che indovinata — il suo `ui_text/en.txt` nomina ogni impostazione e
`CrewChiefV4.exe.config` fornisce i valori predefiniti:

| Il nostro | Quello di Crew Chief | Predefinito |
| --- | --- | --- |
| `DEFAULT_CAR_LENGTH` | `lmu_spotter_car_length` | 4,5 (5 per pcars2/ACC, 4,4 per AMS2) |
| `GAP_FOR_CLEAR` | `spotter_gap_for_clear` | 0,5 m |
| `OVERLAP_DELAY` | `spotter_overlap_delay` | 50 ms |
| `CLEAR_DELAY` | `spotter_clear_delay` | 150 ms |
| `MIN_SPEED` | `min_speed_for_spotter` | 10 m/s |
| `MAX_CLOSING_SPEED` | `max_closing_speed_for_spotter` | 12 m/s |
| l'intervallo di ripetizione | `spotter_hold_repeat_frequency` | 3 s |

Tre di questi mancavano del tutto qui e ciascuno causava un difetto che il pilota
poteva sentire:

**Il limite di velocità di avvicinamento è ciò che intercetta l'auto che
doppia.** Qualcosa che arriva 12 m/s più veloce attraversa l'intera finestra di
sovrapposizione in ben meno di un secondo, così che quando l'annuncio è stato
detto è già passata — e il pilota tiene una traiettoria per un'auto che non c'è
più.

**La velocità minima è ciò che ferma la corsia box e la griglia.** Sotto i 10 m/s
le auto attorno a te sono ferme o passano a passo d'uomo, e annunciarle è il modo
in cui uno spotter finisce disattivato.

**I due ritardi di assestamento sono ciò che ferma le chiacchiere.** Due auto
nella stessa curva entrano ed escono dalla sovrapposizione al ritmo del loro
respiro. Sono volutamente di lunghezze diverse: il ritardo di sovrapposizione è
breve perché un avviso in ritardo non vale nulla, e il ritardo di liberazione è
più lungo perché può permettersi di essere sicuro — un pilota che tiene la
propria linea un decimo più del necessario non ha perso nulla.

La portata di liberazione è `lunghezza dell'auto + spazio`, non un secondo
multiplo della lunghezza. La distinzione conta agli estremi: per un kart
« un'altra lunghezza d'auto » sono due metri di isteresi e l'annuncio si trascina
troppo a lungo, mentre mezzo metro di luce è mezzo metro qualunque cosa tu stia
guidando.

**Lo spotter è muto sotto bandiera gialla su tutto il circuito** — il
`fcy_stop_spotter_immediately` di Crew Chief, attivo per impostazione
predefinita. Il gruppo è compattato a passo d'uomo e permanentemente
sovrapposto, quindi ogni annuncio sarebbe vero e inutile.

### Cosa dice

Il vocabolario è la cartella `Sounds/voice/spotter/` di Crew Chief, quindi un
pacchetto voce costruito per Crew Chief lo dice tutto senza una mappatura:
`car_left`, `car_right`, `still_there`, `hold_your_line`, `in_the_middle`,
`clear_left`, `clear_right`, `clear_all_round`, `three_wide_on_left`,
`three_wide_on_right`.

Due di questi hanno sostituito annunci che dichiaravano lo stesso fatto per la
via più difficile:

* **« Three wide, you're on the right »** era « two cars left ». Un pilota che
  sente il vecchio deve calcolare dove lo lascia, mentre è occupato; il nuovo
  dice direttamente da che parte non c'è spazio.
* **« In the middle »** era « three wide », per un'auto per lato.

Una ripetizione dice `still there` da un lato e `hold your line` da entrambi,
perché sono istruzioni diverse — una significa non andare da quella parte,
l'altra significa non muoverti. L'arrivo e le sue ripetizioni condividono una
chiave derivata dai *conteggi*, così che l'intervallo di ripetizione li governi;
una chiave che cambiasse con la formulazione renderebbe il seguito un annuncio
nuovo, dovuto già al tick successivo.

**Il set ovale è volutamente assente** — `car_inside`, `clear_outside`,
`three_wide_on_inside`. Quale lato sia l'interno è un fatto sulla
sopraelevazione, che nessuno dei simulatori qui pubblica e che Crew Chief tiene
per circuito. Indovinarlo è un annuncio che è fieramente al contrario.

### Carburante

« How much fuel do I need to finish the race when I pit on the next lap », oppure
« ...when I pit in five laps ». **La risposta è una percentuale**, perché è il
numero che compare sulla schermata carburante del simulatore e il pilota ha circa
quattro secondi andando verso l'ingresso box per impostarlo. I litri sono il
calcolo.

**Il consumo è misurato, mai supposto.** Quanto consuma un'auto dipende dal
circuito, dalla mappatura motore, dal traffico e da come la persona la guida,
quindi i litri per giro qui sono ciò che *questa* auto ha consumato su *questi*
giri — una breve media mobile, così da seguire un cambio di mappatura invece di
essere trascinata indietro da un intero stint. Finché non è stato completato un
giro non c'è risposta e lo dice. Un numero di carburante inventato dal nulla è
l'unica risposta sbagliata qui che chiude la gara di qualcuno.

Tre dettagli che altrimenti verrebbero riscoperti:

* **I giri prima della sosta non vengono riforniti.** Quello che è nel serbatoio
  ora li copre. Solo quelli dopo sono la domanda, ed è per questo che questo non
  legge mai il livello attuale.
* **`mMaxLaps` vale `INT_MAX` in una sessione a tempo.** Preso alla lettera,
  chiede carburante per due miliardi di giri. `SessionInfo` porta `max_laps`
  *oppure* `ends_at`, mai entrambi, e il plugin decide quale — l'ingegnere non
  indovina mai quello mancante. Una gara a tempo divide il tempo rimanente per il
  miglior giro del pilota stesso e arrotonda **per eccesso**, perché la bandiera
  cade alla fine del giro in cui sei quando il tempo scade.
* **Un pieno oltre la capacità del serbatoio viene segnalato, non tagliato.**
  Significa che la sosta non può essere l'ultima, e un pilota a cui si dice
  « cento per cento » senza dirgli questo pianifica una gara che non funziona.

Tutto il resto arrotonda verso più carburante: restare a secco è un ritiro, e
portare un litro in più è un decimo al giro.

Il carburante raggiunge `Car` **solo per l'auto del giocatore** — i simulatori
pubblicano la telemetria del serbatoio dell'auto che stai guidando e di nessun
altro — ed è collegato facendo corrispondere `mID`, perché l'array di telemetria
di LMU è indicizzato da `playerVehicleIdx` mentre quello di classifica no.
Collegarlo per posizione metterebbe il tuo serbatoio sull'auto che si trovava
classificata in quello slot.

## Essere lontani dal volante

L'ingegnere non dice nulla, e **non registra nulla**, quando il pilota non sta
guidando. Tre stati, e servono tre segnali diversi:

* **In pausa** — l'orologio del simulatore si ferma mentre quello di questa
  macchina no, e la differenza è il segnale. Non `mGamePhase`: quello indicava
  *bandiera verde* per tutta una sessione passata in pausa nel garage, con
  `mCurrentET` congelato a 2218.0. La fase dice che tipo di sessione sia, non se
  sia in esecuzione.
* **In garage** — qui l'orologio continua, quindi l'orologio non può essere il
  segnale. `mInGarageStall` lo è. Distinto da `in_pits`, che copre tutta la
  corsia box: un'auto che sta scontando una sosta sta gareggiando.
* **Affidata all'IA** — `mControl` vale 1, che è l'aspetto della modalità
  spettatore.

**Non viene osservato nulla, non soltanto non viene detto nulla.** Un simulatore
in pausa ripubblica lo stesso fotogramma all'infinito, e dare quello al quaderno
dei giri registra un'auto che non copre alcuna distanza per tutto il tempo in cui
qualcuno lascia il gioco lì fermo — un giro di riferimento corrotto invece di uno
mancante. Lo stato dello spotter viene scartato in entrata per lo stesso motivo:
un'auto che era affiancata prima della pausa è un fatto su un istante che è
passato.

**Mettere in pausa una gara online non viene rilevato, e non può esserlo.**
L'orologio là continua, perché la gara continua — il menu è aperto su questa
macchina e le auto stanno ancora andando. Nulla nella memoria condivisa distingue
questo da una gara ordinaria, e inventare un segnale per esso zittirebbe
l'ingegnere durante una gara vera. Che è l'errore peggiore dei due.
