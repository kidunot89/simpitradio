# Czat tekstowy

To, do czego zbudowano SimPitRadio. Przytrzymaj klawisz, powiedz, co chcesz
powiedzieć, puść — i pojawia się to w oknie czatu gry, wpisane, a Twoje ręce nie
opuszczają kierownicy.

Wszystko inne w aplikacji z tego wyrosło. Inżynier, trener i czat głosowy dzielą
ten sam klawisz i to samo nagranie; czat tekstowy to, co dzieje się ze słowami,
gdy nic innego się o nie nie upomniało.

## Co dzieje się, gdy trzymasz klawisz

1. **Klawisz zostaje połknięty.** Gra nigdy nie widzi samego wyzwalacza, więc
   może to być klawisz, którego gra też używa.
2. **Nagrywanie startuje natychmiast** — zanim otworzy się okno czatu, nie po.
   Otwarcie zajmuje kilkaset milisekund i wszystko powiedziane w tym czasie
   przepadłoby.
3. **Wysyłane są klawisze czatu**, żeby otworzyć okno czatu gry, a aplikacja
   czeka `pre_delay_ms`, aż przejmie ono fokus.
4. **Puszczasz.** Nagrywanie się kończy, a klip trafia do Whispera, na Twoim
   własnym procesorze.
5. **Tekst zostaje wpisany**, a potem naciśnięte klawisze wysyłki.

Jeśli słowa okażą się poleceniem dla inżyniera albo trenera, to na nie pada
odpowiedź, a nic nie zostaje wpisane. Ta decyzja jest celowo wąska — zobacz
[Rozmowa z nim](engineer.md#mówienie-do-niego) — bo ten sam klawisz wysyła wiadomości
do wszystkich w sesji, a polecenie, które aplikacja sobie wymyśli, to wiadomość,
która po cichu nigdy nie dociera.

## Wyłączanie

**Czat tekstowy → Wysyłanie do gry** to przełącznik, po który sięgasz w środku
wyścigu, gdy sesja staje się publiczna. Wyłączony, wyzwalacz zostaje tylko głosem
i inżynierem: żadnych klawiszy czatu, żadnego pisania, nic nie wysłane.

Jest też drugi przełącznik, osobny dla każdej gry, w Profilach. „Czy ta gra ma
okno czatu” to fakt o grze, a nie decyzja podejmowana co sesję — Assetto Corsa
offline nie ma czatu do otwarcia, więc każde naciśnięcie wysyłało do gry Enter,
który znaczył tam coś innego. Ustaw raz i zapomnij. Przełącznik ogólny nadal
wygrywa: wyłączony tam znaczy wyłączony wszędzie.

## Sprawdzenie wiadomości, zanim pójdzie

Domyślnie wiadomość jest wysyłana, gdy tylko zostanie wpisana. Model mowy czasem
się przesłyszy, a w sesji publicznej pomyłka jest problemem wszystkich — dlatego
każdy profil ma przełącznik **Wysyłaj automatycznie**.

Gdy jest wyłączony, wiadomość zostaje wpisana w okno czatu i tam zostawiona. To
Twój wyzwalacz decyduje, co się z nią stanie, bez puszczania kierownicy:

| Gest | Co robi |
| --- | --- |
| **Stuknięcie** | Wysyła |
| **Dwa stuknięcia** | Kasuje |
| **Przytrzymanie** | Kasuje i nagrywa nową |

Karta Stan pokazuje **czeka na wysłanie**, dopóki wiadomość tam stoi.

Jeśli masz wolne przyciski, **Ustawienia → Wyzwalacz** przypisuje też klawisze
wprost do *Wyślij oczekującą wiadomość* i *Skasuj oczekującą wiadomość*. Działają
natychmiast, bez okna podwójnego stuknięcia, i współistnieją z gestami zamiast je
zastępować.

**Na stuknięcie nie można zareagować od razu**, bo dopóki okno podwójnego
stuknięcia się nie zamknie, może to być jego pierwsza połowa. To czekanie to
`review.double_tap_ms`, około jednej trzeciej sekundy. Ustaw `0` w konfiguracji,
żeby wysyłać natychmiast i zrezygnować z kasowania podwójnym stuknięciem.
`review.tap_ms` to granica między stuknięciem a przytrzymaniem.

**Naciśnięcie przy oczekującej wiadomości od razu zaczyna nagrywanie**, zanim
wiadomo, czy będzie to stuknięcie, czy przytrzymanie. Czekanie na rozstrzygnięcie
zjadłoby pierwsze słowa nowego nagrania; bufor jest wyrzucany, jeśli okaże się to
stuknięciem.

## Profile

O tym, który profil obowiązuje, decyduje program mający fokus, więc kilka
symulatorów może być skonfigurowanych naraz i właściwy zostanie użyty bez
pytania.

Ustawienie, które liczy się najbardziej, to **Opóźnienie otwarcia czatu**
(`pre_delay_ms`). Okno czatu potrzebuje kilku klatek, żeby się otworzyć i przejąć
fokus, a pisanie za wcześnie gubi pierwsze znaki. Zacznij od 350 ms i podnieś,
jeśli wiadomości docierają obcięte.

| Ustawienie | Do czego służy |
| --- | --- |
| **Opóźnienie otwarcia czatu** | Ile czekać po otwarciu czatu, zanim zacznie się pisać. To, które trzeba podnieść przy obciętych wiadomościach |
| **Klawisze otwarcia czatu** | Co otwiera czat. W większości symulatorów Enter |
| **Klawisze wysyłki** | Co ją wysyła. Zwykle znów Enter |
| **Klawisze anulowania** | Co zamyka okno bez wysyłania, do skasowania oczekującej wiadomości |
| **Przytrzymanie klawisza** | Jak długo trzymany jest każdy klawisz. Gry czytają wejście raz na klatkę, więc naciśnięcie krótsze niż klatka to naciśnięcie, którego gra nigdy nie widzi |
| **Opóźnienie pisania** | Odstęp między znakami |
| **Maksymalna liczba znaków** | Dłuższe wiadomości są ucinane. Większość symulatorów ma własny limit |
| **Wysyłaj automatycznie** | Wyłączone, by przejrzeć przed wysłaniem — zobacz wyżej |
| **Wtyczka sesji** | Czyta, kto jest w sesji, żeby nazwiska transkrybowały się poprawnie i stawały wzmiankami. Zostaw na *automatycznie* |

### Unicode czy skankody

**Tryb pisania** decyduje, jak znaki docierają do gry. *Unicode* wysyła sam znak
i radzi sobie z każdym układem klawiatury i każdym alfabetem. Niektóre gry to
ignorują, bo czytają zamiast tego sprzętowe skankody — dla nich przełącz na
*scancode*, który pisze tak, jakby klawisze wciśnięto fizycznie.

Skankody ograniczają się do tego, co potrafi wytworzyć klawiatura amerykańska,
więc znaki diakrytyczne i alfabety niełacińskie tego nie przetrwają. Spróbuj
najpierw unicode; to ustawienie istnieje, bo „gra ignoruje to, co piszemy”
musiało być zmianą konfiguracji, a nie zmianą kodu.

Oba mają też inne czasy i właśnie dlatego są osobnymi trybami. Klawisze w
skankodzie trzymane są `key_hold_ms`, bo gry czytają wejście raz na klatkę.
Pisany tekst nie — idzie przez kolejkę komunikatów, a 40 ms na znak sprawiłoby,
że wiadomość na 200 znaków trwałaby osiem sekund.

## Nazwiska i słownik

Model mowy zapisuje to, co słyszy, a nazwiska kierowców to dokładnie to, co
wychodzi mu najgorzej. Wtyczka sesji czyta, kto jest w Twojej sesji, i podaje te
nazwiska, więc „Estre” wychodzi jako „Estre”, a nie „Ester”.

**Słownik** dokłada do tego Twoje własne słowa: nazwy sponsorów, nazwę zespołu,
to, jak naprawdę pisze się ksywki znajomych. Wszystko, co przyłapujesz się na
poprawianiu, warto dodać.

## Nic się nie wpisuje

**Najpierw sprawdź kartę Stan.** Pokazuje, na co uzbrojony jest hak w tej chwili
i kiedy ostatnio widziano wyzwalacz. Jeśli *Ostatni wyzwalacz* nigdy się nie
aktualizuje, problemem jest klawisz albo hak, a nie transkrypcja.

**Musi działać jako administrator.** Windows odrzuca wstrzyknięte wejście
kierowane do procesu o wyższym poziomie integralności niż nadawca, a symulatory
często działają podniesione. Zainstalowana wersja prosi o to sama.

**Sprawdź, czy profil pasuje.** Karta Stan zapisuje nazwę programu na pierwszym
planie; jeśli nie ma go wśród Twoich profili, używany jest profil domyślny, a
jego klawisze czatu mogą nie pasować do tej gry.

**Sprawdź opóźnienie otwarcia czatu.** Wiadomości docierające bez pierwszych
znaków to za każdym razem zbyt niskie `pre_delay_ms`.

**Sprawdź, czy gra nie ignoruje unicode.** Jeśli okno czatu się otwiera, a nic
się w nim nie pojawia, spróbuj trybu pisania *scancode*.
