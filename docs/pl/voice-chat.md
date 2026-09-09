# Głos na radiu

SimPitRadio wpisuje to, co powiedziałeś, w okno czatu gry. To dokłada drugą połowę:
ludzie, z którymi się ścigasz, przysyłają Ci też *dźwięk*, a Ty go słyszysz.

Celowo nie jest to Discord. Discord już istnieje, działa, i wszyscy już na jakimś są.
Czego Discord nie potrafi, to wsadzić Cię do pokoju z **kimkolwiek jest w tej sesji**,
bez wcześniejszego umawiania, i uciszyć tych, którzy są cztery kilometry dalej.

## Co podróżuje

**Klip z push-to-talk, przy puszczeniu. Nie strumień na żywo.**

Cykl wyzwalacza i tak nagrywa klip, gdy klawisz jest trzymany, i przy puszczeniu podaje go
Whisperowi. Głos używa dokładnie tego klipu: przy puszczeniu trafia on do Whispera *i* do
przekaźnika, a odbiorcy go odtwarzają. Nic w ścieżce nagrywania się nie zmienia.

Strumień na żywo byłby inną aplikacją. Wymaga ramek 20 ms, bufora jittera, miksera i
zegara odtwarzania, wszystkiego na ścieżce dźwięku, a nagrodą jest to, że ludzie słyszą Cię
1,5 sekundy wcześniej. Klip i tak jest tym, czym jest radio z boksu: trzymasz przycisk,
mówisz coś, dociera.

Konsekwencja warta poznania: **klip jest niepodzielny.** Nie da się go przerwać, dociera
w całości albo wcale, a dwie osoby mówiące naraz tworzą dwa klipy, które ustawiają się w
kolejce, zamiast się przekrzykiwać. To lepsze niż wyścig, nie gorsze.

## Kto to słyszy

Przekaźnik jest głupi. Rozsyła klip do wszystkich w pokoju i nie decyduje, kto powinien go
dostać, bo nie może — nie ma pojęcia, gdzie ktokolwiek jest na torze, a danie mu tej
informacji byłoby gorsze niż bezużyteczne.

**Bliskość rozstrzyga się na maszynie słuchacza.** Pamięć współdzielona LMU niesie pozycję
w świecie *każdego* auta, nie tylko Twojego, więc każdy klient już dokładnie wie, jak
daleko jest każdy inny kierowca. Nic pozycyjnego nigdy nie jest publikowane do
przekaźnika, a funkcja działa nawet wtedy, gdy operator przekaźnika jest wrogi.

**Wygrywa własny obraz słuchacza o tym, gdzie jest mówiący.** Klip dociera po tym, jak
mówiący przestał mówić, więc pozycja, którą niesie, ma sekundę czy dwie — przy prędkości
wyścigowej sto metrów, co wobec promienia 200 m rozstrzyga odpowiedź. Blok klasyfikacji ma
każde auto takie, jakie jest *teraz*, a pytanie brzmi, kto jest blisko auta docelowego,
kiedy wiadomość się odtwarza.

Klip i tak niesie pozycję mówiącego, jako zapas dla kogoś, kogo blok słuchacza jeszcze nie
dogonił: kierowcy, który właśnie dołączył, albo którego wpis zniknął. Nieświeża pozycja
bije brak pozycji.

Przedkładanie widoku lokalnego znaczy też, że klip nie zdoła przegadać filtra. Klient
twierdzący, że jest obok Ciebie, gdy jest kilometr dalej, jest po prostu mierzony tam,
gdzie naprawdę jest. To skutek używania świeższej liczby, a nie mechanizm bezpieczeństwa —
mówiący, którego nikt nie potrafi umiejscowić, wciąż jest słyszalny, bo cisza, której nikt
nie umie wyjaśnić, to gorsza awaria.

`proximity_only` we wtyczce LMU to włącza; `proximity_metres` ustawia promień. Wyłączone —
słyszysz całą sesję, czego właśnie chcesz na treningu i na okrążeniu formującym.

### Obserwowanie

Bliskość powinna być mierzona od auta na ekranie: śledzić walkę, w środku której jesteś,
słysząc jednocześnie radio z czterech kilometrów dalej, gdzie stoi zaparkowane Twoje auto,
to bliskość w żadnym sensie, który obserwator by rozpoznał.

To musi być **wykryte**. Ktoś, kto się ściga, nie sięgnie do listy rozwijanej, a ktoś, kto
obserwuje, nie powinien musieć.

**Blok pamięci współdzielonej tego nie mówi**, a trzy prawdopodobne źródła sprawdzono
wobec żywej, obserwowanej sesji i odrzucono — każde wygląda właściwie i żadne nim nie jest:

- `telemetry.playerVehicleIdx` to pojazd *gracza*. Podczas obserwowania kogoś innego
  wciąż wskazywał zaparkowane auto obserwującego.
- `appInfo.mOptionsLocation` przez cały czas czytało 0.
- `$rFactor2SMMP_Graphics$` jest publikowane i niosłoby zarówno pozycję kamery, jak i id
  obserwowanego slotu — ale LMU nigdy go nie wypełnia. Bufor jest w całości zerowy poza
  licznikiem wersji, bo gra nie wywołuje wywołania zwrotnego grafiki, z którego wtyczka
  rF2 go wypełnia. Sąsiedni blok Extended był w tej samej chwili żywy, więc to wybór LMU,
  a nie zepsuta instalacja.

**Własne API HTTP LMU to mówi.** `http://127.0.0.1:6397/rest/watch/standings` to to, co
czytają własne nakładki gry, a każdy wpis niesie `hasFocus` — ustawione na obserwowanym
aucie, odrębne od `player`, które zostaje na Twoim. Jego `slotID` to ta sama liczba co
`mID` w pamięci współdzielonej, więc oba łączą się wprost. Jest częścią gry, a nie
jakiejkolwiek wtyczki, więc nie wymaga niczego instalować.

Czytane z krótkim limitem czasu i buforowane na sekundę: działa to na cyklu wyzwalacza,
odpowiedź ma ~16 KB, a aplikacja do dyktowania nigdy nie może czekać na grę w trakcie
ładowania. **Niepowodzenia też są buforowane** — inaczej zamknięta gra kosztuje limit
czasu przy każdym pojedynczym naciśnięciu.

Każde niepowodzenie daje None, a `SessionInfo.listener()` cofa się wtedy do prowadzonego
auta i wreszcie do None, co `audible` czyta jako słyszalne. Ciche trzymanie zaparkowanego
auta jako odniesienia filtrowałoby sesję według miejsca, na które nikt nie patrzy, a żaden
słuchacz nie odróżniłby tego od zepsutej funkcji.

**„Bliskość” znaczy na torze i nigdzie indziej.** To metry między dwoma autami w grze,
odczytane z symulatora, policzone lokalnie. Nie ma nic wspólnego z tym, gdzie ktokolwiek
mieszka, i żadna fizyczna lokalizacja nie jest odczytywana, wyprowadzana ani przesyłana.
*Hosting* przekaźników poniżej też mówi o odległości, w sensie sieciowym — to kwestia
trasowania między serwerami i nie ma związku z tym, kogo możesz słyszeć.

## Który pokój

Id sesji jest wyprowadzane, nigdy ogłaszane:

    sha256("pitradio/1:{mServerPublicIP}:{mServerPort}")[:32]

Wszyscy na tym samym serwerze gry liczą to samo id, a nikt nie publikuje, który to serwer —
przekaźnik poznaje skrót i nic więcej. Offline i pojedynczy gracz nie mają serwera, więc nie
wytwarzają id ani pokoju, i to jest zachowanie poprawne, a nie przypadek szczególny.

Tor celowo *nie* jest w kluczu. Zmienia się między sesjami na tym samym serwerze, a pokój,
który rozpada się, gdy wydarzenie przenosi się na następny tor, jest gorszym pokojem.

Tożsamość w pokoju to nazwisko kierowcy z bloku klasyfikacji. `mSteamID` w praktyce jest
zerem, więc nie ma nic lepszego pod ręką.

## Przekaźnik

**Kodu i konfiguracji przekaźnika nie ma w tym repozytorium.** SimPitRadio jest publiczne;
serwer, jego Terraform i jego Ansible są prywatne, wraz z sekretem klienta OAuth, którego
potrzebują. Terraform i Ansible istnieją tam do jednego zadania: powtarzalnie postawić, z
czystego obrazu, host głosowy **dostarczony przez zawodnika**.

Adresu bazowego przekaźnika też nie ma w tym repozytorium. Wpisywany jest do
[endpoints.py](../src/pitradio/endpoints.py) **w czasie budowania**, więc kopia kodu — albo
fork — nie ma żadnego adresu i głos jest po prostu niedostępny. To stan działający, a nie
zepsuty: lepszy niż każdy klon źródeł kierujący mikrofon na serwer, którego właściciel nigdy
nie zgodził się go dźwigać.

Nic innego w aplikacji nie może wpisywać adresu na sztywno. Jedno miejsce do nadpisania,
jedno miejsce, gdzie zajrzeć, gdy jest zły.

    wss://<przekaźnik>/chat/{id-sesji}

Jeden WebSocket na klienta, TLS, klipy jako ramki binarne z małym nagłówkiem. To cały
protokół. TLS, bo przekaźnik to maszyna obcego, a dźwięk Twojego głosu nie powinien
przechodzić przez nią otwartym tekstem; WebSocket, bo przeżywa każdy NAT i firewall
korporacyjny, których surowy UDP nie przeżywa, a pasmo dźwięku dla dwudziestu zawodników
naciskających od czasu do czasu przycisk to nic.

**Nie dosłownie peer-to-peer.** Prawdziwe P2P potrzebuje ICE, STUN i zapasowego TURN — a
TURN jest przekaźnikiem, więc ścieżka zapasowa i tak jest tym projektem, osiągniętym po
wciągnięciu stosu WebRTC do kompilacji Nuitki, która i tak walczy z natywnymi
zależnościami. Przekaźnik to jedno małe pudełko i jest uczciwy co do tego, że nim jest.

### Hosty społeczności

Przekaźniki istnieją po to, by być *blisko mówiących*. Stawka zebrana z trzech kontynentów,
trasowana przez jedno pudełko we Frankfurcie, płaci Atlantyk dwa razy na każdym klipie;
przekaźnik wybrany dla grupy nie. To cały powód, dla którego zawodnicy mogą hostować: nie
koszt i nie decentralizacja dla niej samej — geografia.

Terraform robi maszynę; Ansible instaluje przekaźnik, jednostkę systemd i certyfikat TLS,
więc host jest powtarzalny z czystego obrazu Ubuntu bez ręcznych kroków.

Najpierw OAuth DigitalOcean, bo to jest to, co istnieje dzisiaj. Linode ma prawdziwy
przepływ aplikacji OAuth i może dołączyć. **AWS nie może**: nie ma konsumenckiego OAuth do
provisioningu — to klucze IAM albo SSO Identity Center — więc potrzebuje własnej ścieżki i
nie jest to kwestia dodania przycisku.

#### Wybór jednego to decyzja grupowa, nie osobista

**Każdy klient w sesji musi wybrać ten sam przekaźnik, albo nie wybierają żadnego.**
Pozostawieni sobie, każdy wybrałby host najbliższy *sobie*, co dla stawki transatlantyckiej
oznacza dwa przekaźniki, dwa pokoje i obie połowy sesji siedzące w czymś, co wygląda
dokładnie jak działająca funkcja, tylko bez nikogo innego w środku. To ta sama cicha awaria
co niepasujący klucz sesji, osiągnięta inną drogą.

Jest więc jeden koordynator, na stałym hoście bazowym, i on decyduje:

1. Klienci wchodzą do pokoju na skonfigurowanym w kompilacji przekaźniku i zgłaszają
   zmierzony czas w obie strony do każdego kandydata.
2. Koordynator wybiera ten o najlepszym najgorszym przypadku w całym pokoju — minimalizuje
   opóźnienie *najwolniejszego* zawodnika, a nie średnią, bo chodzi o to, żeby nikt nie
   został odcięty.
3. Mówi wszystkim, żeby migrowali, i łączą się tam razem.

Host bazowy jest też przekaźnikiem zapasowym, i to czyni całość opłacalną: koordynator i
tak musi być zawsze włączony, więc równie dobrze może nieść dźwięk sesji zbyt małych albo
zbyt lokalnych, żeby warto je było przenosić.

#### Dlaczego nie połączyć wszystkich hostów ze sobą

Oczywista alternatywa: pozwolić każdemu klientowi łączyć się z przekaźnikiem najbliższym
*jemu*, a przekaźnikom przekazywać klipy między sobą. To prawdziwy projekt — Mumble tak
łączy serwery — i pod jednym względem jest naprawdę bardziej elegancki, bo kasuje powyższą
decyzję grupową. Nie ma czego uzgadniać, jeśli pokój rozciąga się na wszystkie przekaźniki,
więc awaria rozdzielonego pokoju w ogóle nie może wystąpić.

To i tak zła wymiana tutaj, z jednego powodu: **wysyłamy klipy, nie strumień na żywo.**
Klip jest wysyłany po tym, jak mówiący skończył, więc różnica między 90 ms a 250 ms
trasowania nie jest czymś, co ktokolwiek potrafi zauważyć — a to większość argumentu za
geografią i cały argument za płaceniem dwóch dodatkowych przeskoków, żeby ją poprawić.

Mostkowanie kosztuje nie przeskoki, lecz stan. Przekaźniki musiałyby wymieniać między sobą
skład pokoi, uwierzytelniać się nawzajem i strzec przed pętlami i podwójnym dostarczeniem, a
przekaźnik hostowany przez zawodnika, wchodząc w tę tkaninę, widzi ruch pokoi, w których nie
ma członków. To projekt z systemów rozproszonych przykręcony z boku do aplikacji do
dyktowania, w służbie budżetu opóźnień, którego ten projekt nie ma.

Jeśli SimPitRadio kiedyś przejdzie na strumień na żywo, to się odwraca i mostkowanie staje
się właściwą odpowiedzią. Kształt, który wtedy zbudować: pełna siatka ze wspólnym sekretem,
skład pokoi roznoszony plotką i każdy klip niosący id z limitem **jednego przeskoku** między
przekaźnikami — bez przekazywania przechodniego, co zabija pętle trasowania na wstępie i
ogranicza rozejście się zamiast mu ufać.

#### Kiedy host znika

Znikający przekaźnik nie może zakończyć rozmowy. Koordynator trzyma pokój, zauważa, że
przekaźnik przestał odpowiadać, ponownie przeprowadza wybór po tym, co zostało, i migruje
pozostałych zawodników — ten sam mechanizm co wybór początkowy, więc nie ma osobnej ścieżki
awaryjnej, którą można by pomylić. Klienci trzymają połączenie z koordynatorem otwarte
właśnie po to: to ono przeżywa.

Zawodnik opuszczający sesję nie zabiera swojego przekaźnika w środku wyścigu. Jego maszyna
nie jest przekaźnikiem — jest nim droplet, który postawił — a wyciągnięcie go spod nóg tym,
którzy jeszcze jadą, byłoby najgorszym możliwym momentem.

#### Kiedy sesja się kończy

Pokoje są rozbierane, nie zostawiane na chodzie. LMU zgłasza swoją fazę gry, więc klient,
który widzi koniec sesji, mówi o tym; gdy ostatni klient wychodzi albo pokój milczy ponad
limit bezczynności, koordynator go zamyka. Przekaźnik bez pozostałych pokoi jest kandydatem
do `terraform destroy`, i to jest różnica między tym, czy kosztuje to zawodnika kilka groszy
na wydarzenie, czy droplet na zawsze.

Limit bezczynności liczy się tak samo jak jawny sygnał. Klient, który się wysypie, przełączy
się w niebyt albo straci sieć, nigdy nic nie wyśle — więc nic nie może zależeć od tego, że
to zrobi.

## Zgoda

Głos jest **wyłączony, dopóki się go nie włączy**, na profil, a okno mówi, kto może Cię
usłyszeć, zanim powie cokolwiek innego. Aplikacja do dyktowania, która po cichu otworzyłaby
mikrofon dla dwudziestu obcych, byłaby zdradą, choćby funkcja była nie wiadomo jak dobra.

Tylko push-to-talk. Nie ma trybu otwartego mikrofonu i nie powinno być: klawisz jest zgodą.
