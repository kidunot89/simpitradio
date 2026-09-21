# Stimme im Funk

SimPitRadio tippt, was Sie gesagt haben, in die Chatbox des Spiels. Das hier
ergänzt die andere Hälfte: Die Fahrer, gegen die Sie fahren, schicken Ihnen
auch das *Audio*, und Sie hören es.

Discord gibt es bereits, und alle sind schon in einem. Was Discord nicht kann,
ist, Sie in einen Raum mit **wer auch immer in dieser Session ist** zu stecken,
ohne das vorher zu verabreden, und die zum Schweigen zu bringen, die vier
Kilometer entfernt sind.

## Was übertragen wird

**Der Push-to-Talk-Clip, beim Loslassen. Kein Livestream.**

Der Auslösezyklus nimmt ohnehin einen Clip auf, während die Taste gehalten wird, und
übergibt ihn beim Loslassen an Whisper. Der Sprachchat verwendet genau diesen Clip
weiter: Beim Loslassen geht er an Whisper *und* an das Relay, und die Gegenstellen
spielen ihn ab. Am Aufnahmepfad ändert sich nichts.

Ein Livestream wäre eine andere Anwendung. Er braucht 20-ms-Rahmen, einen
Jitter-Puffer, einen Mixer und eine Wiedergabeuhr, alles auf dem Audiopfad, und der
Lohn ist, dass die Leute Sie 1,5 Sekunden früher hören. Der Clip ist ohnehin das, was
ein Boxenfunk ist: Sie halten den Knopf, Sie sagen etwas, es kommt an.

Die Folge, die man kennen sollte: **Ein Clip ist atomar.** Er kann nicht unterbrochen
werden, er kommt ganz oder gar nicht an, und zwei Fahrer, die gleichzeitig sprechen,
erzeugen zwei Clips, die sich anstellen, statt einander zu übertönen. An einem
Rennwochenende ist das die bessere der beiden Varianten.

## Wer es hört

Das Relay ist dumm. Es verteilt einen Clip an alle im Raum und entscheidet nicht, wer
ihn bekommen sollte, weil es das nicht kann. Es hat keine Ahnung, wo irgendwer auf
der Strecke ist, und ihm diese Information zu geben wäre schlimmer als nutzlos.

**Die Nähe wird auf der Maschine des Zuhörers entschieden.** LMUs Shared Memory führt
die Weltposition *jedes* Autos, nicht nur Ihres, also weiß jeder Client bereits genau,
wie weit jeder andere Fahrer entfernt ist. Nichts Positionsbezogenes wird jemals an das
Relay veröffentlicht, und die Funktion arbeitet selbst dann, wenn der Relay-Betreiber
feindselig ist.

**Die eigene Sicht des Zuhörers darauf, wo der Sprecher ist, gewinnt.** Ein Clip kommt
an, nachdem sein Sprecher aufgehört hat zu reden, die mitgeführte Position ist also
ein bis zwei Sekunden alt. Bei Renntempo sind das hundert Meter, und gegen einen
Radius von 200 m entscheiden hundert Meter die Antwort. Der Scoring-Block hat jedes
Auto so, wie es *jetzt* ist, und die Frage ist, wer nahe am Zielauto ist, wenn die
Nachricht abgespielt wird.

Der Clip führt die Position des Sprechers trotzdem mit, als Rückfall für jemanden, den
der Block des Zuhörers noch nicht kennt: einen Fahrer, der gerade beigetreten ist, oder
dessen Eintrag verschwunden ist. Eine veraltete Position schlägt keine.

Die lokale Sicht zu bevorzugen bedeutet auch, dass sich ein Clip nicht am Filter
vorbeireden kann. Ein Client, der behauptet, neben Ihnen zu sein, während er einen
Kilometer weit weg ist, wird dort gemessen, wo er tatsächlich ist. Das ergibt sich
schlicht daraus, die frischere Zahl zu benutzen, und ist kein Sicherheitsmechanismus.
Ein Sprecher, den niemand verorten kann, ist weiterhin hörbar, denn Stille, die
niemand erklären kann, ist der schlimmere Ausfall.

`proximity_only` beim LMU-Plugin schaltet das ein; `proximity_metres` setzt den
Radius. Aus hören Sie die ganze Session, was im Training und auf einer Einführungsrunde
genau das ist, was Sie wollen.

### Zuschauen

Nähe sollte vom Auto auf dem Bildschirm aus gemessen werden: einen Zweikampf zu
verfolgen, in dessen Mitte man ist, und dabei den Funk von vier Kilometern entfernt zu
hören, wo das eigene Auto geparkt steht, ist Nähe in keinem Sinn, den ein Zuschauer
wiedererkennen würde.

Es muss **erkannt** werden. Wer fährt, kann kein Dropdown erreichen, und wer zuschaut,
sollte es nicht müssen.

**Der Shared-Memory-Block sagt es nicht.** Drei plausible Quellen wurden gegen eine
laufende, zugeschaute Session geprüft und ausgeschlossen. Jede sieht richtig aus, und
keine ist es:

- `telemetry.playerVehicleIdx` ist das Fahrzeug des *Spielers*. Während man jemand
  anderem zusah, zeigte es weiter auf das eigene, geparkte Auto.
- `appInfo.mOptionsLocation` las durchgehend 0.
- `$rFactor2SMMP_Graphics$` wird veröffentlicht und würde sowohl eine Kameraposition
  als auch eine betrachtete Slot-ID führen, und LMU befüllt es nie. Der Puffer ist
  bis auf seinen Versionszähler vollständig null, weil das Spiel den Grafik-Callback
  nicht aufruft, aus dem das rF2-Plugin ihn füllt. Der benachbarte Extended-Block war
  im selben Moment lebendig, das ist also LMUs Entscheidung statt einer kaputten
  Installation.

**LMUs eigene HTTP-API sagt es.** `http://127.0.0.1:6397/rest/watch/standings` ist,
was die spieleigenen Overlays lesen. Jeder Eintrag führt `hasFocus`, gesetzt beim
beobachteten Auto und verschieden von `player`, das auf Ihrem eigenen bleibt. Seine
`slotID` ist dieselbe Zahl wie `mID` im Shared Memory, die beiden lassen sich also
direkt verbinden. Es gehört zum Spiel und nicht zu irgendeinem Plugin, es braucht also
keine Installation.

Mit kurzem Timeout gelesen und eine Sekunde zwischengespeichert: Das läuft auf dem
Auslösezyklus, die Antwort ist ~16 KB, und die App darf niemals auf ein Spiel
warten, das gerade lädt. **Fehlschläge werden ebenfalls zwischengespeichert.** Sonst
kostet ein geschlossenes Spiel bei jedem einzelnen Druck einen Timeout.

Jeder Fehlschlag ergibt None, und `SessionInfo.listener()` fällt dann auf das gefahrene
Auto zurück und schließlich auf None, was `audible` als hörbar liest. Stillschweigend
ein geparktes Auto als Referenz zu behalten würde die Session nach einem Ort filtern,
an den niemand schaut, und kein Zuhörer könnte das von einer kaputten Funktion
unterscheiden.

**„Nähe“ heißt auf der Strecke und sonst nirgends.** Es sind Meter zwischen zwei Autos
im Spiel, aus der Simulation gelesen, lokal berechnet. Es hat nichts damit zu tun, wo
irgendwer wohnt, und es wird kein physischer Ort gelesen, abgeleitet oder übertragen.
Das *Hosting* von Relays weiter unten spricht ebenfalls von Entfernung, im
Netzwerksinn. Das ist eine Routingfrage über Server und hat nichts damit zu tun, wen
Sie hören können.

## Welcher Raum

Die Session-ID wird abgeleitet, nie angekündigt:

    sha256("pitradio/1:{mServerPublicIP}:{mServerPort}")[:32]

Alle auf demselben Spielserver berechnen dieselbe ID, ohne dass irgendwer
veröffentlicht, welcher Server das ist. Das Relay erfährt einen Hash und sonst nichts.
Offline und Einzelspieler haben keinen Server, erzeugen also keine ID und keinen Raum,
was das korrekte Verhalten ist und kein Sonderfall.

Die Strecke steht bewusst *nicht* im Schlüssel. Sie wechselt zwischen Sessions auf
demselben Server, und ein Raum, der sich auflöst, sobald die Veranstaltung zur nächsten
Strecke zieht, ist ein schlechterer Raum.

Die Identität innerhalb eines Raums ist der Fahrername aus dem Scoring-Block.
`mSteamID` ist in der Praxis null, es gibt also nichts Besseres.

## Das Relay

**Der Code und die Konfiguration des Relays sind nicht in diesem Repository.**
SimPitRadio ist öffentlich; der Server, sein Terraform und sein Ansible sind privat,
zusammen mit dem OAuth-Client-Secret, das sie brauchen. Terraform und Ansible existieren
dort für eine Aufgabe: einen **von Racern bereitgestellten** Voice-Host reproduzierbar
aus einem sauberen Image aufzusetzen.

Die Adresse des Basis-Relays ist ebenfalls nicht in diesem Repository. Sie wird **zur
Build-Zeit** in `endpoints.py` geschrieben, ein Checkout, oder ein Fork, hat also
überhaupt keine Adresse, und der Sprachchat ist nicht verfügbar. Das ist ein
funktionierender Zustand. Er schlägt jeden Klon der Quelle, der ein Mikrofon auf
einen Server richtet, dessen Besitzer nie zugestimmt hat, ihn zu tragen.

Nichts sonst in der App darf eine Adresse fest verdrahten. Eine Stelle zum
Überschreiben, eine Stelle zum Nachsehen, wenn sie falsch ist.

    wss://<relay>/chat/{session-id}

Ein WebSocket pro Client, TLS, Clips als Binärframes mit einem kleinen Header. Das ist
das ganze Protokoll. TLS, weil ein Relay die Maschine eines Fremden ist und Audio Ihrer
Stimme sie nicht im Klartext überqueren sollte; WebSocket, weil es jedes NAT und jede
Firma-Firewall überlebt, an denen rohes UDP scheitert, und weil die Audiobandbreite für
zwanzig Racer, die gelegentlich einen Knopf drücken, nichts ist.

**Nicht buchstäblich Peer-to-Peer.** Echtes P2P braucht ICE, STUN und einen
TURN-Rückfall, und TURN ist ein Relay, der Rückfallpfad ist also ohnehin dieses Design,
erreicht nach dem Hineinziehen eines WebRTC-Stacks in einen Nuitka-Build, der bereits
mit nativen Abhängigkeiten kämpft. Das Relay ist eine kleine Kiste, und es ist ehrlich
damit, eine zu sein.

### Von der Community betriebene Hosts

Relays existieren, um *nahe bei den Sprechenden* zu sein. Ein Feld aus drei Kontinenten,
das über eine Kiste in Frankfurt geroutet wird, bezahlt bei jedem Clip zweimal den
Atlantik; ein für die Gruppe gewähltes Relay nicht. Geografie ist der ganze Grund, warum
Racer hosten können. Kosten sind es nicht, und Dezentralisierung um ihrer selbst willen
auch nicht.

Terraform macht die Maschine; Ansible installiert das Relay, die systemd-Unit und das
TLS-Zertifikat, ein Host ist also aus einem sauberen Ubuntu-Image ohne manuelle Schritte
reproduzierbar.

DigitalOcean OAuth zuerst, weil es das ist, was es heute gibt. Linode hat einen echten
OAuth-App-Flow und kann folgen. **AWS kann nicht.** Es hat kein Verbraucher-OAuth zur
Provisionierung, nur IAM-Schlüssel oder Identity Center SSO, es braucht also einen
eigenen Weg statt eines Knopfs.

#### Eines auszuwählen ist eine Gruppenentscheidung, keine persönliche

**Jeder Client in einer Session muss dasselbe Relay wählen, oder sie wählen keines.**
Sich selbst überlassen würde jeder den Host wählen, der *ihm* am nächsten ist, was für
ein transatlantisches Feld zwei Relays, zwei Räume und beide Hälften der Session
bedeutet, die in etwas sitzen, das genau wie eine funktionierende Funktion aussieht, nur
ohne irgendwen sonst darin. Das ist derselbe stille Ausfall wie ein nicht passender
Session-Schlüssel, nur auf anderem Weg erreicht.

Es gibt also einen Koordinator, am festen Basis-Host, und der entscheidet:

1. Clients betreten den Raum am konfigurierten Relay des Builds und melden ihre
   gemessene Round-Trip-Zeit zu jedem Kandidaten-Relay.
2. Der Koordinator wählt das mit dem besten schlechtesten Fall im Raum. Er minimiert
   die Latenz des *langsamsten* Racers statt des Durchschnitts, denn der Punkt ist,
   dass niemand gestrandet ist.
3. Er sagt allen, sie sollen migrieren, und sie verbinden sich dort gemeinsam neu.

Der Basis-Host ist auch das Rückfall-Relay, und das macht das Ganze bezahlbar: Der
Koordinator muss ohnehin immer laufen, also kann er ebenso gut das Audio für Sessions
tragen, die zu klein oder zu lokal sind, als dass sich ein Umzug lohnte.

#### Warum nicht alle Hosts zusammenschalten

Die naheliegende Alternative: Jeden Client mit dem Relay verbinden lassen, das *ihm* am
nächsten ist, und die Relays Clips untereinander weiterleiten lassen. Das ist ein echtes
Design, und Mumble verkettet Server so. Es ist in einer Hinsicht eleganter, weil es die
Gruppenentscheidung oben löscht. Es gibt nichts zu vereinbaren, wenn der Raum sich über
jedes Relay erstreckt, der Fehler des geteilten Raums kann also gar nicht auftreten.

Es ist hier trotzdem der falsche Handel, aus einem Grund: **Wir senden Clips, keinen
Livestream.** Ein Clip wird abgeschickt, nachdem der Sprecher aufgehört hat zu reden,
also kann niemand den Unterschied zwischen 90 ms und 250 ms Routing wahrnehmen. Dieser
Unterschied ist der größte Teil des Arguments für Geografie und das ganze Argument
dafür, zwei zusätzliche Hops zu zahlen, um es zu verbessern.

Was Bridging kostet, sind nicht Hops, sondern Zustand. Relays müssten
Raum-Mitgliedschaft austauschen, einander authentifizieren und sich gegen Schleifen und
doppelte Zustellung absichern, und ein von Racern betriebenes Relay, das diesem Gewebe
beitritt, kann Verkehr für Räume sehen, in denen es keine Mitglieder hat. Das ist ein
Projekt über verteilte Systeme, an eine Diktier-App geschraubt, im Dienst eines
Latenzbudgets, das dieses Design nicht hat.

Sollte SimPitRadio je auf Livestreaming gehen, kehrt sich das um und Bridging wird die
richtige Antwort. Die Form, die man dann bauen sollte: ein volles Mesh mit einem
gemeinsamen Geheimnis, per Gossip verteilte Raum-Mitgliedschaft und jeder Clip mit einer
ID und einer Grenze von **einem Hop** zwischen Relays. Kein transitives Weiterleiten,
was Routing-Schleifen sofort abtötet und den Fan-out begrenzt, statt ihm zu vertrauen.

#### Wenn ein Host verschwindet

Ein verschwindendes Relay darf das Gespräch nicht beenden. Der Koordinator hält den Raum,
merkt, dass das Relay nicht mehr antwortet, führt die Wahl über das Verbleibende erneut
aus und migriert die verbliebenen Racer. Das ist derselbe Mechanismus wie bei der ersten
Wahl, es gibt also keinen separaten Failover-Pfad, den man falsch machen könnte. Genau
deshalb halten Clients die Verbindung zum Koordinator offen: Sie ist das, was überlebt.

Ein Racer, der die Session verlässt, nimmt sein Relay nicht mitten im Rennen mit. Seine
Maschine ist nicht das Relay; ein von ihm provisionierter Droplet ist es. Es den noch auf
der Strecke Fahrenden unter den Füßen wegzuziehen wäre der denkbar schlechteste Moment
dafür.

#### Wenn die Session endet

Räume werden abgebaut, nicht weiterlaufen gelassen. LMU meldet seine Spielphase, ein
Client, der das Ende der Session sieht, sagt es also; wenn der letzte Client geht oder
der Raum über einen Leerlauf-Timeout hinaus still bleibt, schließt der Koordinator ihn.
Ein Relay ohne verbleibende Räume ist ein Kandidat für `terraform destroy`, und das ist
der Unterschied, ob das einen Racer ein paar Cent pro Event kostet oder für immer einen
Droplet.

Der Leerlauf-Timeout zählt genauso viel wie das ausdrückliche Signal. Ein Client, der
abstürzt, ins Nichts alt-tabbt oder sein Netz verliert, sendet nie etwas, nichts darf
also davon abhängen, dass er es tut.

## Einwilligung

Der Sprachchat ist **aus, bis er eingeschaltet wird**, und der Reiter Stimme sagt, wer
Sie hören kann, bevor irgendetwas anderes gesagt wird. Eine App, die still das Mikrofon
für zwanzig Fremde öffnet, wäre ein Vertrauensbruch, wie gut die Funktion auch sein mag.

Nur Push-to-Talk. Es gibt keinen Modus mit offenem Mikrofon, und es sollte auch keinen
geben: Der Auslöser ist die Einwilligung.
