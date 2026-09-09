# La voce alla radio

SimPitRadio scrive quello che hai detto nella chat del gioco. Questo aggiunge l'altra
metà: le persone contro cui corri ti mandano anche l'*audio*, e tu lo senti.

Volutamente non è Discord. Discord esiste già, funziona, e tutti sono già dentro a
uno. Quello che Discord non sa fare è metterti in una stanza con **chiunque sia in
questa sessione**, senza averlo organizzato prima, e zittire quelli che sono a quattro
chilometri.

## Cosa viaggia

**La clip del push-to-talk, al rilascio. Non uno streaming dal vivo.**

Il ciclo del trigger registra già una clip mentre il tasto è premuto e la consegna a
Whisper al rilascio. La voce riusa esattamente quella clip: al rilascio va a Whisper *e*
al relay, e i peer la riproducono. Nulla del percorso di registrazione cambia.

Uno streaming dal vivo sarebbe un'altra applicazione. Richiede frame da 20 ms, un
buffer di jitter, un mixer e un clock di riproduzione, tutto sul percorso audio, e il
premio è che la gente ti sente 1,5 secondi prima. La clip è comunque ciò che una radio
di box è: tieni il pulsante, dici una cosa, arriva.

La conseguenza che vale la pena conoscere: **una clip è atomica.** Non può essere
interrotta, arriva intera o non arriva, e due persone che parlano insieme producono due
clip che si mettono in coda invece di sovrapporsi. Questo è meglio di una gara, non
peggio.

## Chi la sente

Il relay è stupido. Distribuisce una clip a tutti nella stanza e non decide chi debba
riceverla, perché non può: non ha idea di dove sia chiunque in pista, e dargli quella
informazione sarebbe peggio che inutile.

**La prossimità è decisa sulla macchina di chi ascolta.** La memoria condivisa di LMU
porta la posizione nel mondo di *ogni* auto, non solo della tua, quindi ogni client sa
già esattamente quanto è lontano ogni altro pilota. Nulla di posizionale viene mai
pubblicato al relay, e la funzione lavora anche se chi gestisce il relay è ostile.

**Vince la visione che chi ascolta ha di dove si trovi chi parla.** Una clip arriva dopo
che chi parlava ha smesso, quindi la posizione che porta ha un secondo o due — a
velocità di gara cento metri, che contro un raggio di 200 m decide la risposta. Il blocco
di classifica ha ogni auto com'è *adesso*, e la domanda è chi è vicino all'auto bersaglio
quando il messaggio viene riprodotto.

La clip porta comunque la posizione di chi parla, come ripiego per qualcuno che il blocco
di chi ascolta non ha ancora recuperato: un pilota appena entrato, o la cui voce è
sparita. Una posizione vecchia batte nessuna posizione.

Preferire la vista locale significa anche che una clip non può parlare per superare il
filtro. Un client che sostiene di essere accanto a te mentre è a un chilometro viene
semplicemente misurato dov'è davvero. È una conseguenza dell'usare il numero più fresco,
non un meccanismo di sicurezza: chi non si riesce a collocare affatto resta comunque
udibile, perché un silenzio che nessuno sa spiegare è il guasto peggiore.

`proximity_only` sul plugin di LMU lo attiva; `proximity_metres` imposta il raggio.
Spento senti tutta la sessione, che è ciò che vuoi nelle prove e nel giro di
formazione.

### Spettatore

La prossimità andrebbe misurata dall'auto sullo schermo: seguire una lotta in mezzo alla
quale sei, sentendo intanto la radio da quattro chilometri più in là dove la tua auto è
parcheggiata, non è prossimità in nessun senso che uno spettatore riconoscerebbe.

Deve essere **rilevata**. Chi sta correndo non può raggiungere un menu a tendina, e chi
guarda non dovrebbe doverlo fare.

**Il blocco di memoria condivisa non lo dice**, e tre fonti plausibili sono state
verificate contro una sessione realmente osservata e scartate: ognuna sembra quella
giusta, e nessuna lo è.

- `telemetry.playerVehicleIdx` è il veicolo del *giocatore*. Mentre si guardava qualcun
  altro, restava puntato sull'auto parcheggiata di chi guardava.
- `appInfo.mOptionsLocation` ha letto 0 per tutto il tempo.
- `$rFactor2SMMP_Graphics$` viene pubblicato e porterebbe sia una posizione di camera sia
  l'id dello slot osservato — ma LMU non lo popola mai. Il buffer è interamente a zero a
  parte il contatore di versione, perché il gioco non chiama la callback grafica da cui
  il plugin rF2 lo riempie. Il blocco Extended vicino era vivo nello stesso momento,
  quindi è una scelta di LMU e non un'installazione rotta.

**L'API HTTP di LMU invece lo dice.** `http://127.0.0.1:6397/rest/watch/standings` è ciò
che leggono gli overlay del gioco stesso, e ogni voce porta `hasFocus` — impostato
sull'auto osservata, distinto da `player`, che resta sulla tua. Il suo `slotID` è lo
stesso numero di `mID` in memoria condivisa, quindi i due si uniscono direttamente. Fa
parte del gioco e non di un plugin, quindi non richiede alcuna installazione.

Letto con un timeout breve e messo in cache per un secondo: gira sul ciclo del trigger,
la risposta è ~16 KB, e un'app di dettatura non deve mai aspettare un gioco che sta
caricando. **Anche i fallimenti vanno in cache**, altrimenti un gioco chiuso costa un
timeout a ogni singola pressione.

Ogni fallimento dà None, e `SessionInfo.listener()` ripiega allora sull'auto guidata e
infine su None, che `audible` legge come udibile. Tenere in silenzio un'auto parcheggiata
come riferimento filtrerebbe la sessione secondo un punto che nessuno sta guardando, e
nessun ascoltatore potrebbe distinguerlo da una funzione rotta.

**«Prossimità» significa in pista e da nessun'altra parte.** Sono metri fra due auto nel
gioco, letti dal simulatore, calcolati localmente. Non ha nulla a che vedere con dove
abita qualcuno, e nessuna posizione fisica viene letta, dedotta o trasmessa. L'*hosting*
dei relay più sotto parla anch'esso di distanza, in senso di rete: è una questione di
instradamento fra server e non ha relazione con chi puoi sentire.

## Quale stanza

L'id di sessione è derivato, mai annunciato:

    sha256("pitradio/1:{mServerPublicIP}:{mServerPort}")[:32]

Tutti sullo stesso server di gioco calcolano lo stesso id senza che nessuno pubblichi
quale server sia: il relay impara un hash e nient'altro. Offline e giocatore singolo non
hanno server, quindi non producono né id né stanza, che è il comportamento corretto e non
un caso speciale.

Il tracciato è deliberatamente *fuori* dalla chiave. Cambia fra sessioni sullo stesso
server, e una stanza che si dissolve quando l'evento passa al tracciato successivo è una
stanza peggiore.

L'identità dentro una stanza è il nome del pilota dal blocco di classifica. `mSteamID` in
pratica è zero, quindi non c'è nulla di meglio a disposizione.

## Il relay

**Il codice e la configurazione del relay non sono in questo repository.** SimPitRadio è
pubblico; il server, il suo Terraform e il suo Ansible sono privati, insieme al client
secret OAuth di cui hanno bisogno. Terraform e Ansible esistono là per un lavoro: tirare
su in modo riproducibile, da un'immagine pulita, un host vocale **fornito da un pilota**.

Nemmeno l'indirizzo del relay di base è in questo repository. Viene scritto in
[endpoints.py](../src/pitradio/endpoints.py) **in fase di build**, quindi un checkout —
o un fork — non ha alcun indirizzo e la voce semplicemente non è disponibile. È uno stato
funzionante, non uno rotto: meglio che ogni clone dei sorgenti punti un microfono su un
server il cui proprietario non ha mai accettato di reggerlo.

Nient'altro nell'app può inserire un indirizzo fisso nel codice. Un posto da
sovrascrivere, un posto dove guardare quando è sbagliato.

    wss://<relay>/chat/{id-sessione}

Un WebSocket per client, TLS, clip come frame binari con una piccola intestazione. È
tutto il protocollo. TLS perché un relay è la macchina di uno sconosciuto e l'audio della
tua voce non dovrebbe attraversarla in chiaro; WebSocket perché sopravvive a ogni NAT e
firewall aziendale a cui l'UDP grezzo non sopravvive, e la banda audio di venti piloti che
premono un pulsante ogni tanto è nulla.

**Non letteralmente peer-to-peer.** Il vero P2P richiede ICE, STUN e un ripiego TURN — e
TURN è un relay, quindi il percorso di ripiego è comunque questo progetto, raggiunto dopo
aver trascinato uno stack WebRTC dentro una build Nuitka che già combatte con dipendenze
native. Il relay è una scatoletta, ed è onesto sull'esserlo.

### Host della comunità

I relay esistono per stare *vicino a chi parla*. Una griglia presa da tre continenti e
instradata attraverso una scatola a Francoforte paga l'Atlantico due volte su ogni clip;
un relay scelto per il gruppo no. È tutta qui la ragione per cui i piloti possono fare da
host: non il costo, e non la decentralizzazione fine a sé stessa — la geografia.

Terraform fa la macchina; Ansible installa il relay, l'unità systemd e il certificato TLS,
così un host è riproducibile da un'immagine Ubuntu pulita senza passaggi manuali.

Prima OAuth di DigitalOcean, perché è ciò che esiste oggi. Linode ha un vero flusso di app
OAuth e può seguire. **AWS non può**: non ha un OAuth consumer per il provisioning — sono
chiavi IAM o SSO di Identity Center — quindi ha bisogno di un percorso suo e non è una
questione di aggiungere un pulsante.

#### Sceglierne uno è una decisione di gruppo, non personale

**Ogni client in una sessione deve scegliere lo stesso relay, o non ne scelgono nessuno.**
Lasciati a sé, ciascuno sceglierebbe l'host più vicino a *sé*, il che per una griglia
transatlantica significa due relay, due stanze e le due metà della sessione sedute in
qualcosa che sembra esattamente una funzione che va, senza nessun altro dentro. È lo
stesso guasto silenzioso di una chiave di sessione che non combacia, raggiunto per
un'altra strada.

Quindi c'è un coordinatore, sull'host di base fisso, e decide:

1. I client entrano nella stanza sul relay configurato nella build e riferiscono il
   round-trip misurato verso ogni relay candidato.
2. Il coordinatore sceglie quello col miglior caso peggiore su tutta la stanza:
   minimizza la latenza del pilota *più lento*, non la media, perché il punto è che
   nessuno resti isolato.
3. Dice a tutti di migrare, e si riconnettono là insieme.

L'host di base è anche il relay di ripiego, ed è ciò che rende la cosa sostenibile: il
coordinatore deve comunque essere sempre acceso, tanto vale che porti l'audio delle
sessioni troppo piccole o troppo locali perché valga la pena spostarle.

#### Perché non collegare tutti gli host fra loro

L'alternativa ovvia: lasciare che ogni client si connetta al relay più vicino a *lui*, e
fare in modo che i relay si inoltrino le clip a vicenda. È un progetto vero — Mumble
collega i server così — ed è genuinamente più elegante sotto un aspetto, perché cancella
la decisione di gruppo qui sopra. Non c'è nulla su cui accordarsi se la stanza copre tutti
i relay, quindi il guasto della stanza divisa non può proprio verificarsi.

Resta comunque lo scambio sbagliato qui, per un motivo: **mandiamo clip, non uno streaming
dal vivo.** Una clip viene spedita dopo che chi parla ha finito, quindi la differenza fra
90 ms e 250 ms di instradamento non è qualcosa che qualcuno possa percepire — ed è la
maggior parte dell'argomento a favore della geografia, e tutto l'argomento per pagare due
salti in più per migliorarla.

Quello che costa il bridging non sono i salti, è lo stato. I relay dovrebbero scambiarsi
l'appartenenza alle stanze, autenticarsi a vicenda e guardarsi da cicli e consegne
duplicate, e un relay ospitato da un pilota che entra in quel tessuto può vedere traffico
di stanze in cui non ha membri. È un progetto di sistemi distribuiti avvitato al fianco di
un'app di dettatura, al servizio di un budget di latenza che questo progetto non ha.

Se SimPitRadio passasse mai allo streaming dal vivo, questo si ribalta e il bridging
diventa la risposta giusta. La forma da costruire allora: una maglia completa con un
segreto condiviso, l'appartenenza alle stanze diffusa per gossip, e ogni clip che porta un
id con un limite di **un salto** fra relay — nessun inoltro transitivo, il che uccide sul
nascere i cicli di instradamento e limita il fan-out invece di fidarsene.

#### Quando un host sparisce

Un relay che sparisce non deve chiudere la conversazione. Il coordinatore tiene la stanza,
si accorge che il relay non risponde più, rifà la scelta su ciò che resta e migra i piloti
rimasti — lo stesso meccanismo della scelta iniziale, quindi non c'è un percorso di
failover separato da sbagliare. I client tengono aperta la connessione al coordinatore
esattamente per questo: è la cosa che sopravvive.

Un pilota che lascia la sessione non si porta via il suo relay a metà gara. La sua macchina
non è il relay — lo è un droplet che ha provvisto — e sfilarlo da sotto i piedi di chi sta
ancora guidando sarebbe il momento peggiore possibile.

#### Quando la sessione finisce

Le stanze vengono smontate, non lasciate in funzione. LMU riporta la sua fase di gioco,
quindi un client che vede la sessione finire lo dice; quando l'ultimo client se ne va, o la
stanza resta in silenzio oltre un timeout di inattività, il coordinatore la chiude. Un
relay senza stanze rimaste è candidato a `terraform destroy`, ed è la differenza fra questa
cosa che costa a un pilota qualche centesimo a evento e che gli costa un droplet per
sempre.

Il timeout di inattività conta quanto il segnale esplicito. Un client che va in crash, fa
alt-tab nel nulla o perde la rete non manda mai niente — quindi nulla può dipendere dal
fatto che lo faccia.

## Consenso

La voce è **spenta finché non la accendi**, per profilo, e la finestra dice chi può
sentirti prima di dire qualsiasi altra cosa. Un'app di dettatura che aprisse in silenzio il
microfono a venti sconosciuti sarebbe un tradimento, per quanto buona sia la funzione.

Solo push-to-talk. Non c'è una modalità a microfono aperto e non dovrebbe esserci: il tasto
è il consenso.
