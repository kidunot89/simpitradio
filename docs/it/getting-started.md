# Per iniziare

Installalo, digli quale tasto ascoltare e parla. Tutto il resto in queste pagine
è facoltativo.

![La finestra di SimPitRadio sulla scheda Stato](images/window.png)

## Installazione

Scarica l'installer dalla
[pagina delle versioni](https://github.com/kidunot89/simpitradio/releases/latest) ed
eseguilo. Windows ti avviserà: le build non sono firmate, quindi SmartScreen
mostra «Windows ha protetto il PC» e devi scegliere **Ulteriori informazioni →
Esegui comunque**. Un installer non firmato è fatto così, e firmare costa denaro
che questo progetto non spende.

L'installazione fa una sola domanda — **quale lingua** — con quella di Windows
già selezionata. Questo fissa tre cose insieme: la finestra, il riconoscimento
vocale e la lingua in cui l'ingegnere di pista parla e ascolta. Puoi cambiarla
più tardi nella scheda Lingua.

**Si installa come amministratore, di proposito.** Windows scarta le pressioni
di tasto iniettate verso un programma che gira con più privilegi di chi le
manda, e i simulatori spesso girano elevati. Senza questo sembra tutto
funzionante e al gioco non arriva mai nulla.

### Al primo avvio scarica due cose

Nell'installer non viaggia nulla di grosso, quindi la prima volta che lo apri ti
viene chiesto di scaricare:

- **il modello vocale**, circa 250 MB, che è ciò che trasforma la tua voce in
  testo
- **una voce registrata** per l'ingegnere, circa 45 MB, se ne esiste una
  pubblicata nella tua lingua

Entrambe una volta sola. Il modello vive fuori dalla cartella di installazione,
così un aggiornamento non lo fa ripagare mai. Se dici «non ora», le schede
Lingua e Impostazioni fanno lo stesso lavoro quando vuoi.

Lo zip portabile non ha installer e quindi nemmeno la domanda sulla lingua: la
pone al primo avvio.

## Scegli un tasto

**Impostazioni → Trigger.** Premi *Premi un tasto…* e poi quello che vuoi.

![La sezione Trigger della scheda Impostazioni](images/trigger.png)

Il tasto viene **inghiottito al passaggio**, quindi il gioco non lo vede mai — il
che significa che puoi usarne uno che il gioco già impiega. `F13` è il valore
predefinito perché la maggior parte delle tastiere non ce l'ha e nient'altro lo
sta ascoltando.

**Un pulsante del volante va bene.** Mappalo su un tasto della tastiera con
[JoyToKey](https://joytokey.net/) e assegna qui quel tasto. SimPitRadio non
legge i volanti direttamente, e il motivo è nelle
[note dell'ingegnere](engineer.md#impostazioni-per-simulatore): una corona Fanatec ha
enumerato 79 ingressi senza mai segnalare una pressione attraverso nessuna di
quattro librerie diverse, e leggere un Steam Controller significava toglierlo a
Steam.

## Imposta il microfono

**Audio → Microfono.** Scegli l'ingresso, tieni premuto il trigger e guarda la
barra del livello: mostra il segnale *dopo* il guadagno, cioè quello che Whisper
riceve davvero. Punta a picchi intorno a tre quarti.

![La scheda Audio](images/audio.png)

**L'uscita non dovrebbe essere il dispositivo del simulatore.** L'ingegnere, il
coach e il segnale di registrazione suonano tutti qui; puntarla sulla stessa
uscita del gioco mette il bip dentro la registrazione.

Premi **Registra 4 s e trascrivi** per sentire che cosa ha capito. Durante una
prova non viene scritto nulla da nessuna parte.

## Di' qualcosa

Tieni premuto il tasto, di' quello che vuoi dire, rilascia.

1. Il tasto viene inghiottito.
2. La registrazione parte **subito** — prima che si apra la chat, così non si
   perde nulla delle prime centinaia di millisecondi.
3. I tasti della chat aprono la chat del gioco.
4. Al rilascio la clip va a Whisper, sulla tua CPU.
5. Il testo viene digitato e i tasti di invio vengono premuti.

La scheda Stato mostra con cosa è armato l'hook e quando il trigger è stato visto
l'ultima volta. Se *Ultimo trigger* non si aggiorna mai, il problema è il tasto o
l'hook, non la trascrizione.

![La scheda Stato](images/status.png)

## Poi, se vuoi di più

Nulla di quanto segue è attivo per impostazione predefinita.

| | |
| --- | --- |
| [Chat testuale](text-chat.md) | La dettatura vera e propria: profili, revisione prima dell'invio, cosa fare quando non viene scritto nulla |
| [L'ingegnere](engineer.md) | Una voce con un nome che legge i tuoi tempi sul giro, segnala le auto affiancate e risponde alle domande |
| [Il coach](coaching.md) | La tua traiettoria contro quella di un rivale dopo ogni curva, con cosa cambiare |
| [Voce alla radio](voice-chat.md) | Sentire gli altri piloti della sessione, e solo quelli vicini |
| [Pacchetti voce](voicepacks.md) | Registrare o installare la voce con cui parla l'ingegnere |

## Quando qualcosa non va

**Guarda prima la scheda Stato.** È l'unico posto che mostra ciò che l'app
crede: il tasto armato, l'eseguibile in primo piano, il profilo in uso e un log
dal vivo.

![Il log sulla scheda Stato](images/log.png)

- **Non viene scritto nulla** — vedi [Non viene scritto nulla](text-chat.md#non-viene-scritto-nulla).
- **Non viene detto nulla** — vedi [Non viene detto nulla](engineer.md#non-viene-detto-nulla).
- **Non viene disegnato nulla** — vedi [Non viene disegnato nulla](coaching.md#non-viene-disegnato-nulla).

Il log viene scritto anche su file. **Stato → Apri cartella dei log** ti ci
porta, ed è la prima cosa che vale la pena allegare a una segnalazione.
