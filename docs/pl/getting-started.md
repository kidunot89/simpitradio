# Pierwsze kroki

Zainstaluj, powiedz, którego klawisza ma nasłuchiwać, i coś powiedz. Wszystko
inne na tych stronach jest opcjonalne.

![Okno SimPitRadio na karcie Stan](images/window.png)

## Instalacja

Pobierz instalator ze
[strony wydań](https://github.com/kidunot89/simpitradio/releases/latest) i uruchom
go. Windows ostrzeże: kompilacje nie są podpisane, więc SmartScreen pokazuje
„System Windows ochronił Twój komputer” i trzeba wybrać **Więcej informacji →
Uruchom mimo to**. Tak wygląda niepodpisany instalator, a podpis kosztuje
pieniądze, których ten projekt nie wydaje.

Instalator zadaje jedno pytanie — **jaki język** — z językiem Windows już
wybranym. Ustala to trzy rzeczy naraz: okno, rozpoznawanie mowy oraz język, w
którym inżynier wyścigowy mówi i słucha. Możesz to później zmienić na karcie
Język.

**Instaluje się jako administrator, i to celowo.** Windows odrzuca wstrzyknięte
naciśnięcia klawiszy kierowane do programu działającego z wyższymi uprawnieniami
niż nadawca, a symulatory często działają podniesione. Bez tego wszystko wygląda
na działające, a do gry nigdy nic nie dociera.

### Pierwsze uruchomienie pobiera dwie rzeczy

W instalatorze nie ma nic dużego, więc przy pierwszym otwarciu zostaniesz
poproszony o pobranie:

- **modelu mowy**, około 250 MB, który zamienia Twój głos w tekst
- **nagranego głosu** dla inżyniera, około 45 MB, jeśli jakiś jest opublikowany
  w Twoim języku

Obie rzeczy jednorazowo. Model leży poza katalogiem instalacji, więc
aktualizacja nigdy nie każe pobierać go ponownie. Jeśli powiesz „nie teraz”,
karty Język i Ustawienia zrobią to samo, kiedy zechcesz.

Wersja przenośna w zipie nie ma instalatora, a więc i pytania o język — zadaje
to samo przy pierwszym uruchomieniu.

## Wybierz klawisz

**Ustawienia → Wyzwalacz.** Naciśnij *Naciśnij klawisz…*, a potem ten, który
chcesz.

![Sekcja Wyzwalacz na karcie Ustawienia](images/trigger.png)

Klawisz jest **połykany po drodze**, więc gra nigdy go nie widzi — co oznacza, że
możesz użyć takiego, którego gra już używa. `F13` jest domyślny, bo większość
klawiatur go nie ma i nic innego go nie nasłuchuje.

**Przycisk kierownicy też działa.** Zmapuj go na klawisz klawiatury za pomocą
[JoyToKey](https://joytokey.net/) i przypisz ten klawisz tutaj. SimPitRadio nie
czyta kierownic bezpośrednio, a powód jest w
[notatkach inżyniera](engineer.md#ustawienia-per-symulator): wieniec Fanatec wyliczył 79
wejść i przez żadną z czterech różnych bibliotek ani razu nie zgłosił
naciśnięcia, a odczytanie Steam Controllera w ogóle oznaczało zabranie go
Steamowi.

## Ustaw mikrofon

**Dźwięk → Mikrofon.** Wybierz wejście, przytrzymaj wyzwalacz i patrz na pasek
poziomu — pokazuje sygnał *po* wzmocnieniu, czyli to, co Whisper naprawdę
dostaje. Celuj w szczyty w okolicach trzech czwartych.

![Karta Dźwięk](images/audio.png)

**Wyjście nie powinno być urządzeniem symulatora.** Inżynier, trener i sygnał
nagrywania odtwarzają się tutaj; skierowanie go na to samo wyjście, którego
używa gra, wpuszcza pisk do nagrania.

Naciśnij **Nagraj 4 s i przepisz**, żeby usłyszeć, co zostało zrozumiane. Podczas
testu nigdzie nic nie jest wpisywane.

## Powiedz coś

Przytrzymaj klawisz, powiedz, co chcesz powiedzieć, puść.

1. Klawisz zostaje połknięty.
2. Nagrywanie startuje **natychmiast** — zanim otworzy się okno czatu, żeby nic z
   pierwszych kilkuset milisekund nie przepadło.
3. Klawisze czatu otwierają okno czatu w grze.
4. Po puszczeniu klip trafia do Whispera, na Twoim własnym procesorze.
5. Tekst zostaje wpisany, a klawisze wysyłki naciśnięte.

Karta Stan pokazuje, na co uzbrojony jest hak i kiedy ostatnio widziano
wyzwalacz. Jeśli *Ostatni wyzwalacz* nigdy się nie aktualizuje, problemem jest
klawisz albo hak, a nie transkrypcja.

![Karta Stan](images/status.png)

## A potem, jeśli chcesz więcej

Nic z poniższych nie jest domyślnie włączone.

| | |
| --- | --- |
| [Czat tekstowy](text-chat.md) | Samo dyktowanie: profile, przegląd przed wysłaniem, co robić, gdy nic się nie wpisuje |
| [Inżynier](engineer.md) | Głos z imieniem, który czyta Twoje czasy okrążeń, zgłasza auta obok i odpowiada na pytania |
| [Trener](coaching.md) | Twój tor jazdy zestawiony z torem rywala po każdym zakręcie, wraz z tym, co zmienić |
| [Głos na radiu](voice-chat.md) | Słyszeć innych kierowców w sesji, i tylko tych blisko |
| [Pakiety głosowe](voicepacks.md) | Nagrać albo zainstalować głos, którym mówi inżynier |

## Kiedy coś jest nie tak

**Najpierw sprawdź kartę Stan.** To jedyne miejsce pokazujące, co aplikacja
uważa: uzbrojony klawisz, program na pierwszym planie, używany profil i dziennik
na żywo.

![Dziennik na karcie Stan](images/log.png)

- **Nic się nie wpisuje** — zobacz [Nic się nie wpisuje](text-chat.md#nic-się-nie-wpisuje).
- **Nic nie jest mówione** — zobacz [Nic nie jest mówione](engineer.md#nic-nie-zostaje-powiedziane).
- **Nic nie jest rysowane** — zobacz [Nic nie jest rysowane](coaching.md#nic-nie-jest-rysowane).

Dziennik zapisywany jest też do pliku. **Stan → Otwórz folder dzienników**
zaprowadzi Cię tam, i to pierwsza rzecz, którą warto dołączyć do zgłoszenia.
