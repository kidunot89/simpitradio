# Per iniziare

Installalo, digli quale tasto ascoltare e di' qualcosa. Tutto il resto in
queste pagine è facoltativo.

![La finestra di SimPitRadio sulla scheda Stato](images/window.png)

## Installazione

Scarica l'installer dalla
[pagina delle versioni](https://github.com/kidunot89/simpitradio/releases/latest)
ed eseguilo. Windows ti avviserà: le build non sono firmate, quindi SmartScreen
mostra «Windows ha protetto il PC» e devi scegliere **Ulteriori informazioni →
Esegui comunque**. Un installer non firmato è fatto così, e firmare costa
denaro che questo progetto non spende.

L'installazione fa una sola domanda. **Quale lingua**, con quella di Windows
già scelta. Fissa tre cose insieme: la finestra, il modello vocale e la lingua
in cui l'ingegnere parla e ascolta. La scheda Lingua la cambia più tardi.

**Si installa come amministratore, di proposito.** Windows scarta le pressioni
di tasto iniettate verso un programma che gira con più privilegi di chi le
manda, e i simulatori spesso girano elevati. Senza questo tutto sembra
funzionare e al gioco non arriva mai nulla.

### Al primo avvio scarica due cose

Nell'installer non viaggia nulla di grosso, quindi la prima volta che lo apri
ti viene chiesto di scaricare:

- **il modello vocale**, circa 250 MB, che è ciò che trasforma la tua voce in
  testo
- **un pacchetto vocale** per l'ingegnere, circa 45 MB, dove ne esiste uno
  pubblicato nella tua lingua

Entrambi una volta sola. Il modello vive fuori dalla cartella di
installazione, così un aggiornamento non lo fa ripagare mai. Di' «non ora» e
le schede Lingua e Impostazioni li scaricano quando vuoi.

La build portatile non ha installer e nessuna domanda sulla lingua, quindi la
pone al primo avvio.

## Scegli un tasto

**Impostazioni → Attivazione.** Premi *Premi un tasto…* e poi quello che vuoi.

![La sezione Attivazione della scheda Impostazioni](images/trigger.png)

Il tasto viene **inghiottito al passaggio**, quindi il gioco non lo vede mai.
Assegnane uno che il gioco già usa e non si rompe nulla. `F13` è il valore
predefinito perché la maggior parte delle tastiere non ce l'ha e nient'altro
lo sta ascoltando.

**Va bene anche un pulsante del volante.** Nella riga **Pulsante del
volante**, premi *Premi un pulsante…* e premi quello che vuoi. SimPitRadio
apre il volante senza toglierlo al gioco, quindi il simulatore continua a
leggere ogni pulsante, compreso quello. Tienilo premuto per parlare esattamente
come faresti col tasto. Restano armati entrambi insieme, così puoi assegnarli
tutti e due e usare quello più vicino.

L'altra strada è il software del tuo stesso volante, oppure
[JoyToKey](https://joytokey.net/): metti `F13` su un pulsante e assegna `F13`
qui. Prendi questa via se il volante fa già girare un software di cui ti fidi,
o se SimPitRadio non riesce ad aprire il dispositivo.

## Imposta il microfono

**Audio → Microfono.** Scegli l'ingresso, tieni premuto il tasto di
attivazione e guarda la barra del livello. Mostra il segnale *dopo* il
guadagno, cioè quello che il modello vocale riceve davvero. Punta a un picco
intorno a tre quarti.

![La scheda Audio](images/audio.png)

**L'uscita non dovrebbe essere il dispositivo del simulatore.** L'ingegnere,
il coach e il bip di registrazione suonano tutti qui, e puntarla sulla stessa
uscita del gioco mette il bip dentro la registrazione.

Premi **Registra 4 s e trascrivi** per sentire che cosa ha capito. Durante una
prova non viene scritto nulla da nessuna parte.

## Di' qualcosa

Tieni premuto il tasto di attivazione, dillo, rilascia.

1. Il tasto viene inghiottito.
2. La registrazione parte **subito**, prima che si apra la chat. Nulla di
   quanto detto nelle prime centinaia di millisecondi va perso.
3. I tasti della chat aprono la chat del gioco.
4. Al rilascio la clip va al modello vocale, sulla tua CPU.
5. Il testo viene digitato e i tasti di invio vengono premuti.

La scheda Stato mostra con cosa è armato l'hook e quando è stato visto l'ultimo
comando. Se *Ultimo comando* non si aggiorna mai, il problema è il tasto o
l'hook, non la trascrizione.

![La scheda Stato](images/status.png)

## Poi, se vuoi di più

L'ingegnere, il coach e la chat vocale sono tutti spenti finché non li
accendi.

| | |
| --- | --- |
| [Chat di testo](text-chat.md) | La dettatura vera e propria: profili, revisione prima dell'invio, cosa fare quando non viene scritto nulla |
| [L'ingegnere](engineer.md) | Una voce con un nome che legge i tuoi tempi sul giro, segnala le auto affiancate e risponde alle domande |
| [Il coach](coaching.md) | La tua traiettoria contro quella di un rivale dopo ogni curva, con cosa cambiare |
| [Voce alla radio](voice-chat.md) | Sentire gli altri piloti della tua sessione, e solo quelli vicini |
| [Pacchetti vocali](voicepacks.md) | Registrare o installare la voce con cui parla l'ingegnere |

## Quando qualcosa non va

**Guarda prima la scheda Stato.** È l'unico posto che mostra ciò che l'app
crede: il tasto armato, l'eseguibile in primo piano, il profilo in uso e un
log dal vivo.

![Il log sulla scheda Stato](images/log.png)

- **Non viene scritto nulla.** Vedi [Non viene scritto nulla](text-chat.md#non-viene-scritto-nulla).
- **Non viene detto nulla.** Vedi [Non viene detto nulla](engineer.md#non-viene-detto-nulla).
- **Non viene disegnato nulla.** Vedi [Non viene disegnato nulla](coaching.md#non-viene-disegnato-nulla).

Il log viene scritto anche su file. **Stato → Apri cartella dei log** ti ci
porta, ed è la prima cosa che vale la pena allegare a una segnalazione.
