# Chat testuale

Ciò per cui SimPitRadio è stato costruito. Tieni premuto un tasto, di' quello che
vuoi dire, rilascia — e compare nella chat del gioco, scritto, senza che le mani
lascino il volante.

Tutto il resto nell'app è nato da qui. L'ingegnere, il coach e la chat vocale
condividono lo stesso tasto e la stessa registrazione; la chat testuale è ciò che
accade alle parole quando nessun altro le ha reclamate.

## Cosa succede mentre tieni premuto il tasto

1. **Il tasto viene inghiottito.** Il gioco non vede mai il trigger, quindi può
   essere un tasto che il gioco usa già.
2. **La registrazione parte subito** — prima che la chat si apra, non dopo.
   Aprirla richiede qualche centinaio di millisecondi e tutto ciò che venisse
   detto nel frattempo andrebbe perso.
3. **Vengono premuti i tasti della chat** per aprire la chat del gioco, e l'app
   attende `pre_delay_ms` che prenda il fuoco.
4. **Rilasci.** La registrazione si ferma e la clip va a Whisper, sulla tua CPU.
5. **Il testo viene digitato**, poi vengono premuti i tasti di invio.

Se le parole risultano essere un comando per l'ingegnere o per il coach, si
risponde a quello e non viene scritto nulla. Quella decisione è volutamente
stretta — vedi [Parlargli](engineer.md#parlargli) — perché lo stesso tasto
manda messaggi a tutti nella sessione, e un comando che l'app si inventa è un
messaggio che in silenzio non arriva mai.

## Spegnerla

**Chat testuale → Invia al gioco** è l'interruttore da cercare a metà gara quando
una sessione diventa pubblica. Spento, il trigger resta solo voce e ingegnere:
niente tasti chat, niente scrittura, niente inviato.

C'è un secondo interruttore per gioco, sotto Profili. «Questo gioco ha una chat?»
è un fatto sul gioco, non una decisione da prendere ogni sessione — Assetto Corsa
offline non ha una chat da aprire, quindi ogni pressione mandava al gioco un
Invio che lì significava altro. Impostalo una volta e dimenticalo. L'interruttore
generale vince comunque: spento lì è spento ovunque.

## Controllare un messaggio prima che parta

Per impostazione predefinita il messaggio viene inviato appena è scritto. Whisper
capisce male le cose, e in una sessione pubblica un errore è un problema di
tutti — quindi ogni profilo ha un interruttore **Invia automaticamente**.

Con quello spento, il messaggio viene scritto nella chat e lasciato lì. È poi il
tuo trigger a decidere che fine fa, senza lasciare il volante:

| Gesto | Cosa fa |
| --- | --- |
| **Tocco** | Lo invia |
| **Due tocchi** | Lo cancella |
| **Tenuta** | Lo cancella e ne registra un altro |

La scheda Stato mostra **in attesa di invio** finché un messaggio resta lì.

Se hai pulsanti da spendere, **Impostazioni → Trigger** assegna anche tasti
diretti a *Invia messaggio in attesa* e *Cancella messaggio in attesa*. Agiscono
subito, senza finestra di doppio tocco da aspettare, e convivono con i gesti
invece di sostituirli.

**Un tocco non può essere eseguito subito**, perché finché la finestra del doppio
tocco non si chiude potrebbe esserne la prima metà. Quell'attesa è
`review.double_tap_ms`, circa un terzo di secondo. Mettila a `0` nella
configurazione per inviare subito e rinunciare a cancellare col doppio tocco.
`review.tap_ms` è il confine fra un tocco e una tenuta.

**Una pressione con un messaggio in sospeso avvia subito la registrazione**, prima
di sapere se sarà un tocco o una tenuta. Aspettare di scoprirlo si mangerebbe le
prime parole di una nuova registrazione; il buffer viene buttato se poi era un
tocco.

## Profili

Quale profilo valga lo decide l'eseguibile che ha il fuoco, così più simulatori
possono essere configurati insieme e viene usato quello giusto senza chiedere.

L'impostazione che conta di più è **Ritardo apertura chat** (`pre_delay_ms`). La
chat ha bisogno di qualche fotogramma per aprirsi e prendere il fuoco, e scrivere
troppo presto perde i primi caratteri. Parti da 350 ms e alzalo se i messaggi
arrivano troncati.

| Impostazione | A cosa serve |
| --- | --- |
| **Ritardo apertura chat** | Quanto attendere dopo aver aperto la chat prima di scrivere. Quello da alzare se i messaggi arrivano troncati |
| **Tasti apri chat** | Cosa apre la chat. Invio nella maggior parte dei simulatori |
| **Tasti di invio** | Cosa la manda. Di solito ancora Invio |
| **Tasti di annullamento** | Cosa chiude la chat senza inviare, per cancellare un messaggio in attesa |
| **Tenuta tasto** | Quanto a lungo è tenuto ogni tasto. I giochi leggono l'input una volta per fotogramma, quindi una pressione più corta di un fotogramma è una pressione che il gioco non vede mai |
| **Ritardo di digitazione** | Lo spazio fra un carattere e l'altro |
| **Caratteri massimi** | I messaggi più lunghi vengono tagliati. Quasi tutti i simulatori hanno un limite proprio |
| **Invia automaticamente** | Spento per rivedere prima di inviare — vedi sopra |
| **Plugin di sessione** | Legge chi è nella sessione perché i nomi si trascrivano bene e diventino menzioni. Lascia su *automatico* |

### Unicode o scan code

**Modalità di digitazione** decide come i caratteri arrivano al gioco. *Unicode*
manda il carattere stesso e regge qualsiasi layout di tastiera e qualsiasi
alfabeto. Alcuni giochi lo ignorano perché leggono invece gli scan code
dell'hardware: per quelli passa a *scancode*, che scrive come se i tasti fossero
stati premuti fisicamente.

Gli scan code sono limitati a ciò che una tastiera statunitense può produrre,
quindi i caratteri accentati e gli alfabeti non latini non sopravvivono. Prova
prima unicode; l'impostazione esiste perché «il gioco ignora quel che scriviamo»
doveva essere un cambio di configurazione e non di codice.

I due hanno anche tempi diversi, ed è per questo che sono modalità separate. I
tasti in scancode sono tenuti `key_hold_ms` perché i giochi leggono l'input una
volta per fotogramma. Il testo digitato no: passa dalla coda dei messaggi, e
40 ms a carattere farebbero durare otto secondi un messaggio di 200 caratteri.

## Nomi e vocabolario

Whisper trascrive quel che sente, e i nomi dei piloti sono esattamente ciò in cui
riesce peggio. Il plugin di sessione legge chi c'è davvero nella tua sessione e
gli passa quei nomi, così «Estre» esce come «Estre» e non come «Ester».

**Vocabolario** aggiunge le tue parole sopra: nomi di sponsor, il nome di una
squadra, come si scrivono davvero i nick dei tuoi amici. Tutto ciò che ti ritrovi
a correggere vale la pena aggiungerlo.

## Non viene scritto nulla

**Guarda prima la scheda Stato.** Mostra con cosa è armato l'hook in questo
momento e quando il trigger è stato visto l'ultima volta. Se *Ultimo trigger* non
si aggiorna mai, il problema è il tasto o l'hook, non la trascrizione.

**Deve girare come amministratore.** Windows scarta l'input iniettato verso un
processo con un livello di integrità più alto di chi lo manda, e i simulatori
spesso girano elevati. La versione installata lo chiede da sola.

**Controlla che il profilo corrisponda.** La scheda Stato registra il nome
dell'eseguibile in primo piano; se non è uno dei tuoi profili, si sta usando il
profilo predefinito e i suoi tasti chat potrebbero non andare bene per quel
gioco.

**Controlla il ritardo di apertura della chat.** Messaggi che arrivano senza i
primi caratteri sono ogni volta un `pre_delay_ms` troppo basso.

**Controlla che il gioco non ignori l'unicode.** Se la chat si apre e non compare
nulla, prova la modalità *scancode*.
