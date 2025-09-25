Godmod

Godmod — przenośne, niskokosztowe urządzenie do pozyskiwania, konfiguracji i transmisji obrazu i dźwięku z kamer (np. GoPro). Projekt łączy jednopłytkowy komputer Radxa Zero 3W, dotykowy panel sterowania i autorską aplikację Pelabox. Godmod wystawia UVC (webcam) — dzięki temu Pelabox może przechwycić obraz i dźwięk jako urządzenie webcam, enkodować do HEVC i wysyłać przez SRT.

> Projekt powstał z pasji do transmisji na żywo i pracy z wideo w czasie rzeczywistym — celem jest stworzenie elastycznego, otwartego i przystępnego narzędzia, które każdy będzie mógł zbudować i rozwinąć.







---

Czym jest Godmod

Godmod to urządzenie typu "bridge" między kamerą (np. GoPro) a światem streamingu: ułatwia konfigurację parametrów kamery, wystawia sygnał jako UVC (webcam) oraz umożliwia lokalne enkodowanie i wysyłkę strumienia przez SRT za pomocą aplikacji Pelabox. Jego zaletą jest niska cena, mobilność i możliwość łatwej rozbudowy przez społeczność.

Najważniejsze cechy

Wystawianie UVC (webcam) z podłączonej kamery — prosty odczyt w systemie.

Pełna kontrola ustawień kamery (soczewka, rozdzielczość, FPS, bitrate, Protune itd.).

Obsługa zarówno UVC (webcam) jak i HDMI (passthrough / wejście zależnie od konfiguracji).

Integracja z Pelabox — enkodowanie HEVC i wysyłka przez SRT.

Obsługa zewnętrznych mikrofonów USB / dongli bezprzewodowych.

Minimalna liczba kabli dzięki USB-C z PD passthrough (zasila + przesyła dane).


Sprzęt (rekomendowany)

Radxa Zero 3W — preferowana konfiguracja: 4 GB RAM + 32 GB eMMC (wersja 8GB/64GB możliwa przy dostępności/promocji).

Ekran IPS dotykowy (kompaktowy) — interfejs wyboru ustawień.

2× USB-C z PD passthrough: jeden dedykowany do kamery, drugi opcjonalnie do telefonu/komputera.

Port HDMI (wejście/wyjście w zależności od trybu).

USB-C host dla akcesoriów (mikrofony bezprzewodowe, dongle itp.).

Kable: USB-C PD passthrough, krótkie kable USB-C/USB-A, adaptery HDMI w razie potrzeby.


Oprogramowanie i komponenty

System: firmaware godmod.

GoPro Open API — do zdalnej konfiguracji parametrów kamery (przełączanie trybów, ustawienia soczewki, itp.).

Pelabox — autorska aplikacja enkodera (przechwytywanie UVC, enkodowanie HEVC, SRT transport).

FFmpeg / GStreamer — narzędzia pomocnicze do transformacji, testów i relay.


Ustawienia kamery dostępne w GUI

Godmod daje użytkownikowi możliwość wyboru (przykładowe ustawienia):

Soczewka / FOV: Wide / Linear / Narrow / SuperView (w zależności od modelu).

Rozdzielczość: 1080p / 1440p / 2.7K / 4K (gdzie dostępne).

FPS: 24 / 30 / 50 / 60 / 120 (gdzie dostępne).

Bitrate: stały lub adaptacyjny (konfigurowalny w kbps).

Protune / profile: Standard / Flat, ustawienia kolorów, ISO limit, balans bieli.

Ekspozycja / shutter / EV: kontrola ekspozycji.

Stabilizacja: On / Off (jeżeli kamera obsługuje).

Audio: źródło audio (wewnętrzny mikrofon GoPro / zewnętrzny mikrofon USB przez Godmod), poziomy/gain.

Tryb transmisji: UVC (Webcam) lub HDMI passthrough.

Dodatkowo: timestamp overlay, nagrywanie lokalne obok streamu, automatyczne profile.


> Wszystkie ustawienia mogą być przesyłane do kamery przez GoPro Open API oraz zapisywane jako profile na urządzeniu.



Zasada działania (flow danych)

1. Kamera (GoPro) podłączona do portu USB-C PD passthrough w Godmod.


2. Godmod (Radxa) komunikuje się z kamerą przez GoPro Open API i konfiguruje parametry.


3. Godmod wystawia sygnał jako UVC (video + audio) lub przekierowuje sygnał przez HDMI w zależności od trybu.


4. Pelabox przechwytuje UVC jako urządzenie webcam (np. /dev/videoX) oraz audio USB.


5. Pelabox enkoduje sygnał do HEVC i wysyła go przez SRT na serwer docelowy.


6. Opcjonalnie: lokalny podgląd przez HDMI i/lub nagrywanie lokalne.






Przykładowe zastosowania

Streaming IRL (vlogi, relacje z wydarzeń).

Monitoring tymczasowy / mobilny (wydarzenia, budowy, konferencje).

Produkcje wideo DIY i reżyserskie (podgląd dla reżysera).

Edukacja i laboratoria (kodeki, SRT, real-time media).

Prototypowanie systemów vision / AI w czasie rzeczywistym.


Schemat połączeń (ASCII)

Powerbank --> PD passthrough hub --> Godmod (Radxa)
                                      |-- USB-C (to GoPro) (data + PD)
                                      |-- USB-C host (mikrofon bezprzewodowy)
                                      |-- HDMI out (monitor / podglad)
                                      |-- Ekran dotykowy (GUI)

Godmod (Radxa) -- Pelabox (process) -> enkodowane HEVC -> SRT -> Server







