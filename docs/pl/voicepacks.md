# Pakiety głosowe

Inżynier brzmi jak człowiek tylko wtedy, gdy ma nagrania człowieka. Pakiet
głosowy to właśnie to: folder z plikami WAV, po jednym na frazę, które inżynier
odtwarza zamiast mówić głosem Windows. W folderze jednej frazy może leżeć kilka
podejść, a inżynier wybiera jedno losowo, więc to samo zgłoszenie powtórzone
dwa razy w trakcie stintu nie brzmi jak maszyna powtarzająca samą siebie.

Wszystko, co powie, a czego nie ma w pakiecie — Twoje imię, czas okrążenia,
kierowca, o którym nigdy nie słyszał — nadal wypowiada głos Windows. Pakiet nie
musi być kompletny, żeby był wart posiadania.

## Trzy sposoby, żeby go zdobyć

**Zainstalować opublikowany.** *Ustawienia → Głos* wypisuje pakiety opublikowane
do pobrania i instaluje wybrany na życzenie, sprawdzając sumę kontrolną, zanim
cokolwiek rozpakuje. To droga dla języka innego niż Twój.

**Nagrać samemu**, w oknie programu. To droga bez sufitu i ta, wokół której
aplikacja została zbudowana: *Ustawienia → Głos → Utwórz model głosu*.

**Wygenerować bazę Piperem**, offline, i nagrać ponownie te fragmenty, na których
Ci zależy. Przydatne, jeśli chcesz od razu czegoś poprawnego i przyjemnego albo
wolisz nie czytać 171 fraz przed jazdą.

Nie wykluczają się. Pakiet z Pipera to zwykły pakiet, więc każdą frazę w nim
można później zastąpić własnym nagraniem.

### Dlaczego nie klonowanie głosu

Próbowano tego najpierw i porzucono, a powód warto znać, zanim zaczniesz go
szukać.

Na potrzeby tego projektu wygenerowano sklonowany głos z niemal trzech minut
czystego materiału referencyjnego. Przepuszczony z powrotem przez własny
rozpoznawacz mowy aplikacji, każde nagranie „five” wracało jako „bye”, „four”
jako „boy”, a „zero” jako „yo”.

Powodem jest inwentarz. **141 ze 171 fraz to jedno lub dwa słowa**, a krótki
tekst to dokładnie miejsce, w którym model klonujący radzi sobie najgorzej: XTTS
generuje autoregresyjnie i sam decyduje, kiedy przestać, a przy dwóch słowach
prawie nic tej decyzji nie ogranicza. Piper jest modelem w stylu VITS — jedno
przejście od fonemów do przebiegu, bez pętli próbkowania, która mogłaby zbłądzić.
Nie potrafi powiedzieć innego słowa, a przy tym inwentarzu liczy się to bardziej
niż barwa.

Crew Chief rozwiązuje ten sam problem tak samo: jego pakiety są *nagrane*, a jego
11 176 nazwisk kierowców i 1052 klipy liczbowe przeczytał człowiek.

## Nagrywanie własnego

*Ustawienia → Głos → Utwórz model głosu* otwiera rejestrator: fraza do
przeczytania, odliczanie, nagranie i odsłuch do sprawdzenia.

To mniej pracy, niż brzmi. Cały inwentarz to **około czterdziestu minut przy
trzech podejściach na frazę**, i wznawia się — można to więc robić na raty, a
pakiet pokrywający połowę fraz działa od chwili, gdy go zapiszesz.

O tym, czy wynik będzie użyteczny, decyduje kilka rzeczy:

- **Z boku ust**, na szerokość dwóch palców, nie przed nimi. Mikrofon na pałąku
  ustawiony wprost w strumieniu powietrza przesterowuje na każdym *p* i *b*, a
  przesterowania nie da się później cofnąć.
- **Cichy pokój.** Wentylator albo komputer pod biurkiem trafia do każdego klipu,
  a każdy klip odtwarzany jest Tobie w środku wyścigu przez słuchawki.
- **Stała odległość.** Nie przechylaj się między podejściami. Klipy nagrane z
  czterech różnych odległości brzmią jak cztery różne osoby.
- **Wyłącz wzmocnienie mikrofonu w Windows.** To kompresor, który podbija szum
  pomieszczenia między słowami.

Czytaj je tak, jak powiedziałby je inżynier przez radio — płasko, bez pośpiechu,
lekko znudzony. Inżynier niczego nie odgrywa.

## Generowanie bazy Piperem

Piper działa offline, ze skryptów pakujących, a nie wewnątrz aplikacji. Poniższe
ścieżki są względne wobec `apps/client` w wersji ze źródeł:

```
pip install -r packaging/requirements-voices.txt
python -m piper.download_voices --download-dir models/piper en_GB-alan-medium
python packaging/make_piper_pack.py --name Piper
```

Aby zbudować z konkretnym modelem:

```
python packaging/make_piper_pack.py --name Piper --model models/piper/en_GB-alan-medium.onnx
```

**Offline i poza aplikacją, celowo.** Piper jest na procesorze dość szybki, by
kusić do wywoływania go w chwili mówienia. To wstawiłoby model o rozmiarze 63 MB
i środowisko ONNX do kompilacji, której ostatnie cztery zepsute wydania były
wyłącznie natywnymi zależnościami, których nie udało się zebrać. Pakiet to folder
plików WAV; wygenerowanie go tutaj nic aplikacji nie kosztuje i nie może zepsuć
kompilacji.

To nie jest *Twój* głos i nic nie udaje, że jest. To baza, która jest poprawna i
przyjemna, a na której każdą frazę można nagrać na nowo w oknie programu.

**Japoński potrzebuje jeszcze jednego pakietu i bez niego zawodzi w mylący
sposób.** Model japoński prosi Pipera o `pyopenjtalk`, aby zamienić tekst na
fonemy, a bez niego żadna fraza nie tworzy w ogóle dźwięku — zgłaszane jako
`wave.Error: # channels not specified`, co jest pustym plikiem wyjściowym, a
nie prawdziwą przyczyną. Oryginalny `pyopenjtalk` publikuje wyłącznie źródła i
wymaga CMake oraz kompilatora C++; `pyopenjtalk-plus` to fork publikujący koła
pod tą samą nazwą importu i znajduje się w pliku zależności powyżej.

## Jak wygląda pakiet

Pakiet to folder z podfolderem `voice` w środku, a w nim po jednym folderze na
frazę, z jej podejściami. To układ, który zapisuje `crew-chief-autovoicepack`,
więc **pakiet z Crew Chiefa wchodzi wprost**. Folder zewnętrzny jest osobny,
żeby pakiet mógł nieść licencję i swoje nagrania źródłowe, nie myląc ich z
frazami.

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

Folder, w którym leży plik WAV, jest frazą, więc głębokość między `voice` a
tym folderem jest dowolna. Rejestrator zapisuje do `pitradio/`; Crew Chief
zapisuje folder na kategorię. Oba są czytane tak samo.

Tylko WAV. To, co wypuszcza każdy generator, co czyta biblioteka standardowa, i
co nie wymaga dekodera w kompilacji, która i tak walczy z natywnymi
zależnościami.

Nazwy plików powstają z frazy, małymi literami, ze znakami przestankowymi
**usuwanymi**, a nie zastępowanymi — dzięki temu „that's enough” i „thats enough”
to ten sam klip. Zamiana apostrofu na separator dałaby `that_s_enough`, a pakiet
nagrany według jednej z pisowni po cichu mijałby się z drugą.

## Gdzie mieszkają pakiety

**Ustawienia → Głos** to miejsce, gdzie wypisane są wszystkie: co zainstalowane,
co dołączone i co można pobrać. Pakiety leżą obok Twojej konfiguracji, w
`voices/`, a nie w katalogu instalacji — aktualizacja zastępuje katalog
instalacji w całości, a pakiet to dużo dźwięku, który sam tam umieściłeś.
**Ustawienia → Głos → Otwórz folder pakietów głosowych** go otwiera.

Wrzuć folder, otwórz kartę ponownie, i pojawi się w wyborze.

## Lista fraz

**Ustawienia → Głos → Zapisz listę fraz** eksportuje każdą frazę, jaką inżynier
potrafi powiedzieć, jako CSV, w języku samego inżyniera — bo pakiet nagrywa się w
tym języku, w którym będzie mówiony.

Jest generowana z aplikacji, a nie prowadzona ręcznie, więc nie może rozjechać
się z tym, co inżynier faktycznie mówi. Skorzystaj z niej, jeśli nagrywasz poza
aplikacją albo piszesz własny generator.

## Nic nie słychać

**Sprawdź, czy wybrany jest pakiet.** *Inżynier → Głos → Głos* musi wskazywać na
pakiet, a nie na *(brak pakietu)*.

**Sprawdź urządzenie wyjściowe.** *Dźwięk → Wyjście* powinno być Twoimi
słuchawkami — tymi samymi, których używasz do czatu głosowego, a nie wyjściem
symulatora.

**Brakująca fraza to nie usterka.** Wszystko, czego nie ma w pakiecie, spada na
głos Windows, więc pakiet nagrany w połowie brzmi jak dwie osoby, zamiast
zawodzić. To zamierzone: właśnie to sprawia, że pakiet jest użyteczny, zanim
będzie skończony.
