# Inżynier

Głos z imieniem, który obserwuje symulator i mówi do ciebie: twoje czasy okrążeń,
samochody obok i odpowiedzi, gdy o coś zapytasz.

Dzieli klawisz push-to-talk ze wszystkim innym, co robi SimPitRadio. Przytrzymaj
wyzwalacz, powiedz „Chief, target P3", puść — i zamiast trafić do okna czatu,
odpowiada inżynier.

**Jest wyłączony, dopóki go nie włączysz.** Nic nie zostaje powiedziane, dopóki
nie wejdziesz w Ustawienia → Inżynier i nie zaznaczysz pola.

---

## Szybki start

1. Otwórz **Ustawienia → Inżynier** i zaznacz **Inżynier włączony**.
2. Wybierz jednego z czterech inżynierów. To ustala jego imię, głos i to, ile
   mówi.
3. Naciśnij **Test**. Powinieneś usłyszeć, jak powtarza swoje imię.
4. Ustaw **Urządzenie wyjściowe** na swoje słuchawki — te same, których używasz do
   czatu głosowego, nie wyjście symulatora.
5. Jedź. Odczyta twój czas okrążenia na linii.
6. Przytrzymaj wyzwalacz i powiedz **„Chief, target P3"**, aby uruchomić coacha
   zakrętów wobec tego, kto jest trzeci.

Jeśli Test nic nie mówi, zobacz [Nic nie zostaje
powiedziane](#nic-nie-zostaje-powiedziane) na dole.

---

## Mówienie do niego

Są dwa sposoby, by zdanie stało się poleceniem, i oba są celowo wąskie. Ten sam
klawisz wysyła wiadomości do wszystkich w twojej sesji, więc polecenie, które
inżynier *wymyśli*, to wiadomość, która po cichu nigdy nie dociera.

**Powiedz najpierw jego imię.** „Chief, target P3". Imię idzie pierwsze, fraza
zaraz po nim. `hey`, `ok` i `right` są dozwolone przed imieniem.

**Albo powiedz samą frazę** — ale tylko te, które nie przyjmują kierowcy.
„initiate corner coaching" działa bez niczego z przodu. „target Verstappen" już
nie, bo „target" mogłoby rozpocząć zwyczajne zdanie, a jego argument nie ma
końca: *„target time is a twenty three"* zostałoby inaczej połknięte w całości i
nigdy nie dotarłoby do okna czatu.

Powiedzenie samego imienia daje „go ahead", tak jak zrobiłoby prawdziwe radio — i
trzyma zabłąkane „Chief" z dala od wiadomości do dwudziestu innych osób.

**„Stop"** działa zawsze, cokolwiek jest w toku i cokolwiek to uruchomiło. Tak
samo „stand down", „cancel", „that's enough" i „forget it".

Wszystko, czego inżynier nie rozpozna, jest wiadomością i trafia do okna czatu
dokładnie tak jak wcześniej.

---

## Wybór inżyniera

Cztery są dołączone do aplikacji:

| | Głos | Styl |
| --- | --- | --- |
| **Chief** | męski | Spokojny i pełny. „Zakręt cztery, Tandy był szybszy na wyjściu, dwie dziesiąte." |
| **Ada** | żeński | Zwięzły. Pomija numer zakrętu: „Tandy, lepsze wyjście, dwie dziesiąte." |
| **Marshall** | męski | Wolniejszy i pełniejszy, jeśli pozostali wydają się pośpieszni. |
| **Vic** | żeński | Szybko i krótko. Mówi najmniej z czwórki. |

To są **ustawienia wstępne, nie nagrania** — imię, preferowany głos Windows,
tempo i to, ile mówią. Warto to powiedzieć wprost, bo „cztery głosy" zwykle
oznacza cztery zestawy audio: wygenerowany pakiet głosowy ma jeden do dwóch
gigabajtów, a dostarczenie czterech byłoby pobieraniem ośmiu gigabajtów, by
zastąpić coś, co i tak jest za darmo na każdej maszynie z Windows.

Każdy wybiera najlepszy zainstalowany głos Windows pasujący do jego preferencji i
twojego języka. W standardowej instalacji Windows 11 są zwykle dwa albo trzy,
więc dwaj inżynierowie mogą dzielić głos i różnić się tempem oraz sformułowaniami.
Jeśli chcesz konkretny, ustaw **Głos Windows**, a to nadpisze ustawienie wstępne.

**Nazywany** to to, na co reaguje. Ustaw dowolnie — imię służy wyłącznie do
zwracania się do niego, a „Bob, target P3" działa dokładnie tak samo dobrze.

---

## Co ci mówi

### Czasy okrążeń

Odczytuje twoje okrążenie, gdy przekraczasz linię, i mówi, kiedy było twoim
najlepszym. Domyślnie włączone.

### Spotter

Zapowiada samochody obok: „car left", „car right", „cars both sides", a potem
„clear", gdy odjadą. Domyślnie wyłączone, i jest jedna rzecz, którą trzeba
wiedzieć.

**Która strona jest która, nie dało się zweryfikować bez samochodu na torze.**
Pozycje pochodzą z własnych współrzędnych świata symulatora, a to, czy
obliczenia wyjdą jako lewa czy prawa, zależy od konwencji skrętności, której ten
projekt nie mógł sprawdzić z maszyny deweloperskiej. Więc jeśli mówi „lewa" o
samochodzie po twojej prawej, włącz **Zamień strony spottera** w Profile →
ustawienia wtyczki dla danej gry. Jedno zaznaczenie, raz.

Wszystko inne w spotterze jest dokładne: używa pozycji z gry, odrzuca wysokość
(żeby most albo esy w Le Mans nie stawiały nikogo przy twoich drzwiach) i nie
zapowiada samochodów z sąsiedniej prostej.

### Uszkodzenia

Mówi, co się zepsuło i czy trzeba przez to wjechać. Domyślnie włączone i wymaga
symulatora, który publikuje stan samochodu — dziś jest to Le Mans Ultimate.

> *Straciłeś element nadwozia. Box na tym okrążeniu.*

**Mówione, gdy się zmienia, a nie przez cały czas trwania.** Kierowca wożący
wgnieciony lewy tył przez pół godziny nie potrzebuje przypomnienia o tym za
każdym razem, więc odzywa się w momencie, gdy robi się gorzej, i potem milczy.
Obserwowana jest każda część odczytu, nie tylko najgorsza — druga rzecz
odpadająca od już wgniecionego samochodu to nowość, nawet jeśli powaga się nie
zmieniła.

**To, co mówi, to gdzie, a potem czy.** Już wiesz, że w coś uderzyłeś; czego nie
widzisz z fotela, to jak bardzo jest źle i czy jest czas na naprawę. Więc
nazywa miejsce — nos, tył, cała lewa strona — a potem daje jedną z trzech
odpowiedzi:

| | |
| --- | --- |
| **Box na tym okrążeniu** | samochodem nie da się ścigać, tylko doprowadzić go do boksu: zwisający element, przebita opona, utracone koło albo złamany nos. Ilość pozostałego czasu tego nie zmienia — alternatywą jest czarna flaga albo mur |
| **Box, gdy będziesz mógł** | warto naprawić. Zawsze na treningu i kwalifikacjach, gdzie postój nic nie kosztuje, a sensem bycia na torze jest działający samochód |
| **Zostań na torze, poradzimy sobie** | wyścig, w którym zostało mniej niż jedna piąta. Trzy okrążenia przed metą lepiej dowieźć uszkodzony samochód do flagi niż oddać minutę |

Lekkie uszkodzenia dostają pierwszą połowę i żadnej porady. Usłyszeć propozycję
rozważenia postoju przez zadrapany tylny błotnik jest gorzej niż nie usłyszeć
nic.

Nigdy nie mówi przez coacha. Uszkodzenia są pilne — chcesz wiedzieć, że skrzydło
odpadło, przed następnym zakrętem, a nie po nim — ale krytyka, o którą sam
poprosiłeś, nie jest warta przerwania dla samochodu, który za cztery sekundy
nadal będzie zepsuty. Spotter to jedyna zapowiedź, która mówi ponad czymkolwiek.

---

## Kogo obserwuje

Inżynier utrzymuje **fokus**: jednego kierowcę, z którym cię zestawia. Nie musisz
tego ustawiać. Domyślnie jest to **samochód przed tobą w twojej klasie** albo
samochód za tobą, gdy ją prowadzisz — bo nie ma nikogo z przodu do gonienia, a
pytaniem staje się to, czy utrzymujesz ich za sobą.

Podąża za zmianą dopiero wtedy, gdy pozycja **utrzyma się przez osiem sekund**.
Pozycje kotłują się bez przerwy: zmierzone na prawdziwym starcie wyścigu,
piętnastu różnych kierowców było samochodem z przodu w ciągu dziewięćdziesięciu
sekund, a każda zmiana wyrzucała zebrane okrążenia, więc nigdy nie miał ich dość,
by cokolwiek powiedzieć.

Powiedz, jeśli chcesz kogoś innego:

- `focus on {kierowca}` — albo „keep an eye on", „keep tabs on", „study", „watch"
- `default focus` — powrót do samodzielnego wyboru
- `stop focusing` — wyłączone i pozostaje wyłączone, dopóki go nie poprosisz z
  powrotem

Kierowca, którego wskażesz, nigdy nie zostaje nadpisany. Powrót dwa zakręty
później do tego, kto jest z przodu, to aplikacja spierająca się z tobą.

Karta Status pokazuje, kto jest obserwowany, a `what are we watching` o to pyta.

---

## Pytanie go o różne rzeczy

Każde pytanie ma pole fraz w Ustawienia → Inżynier, po jednej w wierszu, a to, co
wpiszesz, zastępuje wartości domyślne. Każde można wyłączyć; wyłączone pytanie nie
wnosi żadnych fraz, więc jego słowa docierają do okna czatu jak wszystkie inne,
zamiast być przechwycone i pozostawione bez odpowiedzi.

- **Twój samochód** — `what's my best lap`, `how are the tyres`, `what's the
  damage`, `how's the fuel`, `how much fuel do I need to finish the race when I
  pit on the next lap`
- **Sesja** — `who has the fastest lap`, `who's fastest`,
  `who has the fastest sector`, `who's in the lead`, `who's ahead`
- **Gdzie ucieka czas** — `where am I slower`, `where am I faster`, każde z nich z
  `than {kierowca}` na końcu

**Pytania wyprzedzają kolejkę.** Pytanie zadane, gdy inżynier był w połowie
zapowiedzi, czekało za nią albo było wprost odrzucane — kolejka mieści sześć, a
ruchliwe okrążenie ją wypełnia — więc pytałeś, słyszałeś, jak mówi o czymś innym,
i nie dostawałeś odpowiedzi. Odpowiedź teraz sprząta zwykły ruch, przerywa to, co
jest mówione, i nie może zostać wypchnięta. Wciąż ustępuje spotterowi, bo
samochód obok to kwestia niezderzenia się.

**Pytanie, na które nie potrafi odpowiedzieć, zostaje poza oknem czatu.** „Who's
faster?" nie jest frazą, którą zna, i kiedyś przelatywało dalej i szło do sesji.
Wszystko, co czyta się jak pytanie — kończy się znakiem zapytania albo zaczyna od
zaimka pytającego — dostaje zamiast tego „say again". Na karcie Czat tekstowy
jest pole wyboru, jeśli wolisz stare zachowanie, a pytanie, które jawnie
wyłączyłeś, i tak dociera do czatu, bo wyłączenie go to twój sposób powiedzenia,
że te słowa są twoje.

Imię inżyniera możesz umieścić z każdej strony: „Bono, how are the tyres" i „how
are the tyres, Bono" działają oba. To przecinek oznacza je jako imię, więc `focus
on Bono` nadal celuje w kierowcę o nazwisku Bono.

### Gdzie jestem wolniejszy

Ta, którą warto znać. Zestawia cię z twoim fokusem **zakręt po zakręcie,
uśredniając po każdym okrążeniu tej sesji**, zamiast odczytywać z jednego —
pojedyncze okrążenie mówi, co się na nim wydarzyło, a pytanie dotyczy tego, co
dzieje się wciąż.

> Chief, where am I slower
>
> *Zakręt trzy, jesteś wolniejszy na wejściu, dwie dziesiąte.*
>
> *Zakręt siedem, on ma lepsze wyjście, dziesiąta.*

Mówi *jak*, nie tylko gdzie: wejście, wyjście, późniejsze hamowanie albo
wolniej przez cały zakręt. Tam, gdzie istnieje katalog zakrętów dla toru, używa
nazwy — „Eau Rouge" zamiast „zakręt trzy".

**Jak znajduje zakręty.** Nie ma mapy toru i nie będzie — wymagałaby pliku na
każdy tor, dezaktualizowałaby się przy każdej zmianie układu i działałaby na
czterech torach, na które ktoś zdążył. Zakręt to miejsce, gdzie okrążenie
referencyjne zwolniło i znów przyspieszyło, co jest prawdą na każdym torze w
każdym symulatorze. Szykany liczą się jako jeden zakręt.

**Opisuje, nie instruuje.** „On ma lepsze wyjście" to to, co aplikacja wie. Nie
wie, czy chodziło o linię, opony czy tunel aerodynamiczny, a „hamuj później"
byłoby zgadywaniem przebranym za coaching.

**Jeśli brakuje okrążeń, mówi czyich.** Twoich albo jego — inaczej „brak okrążeń
do porównania" zostawia cię ze zgadywaniem, których.

### Czego nie użyje jako odniesienia

- Okrążenia, którego jakakolwiek część była w alei serwisowej. Szybkie okrążenie,
  które w rzeczywistości było skrótem przez boksy, stałoby się inaczej celem, do
  którego mierzy się wszystkich, i nic by w nim nie wyglądało źle.
- Okrążenia, do którego dołączyłeś w połowie.
- Okrążenia, dla którego symulator nie podał czasu — okrążenia wyjazdowego albo
  samochodu, który dopiero się pojawił.
- Czegokolwiek z innego toru. Zmiana toru czyści wszystko.

Milczy również, gdy jesteś obserwatorem. Komentowanie okrążenia, które oglądasz,
a nie prowadzisz, byłoby bez sensu.

---

## Gdy twój symulator nie może odpowiedzieć

Nie każdy symulator publikuje to samo, a inżynier mówi to zamiast zgadywać.
Oryginalne Assetto Corsa na przykład publikuje **twój własny samochód i nic o
nikim innym** — żadnego nazwiska, pozycji ani czasu okrążenia innego kierowcy —
więc cokolwiek zestawiającego cię ze stawką nie ma danych żadną drogą.

Zapytaj tam „who's leading", a odpowie **„ta gra tego nie podaje"**. To celowe i
nie jest tym samym co „nie ma kogo obserwować", co oznacza, że stawka naprawdę
jest pusta. Powiedzenie kierowcy na siódmym miejscu, że nikogo przed nim nie ma,
nie jest bezużyteczną odpowiedzią — jest fałszywą.

Zachowania, które potrzebują danych, których twój symulator nie dostarcza, są
pomijane z wpisem w dzienniku, zamiast zostawiać je włączone i nieme:

```
Spotter is on but this sim does not publish positions or spotter; it will stay quiet
```

`--telemetry` wypisuje, co twój symulator faktycznie wysyła — zobacz ostatnią
sekcję.

---

## Inne języki

Inżynier mówi w języku ustawionym dla **transkrypcji**, chyba że przypniesz go na
karcie Inżynier. To właściwa wartość domyślna, a nie arbitralna: twoje polecenia
przychodzą przez Whisper, więc jeśli Whisper produkuje hiszpański, inżynier
nasłuchujący angielskich fraz nigdy nie usłyszy ani jednej.

Wszystko, co mówi — łącznie z frazami wyzwalającymi — przechodzi przez te same
katalogi tłumaczeń co okno. Dodanie języka to jeden plik JSON w
`src/pitradio/locale/`; zobacz główny README.

**Liczby są zapisywane słownie po angielsku, a wszędzie indziej czytane jako
cyfry.** Nie z lenistwa: gramatyka liczebników naprawdę jest specyficzna dla
języka — niemiecki odwraca dziesiątki i jedności, hiszpański zlewa dwudziestki —
a implementacja zrobiona w połowie produkowałaby pewne siebie bzdury w czyimś
własnym języku. Cyfry przekazują problem silnikowi mowy dla danego języka, który
już rozwiązuje go poprawnie. Skutkiem ubocznym jest to, że nieangielski pakiet
głosowy nie może pokryć liczb i wychodzą one syntetyzowane.

---

## Pakiety głosowe

**To, z jakiego pakietu mówi ten inżynier, ustawia się tutaj, na karcie
Inżynier**, a coach wybiera swój na karcie Coaching — to dwa osobne zadania i
kierowca może rozsądnie chcieć słyszeć, który z nich mówi.

**Instalowanie, nagrywanie i usuwanie pakietów to Ustawienia → Głos.** Pakiet to
coś, co posiada aplikacja; to, z którego mówi dana persona, jest ustawieniem tej
persony.

Dwa pakiety są dołączone: **Norman** i **Claudia**. Oba zostały wygenerowane
Piperem — zobacz [voicepacks.md](voicepacks.md) — i każdy można zastąpić własnym.

Pakiet głosowy zastępuje syntezator nagranym dźwiękiem: folder plików WAV, jeden
folder na frazę, po kilka ujęć każda. Inżynier wybiera ujęcie losowo, i to w
przeważającej mierze sprawia, że pakiet brzmi jak człowiek, a synteza mowy nie.

**Układ jest taki jak w Crew Chief**, celowo:

```
%APPDATA%\pitradio\voices\
  Ada\
    voice\
      corners\
        two_tenths\
          a.wav
          b.wav
```

Płaskie `<pakiet>/<fraza>/*.wav` też działa i to właśnie dostajesz, nagrywając
samodzielnie.

Ten układ sprawia, że pakiet wygenerowany przez
[crew-chief-autovoicepack](https://github.com/cktlco/crew-chief-autovoicepack)
można wrzucić bez zmian. Aby wygenerować taki dla fraz SimPitRadio zamiast fraz
Crew Chief:

1. Ustawienia → **Głos** → **Zapisz listę fraz**. To zapisuje
   `phrase_inventory.csv` do folderu głosów, w języku inżyniera.
2. Podaj tę listę generatorowi zamiast jego własnej.
3. Umieść folder wyjściowy pod `voices\` i wybierz go na karcie Inżynier (albo
   użyj **Ustawienia → Głos → Otwórz folder pakietów głosowych**, aby tam
   trafić).

**Nazwisk i liczb nigdy nie ma w pakiecie** i zawsze wypowiada je głos Windows.
Nie da się tego obejść — żaden pakiet nie pomieści nazwiska każdego kierowcy ani
każdego czasu okrążenia — więc zapowiedź w rodzaju „zakręt cztery, Tandy był
szybszy na wyjściu" jest częściowo nagrana, a częściowo syntetyzowana. Ten szew
słychać. To wciąż właściwy kompromis: alternatywą jest pakiet, który przestaje
być używany w chwili, gdy padnie nazwisko kierowcy, a to większość zapowiedzi.

Pakiety są przechowywane obok twojej konfiguracji, a nie w katalogu instalacji,
więc aktualizacja nie usuwa gigabajta dźwięku, który postanowiłeś
zainstalować.

---

## Jak to się składa

Inżynier działa na **własnym wątku**, oddzielnym od czterech, które SimPitRadio
już ma, a mówienie dostaje wątek poniżej. Żaden z nich nie może zablokować hooka
klawiatury, workera ani okna.

Wszystko, co robi, ma prawo zawieść. To, że inżynier zamilknie, nigdy nie może
kosztować cię wyzwolenia, transkrypcji ani wiadomości w czacie — więc jeśli coś
tutaj się zepsuje, słowa idą do okna czatu tak jak zawsze, a problemem jest wpis
w dzienniku.

Czyta symulator dziesięć razy na sekundę przez tę samą wtyczkę, która dostarcza
nazwisk kierowców do wzmianek. Nie ma drugiej ścieżki danych ani dodatkowego
połączenia z grą.

---

## Nic nie zostaje powiedziane

**Test nic nie robi.** Syntezator działa w hoście PowerShell z użyciem
`System.Speech`, który jest częścią .NET Framework na każdej maszynie z Windows
10 i 11. Poszukaj w dzienniku `no speech host` — zablokowana maszyna z wyłączonym
PowerShellem to zwykła przyczyna.

**Słyszysz go, ale nie w słuchawkach.** Ustaw urządzenie wyjściowe na karcie
Audio. Domyślnie jest to urządzenie systemowe, którym podczas wyścigu często jest
głośnik w kierownicy.

**Odczytuje czasy okrążeń, ale nigdy nie prowadzi coachingu.** Coach zakrętów
potrzebuje okrążenia referencyjnego. Dopóki kierowca, którego wskazałeś, go nie
ukończy — czysto, nie przez boksy — nie ma z czym porównywać. Wiersz stanu na
karcie Inżynier mówi, ile zakrętów zmapował.

**Prowadzi coaching, ale przy niektórych zakrętach nic nie mówi.** Tak jest
zaprojektowane: te zakręty mieściły się w progu. Obniż **Próg zakrętu**, jeśli
chcesz więcej.

**Nie reaguje na nic, co mówisz.** Sprawdź imię na karcie Inżynier i pamiętaj, że
każda fraza przyjmująca kierowcę wymaga imienia z przodu. Powiedz samo „Chief" —
jeśli dostaniesz „go ahead", to słucha, a problemem jest fraza.

**Zjadł wiadomość.** Nie powinien. Jeśli inżynier przechwycił coś, co chciałeś
wysłać, wpis w dzienniku mówi `that was for the engineer` wraz z tym, co
dopasował — proszę, zgłoś to z tym wpisem, bo zbyt gorliwy matcher to jedyny błąd
w tej funkcji, który kosztuje coś realnego.

---

## Sprawdzanie, co twój symulator faktycznie wysyła

Większość problemów typu „inżynier nic nie mówi" to nie inżynier. Uruchom grę,
wyjedź **na tor i ruszaj**, potem:

```bash
python -m pitradio --telemetry
```

Wypisuje każdy samochód tak, jak widzi go inżynier — dystans na okrążeniu,
prędkość, licznik okrążeń, sektor, czasy okrążeń, flagę boksów, pozycję w świecie
— a co bardziej użyteczne, porównuje kolejne odczyty i mówi ci, czy cokolwiek się
zmienia.

Ta ostatnia część liczy się bardziej, niż brzmi. Symulator zapauzowany albo
stojący w menu wciąż publikuje blok, który wygląda całkowicie zdrowo: samochody,
pozycje, prędkości, wszystko wiarygodne. Nic się nie rusza, więc inżynier nie ma
nic do powiedzenia, a żaden pojedynczy zrzut tego nie pokazuje. Jeśli zgłosi

> Nothing changed across 4 reads, including the sim's own clock.

to gra jest zapauzowana, w menu albo sesja się skończyła — nie jest zepsuta.

Na co patrzeć, gdy *żyje*:

| Kolumna | Zasila |
| --- | --- |
| `lapdist`, `speed` | wykrywanie zakrętów i to, gdzie ucieka czas |
| `lap`, `last lap`, `best lap` | zapowiedzi czasu okrążenia i najszybszego okrążenia |
| `sec` — zmienia się trzy razy na okrążenie | każdą zapowiedź sektorową |
| `world x/y/z` — inne dla każdego samochodu | spottera |

Wiersz `provides:` na górze mówi, które z tych rzeczy wtyczka deklaruje
dostarczać. Zachowanie potrzebujące czegoś nieobecnego jest pomijane, zamiast
zostawać włączone i nieme, a dziennik mówi, której zdolności brakuje.

## Co potrafi każdy symulator

Symulatory publikują bardzo różne rzeczy, a zachowanie, którego danych brakuje,
jest **pomijane z wpisem w dzienniku**, zamiast zostawać włączone i nieme.

| | Le Mans Ultimate | iRacing | Assetto Corsa / Competizione / Evo | Automobilista 2, Project CARS 2 / 3 |
| --- | --- | --- | --- | --- |
| Czasy okrążeń | tak | tak | tak | wyliczane |
| Nowe najszybsze okrążenie | tak | tak | — | tak |
| Zapowiedzi sektorowe | tak | — | tak | — |
| Gdzie jestem wolniejszy | dowolny kierowca | dowolny kierowca | twoje własne najlepsze | dowolny kierowca |
| Kto jest przed / prowadzi | tak | tak | — | tak |
| Spotter | geometria | własna zapowiedź symulatora | tylko Competizione | geometria |
| Wzmianki o kierowcach, „P3" | tak | tak | — | tak |
| Uszkodzenia | tak | — | — | — |
| Coaching i diagram segmentu | tak | — | — | — |

Luki to gry, nie aplikacja:

- **iRacing** nie publikuje czasów sektorowych dla poszczególnych samochodów, więc
  zapowiedzi sektorowe nie mają z czego korzystać. Jego spotter jest najlepszy ze
  wszystkich — `CarLeftRight` pochodzi z rzeczywistych nadwozi, więc nie potrzebuje
  ani ustawienia zamiany stron, ani szacowania szerokości.
- **Assetto Corsa** publikuje czasy okrążeń tylko dla twojego samochodu i żadnych
  nazwisk kierowców. Dlatego nie ma klasyfikacji ani wzmianek i dlatego „gdzie
  jestem wolniejszy" goni twoje własne najlepsze okrążenie — do czego i tak służy
  sesja treningowa.

  Oryginalna gra idzie dalej: nie publikuje **żadnego innego samochodu**, nawet
  pozycji. Sprawdzone na prawdziwym wyścigu ośmiu samochodów, tablica współrzędnych
  zawierała gracza w slocie zero i nietkniętą pamięć we wszystkich pozostałych —
  zera, jeden NaN, jedną liczbę zdenormalizowaną. Więc spotter też nie ma tam z
  czego korzystać, a wtyczka mówi to per sesja, a nie per gra: **Competizione
  publikuje** tę tablicę i ta sama wtyczka raportuje dla niej pozycje.
- **Automobilista 2 i Project CARS** niosą *liczniki* okrążeń, a nie czasy w tej
  części swojego bloku, której warto ufać, więc czasy okrążeń są tu mierzone
  stoperem. Okrążenie obejmujące pauzę wychodzi dłuższe, niż było; to zawodzi w
  bezpieczną stronę, bo napompowane okrążenie nigdy nie staje się odniesieniem,
  które goni porównanie. Ich pole sektora to enum, którego nie dało się ustalić
  spoza gier, więc zapowiedzi sektorowe nie są oferowane.

Automobilista 2 ma własny wpis, zamiast dzielić ten od Project CARS, żebyś mógł
wybrać grę, którą faktycznie uruchamiasz, i żeby obie zachowały osobne ustawienia
spottera i bliskości.

**Le Mans Ultimate to jedyny zweryfikowany wobec działającej gry.** Każdy inny
czytnik jest testowany wobec pamięci współdzielonej zbudowanej ręcznie, co wyłapuje
złą szerokość pola, źle zdekodowane nazwisko albo błąd wypełnienia — a nie może
wyłapać błędnego założenia co do tego, co symulator umieszcza gdzie. Uruchom
`--telemetry` z grą na torze, zanim zaufasz któremukolwiek z nich, a zwłaszcza
Assetto Corsa Evo, które wciąż jest we wczesnym dostępie i może przesunąć swój
układ.

**iRacing jest oznaczony jako eksperymentalny** i tak też pokazuje się w wyborze
profilu. Nie dlatego, że to gorszy kod niż pozostałe, ale dlatego, że nikt
pracujący nad SimPitRadio nie ma jego kopii — więc, w odróżnieniu od reszty, nie
zostanie sprawdzony wobec rzeczywistości, dopóki ktoś, kto go ma, nie uruchomi
`--telemetry` i nie powie, co wróciło. Jeśli to ty, proszę, zrób to; notatka na
liście wtyczek prosi dokładnie o to.

## Ustawienia per symulator

Trzy liczby inżyniera mieszkają w **profilu**, pod ustawieniami wtyczki dla gry, a
nie na karcie Inżynier — bo opisują grę, a nie twój gust:

- **Zamień strony spottera** — jeśli „lewa" oznacza samochód po twojej prawej
- **Nakładanie spottera (metry)** — jak daleko wzdłuż toru wciąż liczy się jako obok
  siebie. Hypercar ma około 5 m
- **Szerokość spottera (metry)** — jak daleko w bok się liczy, zanim będą po prostu
  na innej części toru

Długości samochodów i konwencje osi różnią się między symulatorami, więc liczba
pasująca do jednej gry jest błędna w następnej.

## Flagi i incydenty

Osobne zachowanie, celowo oddzielone od spottera. Własne foldery dźwięków Crew
Chief rysują granicę i jest to właściwa granica: `car_left`, `still_there` i
`clear_all_round` są w `spotter/`, podczas gdy `stopped_car_in_turn_3`,
`slow_car_ahead` i `local_yellow_ahead` są w `flags/`. Spotter odpowiada na „kto
jest obok mnie", co jest geometrią. Flagi odpowiadają na „co się stało z torem",
co nią nie jest.

Wyprowadzanie drugiego z pierwszego jest tym, co produkowało ostrzeżenie w każdej
strefie hamowania: SimPitRadio miało regułę mówiącą, że samochód dużo wolniejszy
od ciebie jest zagrożeniem, a strefa hamowania to dokładnie miejsce, gdzie
samochód przed tobą jest dużo wolniejszy od ciebie. Tej reguły już nie ma.

**Trzy źródła, niejednakowo godne zaufania.**

*Żółta flaga na całym torze* i *niebieska* pochodzą z symulatora i są wiarygodne —
`mGamePhase`, `mYellowFlagState` i `mFlag` per samochód w LMU czytają się
sensownie wobec sesji na żywo.

*Lokalne żółte są wyprowadzane*, bo `mSectorFlag` w LMU jest bezużyteczne. Jest
udokumentowane jako „czy w każdym sektorze są w tej chwili lokalne żółte" i czyta
się jako `[11, 11, 1]` pod zieloną flagą, przy poprawnych polach po obu stronach —
więc to nie jest przesunięty offset, LMU po prostu publikuje tam coś innego.
Odczytane jako wartości logiczne, założyłoby trwałe żółte na cały tor. Więc
incydent tutaj znaczy to, co rozumie przez niego sędzia torowy: samochód zatrzymał
się na drodze i stoi tam od dwóch sekund. To wyprowadzenie z danych, które
symulator publikuje uczciwie, w tym samym duchu, co szukanie zakrętów w wykresie
prędkości zamiast dostarczania mapy toru.

Kosztem jest to, że zapowiedź nie może wyprzedzić incydentu — prawdziwa żółta
wisi w chwili, gdy sędziowie ją widzą, a ta czeka na pewność. Korzyścią jest to,
że nigdy nie myli się co do zielonego toru, a to właśnie ta awaria sprawia, że
ludzie wyłączają funkcję.

**Incydenty są nazywane po zakręcie, nie po kierowcy.** Przy prędkości, przy której
to ma znaczenie, „zakręt sześć" to coś, na co kierowca może zareagować, a nazwisko
to liczba sylab, na którą nie może. Numeracja jest ta z księgi okrążeń, żeby
kierowca słyszał jeden zestaw numerów zakrętów, zamiast żeby jedna funkcja używała
jednego, a flagi drugiego; zakręty są znajdowane raz na okrążenie referencyjne i
buforowane, bo `find_corners` przepróbkowuje całe okrążenie, a to działa kilka
razy na sekundę. Bez okrążenia referencyjnego nazywany jest sektor.

**Gdy to ty jesteś incydentem, zapowiedzi boczne ustają.** Opisywanie kierowcy
obróconego samochodu aut, które go mijają, jest szumem; jedynym użytecznym
pytaniem jest to, czy jest miejsce, by ruszyć, i
[rejoin.py](../src/pitradio/engineer/rejoin.py) na nie odpowiada — porównując *czas
do bycia bezpiecznym* z *czasem do przyjazdu następnego samochodu*, a nie dystans z
dystansem. Stojący samochód musi odzyskać całe przyspieszenie przed pierwszym
przyjazdem. Dlatego naiwna odpowiedź „trzy sekundy czystego toru" powoduje, że
ludzi ktoś zbiera.

Dwa zabezpieczenia, oba wyuczone, a nie założone: nic nie jest mówione w alei
serwisowej, gdzie bycie w bezruchu jest sensem, i nic, zanim samochód w ogóle się
poruszył — stanie na starcie przed światłami to bezruch, na linii jazdy, z całą
stawką z tyłu, czyli dokładnie każde wejście, na które patrzy porada o powrocie na
tor.

Zobacz [voicepacks.md](voicepacks.md) w sprawie generowania głosu.

## Pytania

Odrębne od zachowań, a to rozróżnienie nie jest księgowością. Zachowanie to coś,
co inżynier *robi dalej* — zobacz [Co ci mówi](#co-ci-mówi) — i niesie
interwał powtarzania, bo samochód obok przestaje tam być, choć nic się nie dzieje.
Pytanie ma odpowiedź, a gdy odpowiedź padła, nic nie działa. Modelowanie jednego
jako drugiego umieściłoby „who has the fastest lap" na liście Zachowań, gdzie
każdy wpis ma interwał powtarzania, a nie ma czegoś takiego jak odpowiadanie na
pytanie ponownie co 1,2 sekundy.

Są trzy: najszybsze okrążenie, najszybszy sektor i twoje własne najlepsze.

**Parametr idzie po słowie kluczowym i nigdy nie jest częścią frazy.** To, o co
kierowca może zapytać, zależy od symulatora, w którym się znajduje — klas na tej
stawce, sektorów, które ma ten tor — i nic z tego nie należy do frazy, którą ktoś
wpisał w pole ustawień. „Who has the fastest sector" to fraza; „three in GT3" to
to, co przyszło po niej, sparsowane wobec sesji. Klasa jest dopasowywana przez
`mentions.class_aliases`, więc „LMGT3" z LMU reaguje na „GT3" dokładnie tak jak
wszędzie indziej, a „LMP2" wciąż odmawia reagowania na „P2", bo to jest pozycja.

**Zamknięta przestrzeń argumentów jest obroną przed fałszywymi trafieniami** i
lepszą niż liczenie słów. `phrases.MIN_BARE_WORDS` chroni polecenia mówione,
wymagając dwóch słów przed otwartym parametrem; tutaj to nie wystarcza, bo „who
has the fastest lap of my life that one" przechodzi to bez trudu i zostałoby
wzięte za pytanie o klasę zwaną „of my life that one" — połykając wiadomość. Ale
argumentem pytania może być tylko klasa na tej stawce, sektor między jeden a trzy,
albo nic. Wszystko inne nie było pytaniem, czymkolwiek się zaczęło. Zaadresowane po
imieniu jest nim mimo wszystko: ktoś, kto powiedział imię inżyniera, mówił do
niego.

**Brak nazwanej klasy oznacza twoją własną klasę**, bo to właśnie ma na myśli ktoś
w samochodzie GT3, pytając „who has the fastest lap". Nazwana klasa, w której
nikogo nie ma, dostaje o tym informację, zamiast być po cichu obsłużona wynikiem
ogólnym — błędna odpowiedź podana pewnie to tryb awarii bez objawu.

Każde ma pole wyboru na karcie Inżynier i nic więcej. To, o co można zapytać, jest
ustalone przez to, co publikuje symulator, więc edytowalne pole fraz sugerowałoby
tam, że możesz jakieś wymyślić.

Przełącznik zasługuje na swoje miejsce z innego powodu: **każda fraza, której
inżynier nasłuchuje, to fraza, którą można wyjąć z wiadomości przeznaczonej dla
całej sesji**, a ktoś, kto nigdy o te rzeczy nie pyta, nie ma powodu ponosić tego
ryzyka. Wyłączenie jednego usuwa jego frazy z matchera całkowicie, zamiast uciszać
go dalej w łańcuchu — inaczej „who has the fastest lap" wciąż byłoby wyjęte z
wiadomości, a potem pozostawione bez odpowiedzi, co jest najgorsze z obu. Brak w
konfiguracji oznacza włączone, więc dodanie pytania nigdy nie wymaga migracji.

## Spotter i skąd biorą się jego liczby

Każdy próg w `spotter.py` jest ten z Crew Chief, odczytany z lokalnej instalacji, a
nie zgadnięty — jego `ui_text/en.txt` nazywa każde ustawienie, a
`CrewChiefV4.exe.config` dostarcza wartości domyślne:

| Nasz | Crew Chief | Domyślnie |
| --- | --- | --- |
| `DEFAULT_CAR_LENGTH` | `lmu_spotter_car_length` | 4,5 (5 dla pcars2/ACC, 4,4 dla AMS2) |
| `GAP_FOR_CLEAR` | `spotter_gap_for_clear` | 0,5 m |
| `OVERLAP_DELAY` | `spotter_overlap_delay` | 50 ms |
| `CLEAR_DELAY` | `spotter_clear_delay` | 150 ms |
| `MIN_SPEED` | `min_speed_for_spotter` | 10 m/s |
| `MAX_CLOSING_SPEED` | `max_closing_speed_for_spotter` | 12 m/s |
| interwał powtarzania | `spotter_hold_repeat_frequency` | 3 s |

Trzech z nich brakowało tu całkowicie i każdy powodował usterkę, którą kierowca
mógł odczuć:

**Limit prędkości zbliżania to to, co wyłapuje samochód dublujący.** Coś, co
przyjeżdża 12 m/s szybciej, przecina całe okno nakładania w znacznie mniej niż
sekundę, więc zanim zapowiedź zostanie wypowiedziana, już przejechali — a kierowca
trzyma linię dla samochodu, którego już nie ma.

**Minimalna prędkość to to, co zatrzymuje aleję serwisową i pole startowe.** Poniżej
10 m/s samochody wokół ciebie stoją albo mijają w tempie spacerowym, a zapowiadanie
ich to sposób, w jaki spotter kończy wyłączony.

**Dwa opóźnienia stabilizacji to to, co zatrzymuje paplaninę.** Dwa samochody w tym
samym zakręcie wchodzą i wychodzą z nakładania tak, jak oddychają. Są celowo różnej
długości: opóźnienie nakładania jest krótkie, bo spóźnione ostrzeżenie jest
bezwartościowe, a opóźnienie zwolnienia jest dłuższe, bo może sobie pozwolić na
pewność — kierowca, który trzyma swoją linię o dziesiątą sekundy dłużej niż trzeba,
nic nie stracił.

Zasięg zwolnienia to `długość samochodu + odstęp`, a nie druga wielokrotność
długości. Rozróżnienie ma znaczenie na skrajach: dla gokarta „kolejna długość
samochodu" to dwa metry histerezy i zapowiedź wisi stanowczo za długo, podczas gdy
pół metra prześwitu to pół metra, cokolwiek prowadzisz.

**Spotter milczy pod żółtą flagą na całym torze** — `fcy_stop_spotter_immediately`
z Crew Chief, domyślnie włączone. Stawka jest ściśnięta w tempie pełzania i trwale
nachodzi na siebie, więc każda zapowiedź byłaby prawdziwa i bezużyteczna.

### Co mówi

Słownictwo to folder `Sounds/voice/spotter/` z Crew Chief, więc pakiet głosowy
zbudowany dla Crew Chief wypowiada to wszystko bez mapowania: `car_left`,
`car_right`, `still_there`, `hold_your_line`, `in_the_middle`, `clear_left`,
`clear_right`, `clear_all_round`, `three_wide_on_left`, `three_wide_on_right`.

Dwa z nich zastąpiły zapowiedzi, które podawały ten sam fakt trudniejszą drogą:

* **„Three wide, you're on the right"** było „two cars left". Kierowca słyszący
  starą wersję musi wyliczyć, gdzie go to stawia, będąc zajętym; nowa mówi wprost,
  po której stronie nie ma miejsca.
* **„In the middle"** było „three wide", dla jednego samochodu po każdej stronie.

Powtórzenie mówi `still there` po jednej stronie i `hold your line` po obu, bo to
różne instrukcje — jedna znaczy nie jedź tam, druga znaczy nie ruszaj się.
Pojawienie się i jego powtórzenia dzielą klucz wyprowadzony z *liczników*, żeby
interwał powtarzania nimi rządził; klucz zmieniający się wraz ze sformułowaniem
czyniłby kontynuację nową zapowiedzią, należną już przy następnym tyknięciu.

**Zestaw owalny jest celowo nieobecny** — `car_inside`, `clear_outside`,
`three_wide_on_inside`. To, która strona jest wewnętrzna, jest faktem o
przechyłce, której żaden z tutejszych symulatorów nie publikuje, a Crew Chief
trzyma ją per tor. Zgadywanie tego to zapowiedź pewnie odwrócona na opak.

### Paliwo

„How much fuel do I need to finish the race when I pit on the next lap" albo
„...when I pit in five laps". **Odpowiedzią jest procent**, bo to jest liczba na
własnym ekranie paliwa symulatora, a kierowca ma około czterech sekund w drodze do
wjazdu do boksów, żeby ją wykręcić. Litry są rachunkiem.

**Zużycie jest mierzone, nigdy zakładane.** Zużycie samochodu zależy od toru, mapy
paliwowej, ruchu na torze i tego, jak dana osoba go prowadzi, więc litry na
okrążenie to tutaj to, co *ten* samochód zużywał na *tych* okrążeniach — krótka
średnia krocząca, żeby podążała za zmianą mapy paliwowej, zamiast być ciągniętą w
tył przez cały stint. Dopóki nie zostanie ukończone okrążenie, nie ma odpowiedzi i
mówi o tym. Liczba paliwa wymyślona z niczego to jedyna błędna odpowiedź tutaj,
która kończy czyjś wyścig.

Trzy szczegóły, które inaczej byłyby odkrywane na nowo:

* **Okrążenia przed postojem nie są tankowane.** To, co jest teraz w baku, je
  pokrywa. Pytaniem są tylko te po nim, i dlatego to nigdy nie odczytuje bieżącego
  poziomu.
* **`mMaxLaps` to `INT_MAX` w sesji na czas.** Wzięte dosłownie, prosi o paliwo na
  dwa miliardy okrążeń. `SessionInfo` niesie `max_laps` *albo* `ends_at`, nigdy
  oba, a wtyczka decyduje które — inżynier nigdy nie zgaduje brakującego. Wyścig na
  czas dzieli pozostały zegar przez własne najlepsze okrążenie kierowcy i zaokrągla
  **w górę**, bo flaga pada na końcu okrążenia, na którym jesteś, gdy czas się
  kończy.
* **Zatankowanie ponad pojemność baku jest raportowane, nie przycinane.** Oznacza,
  że postój nie może być ostatnim, a kierowca, któremu powiedziano „sto procent"
  bez tej informacji, planuje wyścig, który się nie uda.

Wszystko inne zaokrągla w stronę większej ilości paliwa: zabraknięcie to wycofanie,
a wożenie zapasowego litra to dziesiąta na okrążeniu.

Paliwo trafia do `Car` **tylko dla samochodu gracza** — symulatory publikują
telemetrię baku dla samochodu, którym jedziesz, i niczyjego innego — i jest
dołączane przez dopasowanie `mID`, bo tablica telemetrii LMU jest indeksowana przez
`playerVehicleIdx`, a tablica klasyfikacji nie. Dołączanie po pozycji umieściłoby
twój bak na samochodzie, który akurat był sklasyfikowany w tym slocie.

## Bycie z dala od kierownicy

Inżynier nic nie mówi i **niczego nie rejestruje**, gdy kierowca nie jedzie. Trzy
stany, i potrzebują trzech różnych sygnałów:

* **Pauza** — zegar symulatora staje, podczas gdy zegar tej maszyny nie, i ta
  różnica jest sygnałem. Nie `mGamePhase`: to pokazywało *zieloną flagę* przez całą
  sesję stojącą zapauzowaną w garażu, z `mCurrentET` zamrożonym na 2218.0. Faza
  mówi, jakiego rodzaju jest to sesja, a nie czy działa.
* **W garażu** — tutaj zegar idzie dalej, więc zegar nie może być sygnałem. Jest nim
  `mInGarageStall`. Odrębne od `in_pits`, które obejmuje całą aleję serwisową:
  samochód odbywający postój ściga się.
* **Oddany SI** — `mControl` wynosi 1, a tak wygląda tryb obserwatora.

**Nic też nie jest obserwowane, nie tylko nic nie jest mówione.** Zapauzowany
symulator publikuje w kółko tę samą klatkę, a podanie tego do księgi okrążeń
rejestruje samochód niepokonujący żadnego dystansu tak długo, jak ktoś zostawi grę
stojącą — zepsute okrążenie referencyjne zamiast brakującego. Stan spottera jest
odrzucany na wejściu z tego samego powodu: samochód, który był obok przed pauzą,
jest faktem o chwili, która minęła.

**Zapauzowanie wyścigu online nie jest wykrywane i wykryte być nie może.** Zegar tam
idzie dalej, bo wyścig idzie dalej — menu jest otwarte na tej maszynie, a samochody
wciąż jadą. Nic w pamięci współdzielonej nie odróżnia tego od zwykłej jazdy, a
wymyślenie sygnału na to uciszyłoby inżyniera podczas prawdziwego wyścigu. A to
gorszy z dwóch błędów.
