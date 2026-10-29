# Dom – notatki dla Claude

Ten plik Claude Code czyta na starcie każdej rozmowy. Dopisuj tu rzeczy, które mają być pamiętane na stałe.

## Jak rozmawiać
- Zawsze po polsku, krótko i konkretnie.
- Przed usuwaniem czegokolwiek (encje, automatyzacje, dashboardy, dodatki) – pokaż listę i poczekaj na OK.

## Zapisywanie pamięci (rób to sam, bez pytania)
- Po zakończeniu każdej konkretnej rzeczy (nowa/zmieniona automatyzacja, dashboard, urządzenie, naprawa, ważna decyzja) dopisz **jedną linijkę** w sekcji „Historia wcześniejszych rozmów”: data + co zrobiono + nazwy encji/dashboardów, jeśli ważne.
- Nowe stałe fakty (nowe urządzenie, zmiana IP, nowy dodatek, preferencja) wpisz w odpowiednią sekcję wyżej.
- Zapisz commitem i wypchnij od razu na `main` (`git pull --rebase origin main`, commit, `git push origin HEAD:main`). Nie twórz PR do tego pliku.
- Nigdy nie zapisuj tu haseł, tokenów, loginów ani kluczy – wpisz tylko, gdzie są (np. „dane IPTV w input_text w HA”).
- Plik ma być krótki: gdy historia przekroczy ~40 linijek, połącz najstarsze wpisy w zwięzłe podsumowania miesięczne.

## Home Assistant
- Home Assistant OS na komputerze x86 (`generic-x86-64`), IP w sieci domowej: `192.168.0.153`, strefa czasowa Europe/Warsaw, język PL.
- Sterowanie z Claude: złącze **Home Assistant MCP** (działa z chmury, dostęp z zewnątrz przez Cloudflared / Duck DNS).
- Dodatki: ESPHome Device Builder, Frigate (Full Access), Mosquitto (MQTT), Music Assistant, Spotify Connect, Whisper + Piper (głos), HyperHDR, Samba, File editor, Terminal & SSH, Advanced SSH, Cloudflared, Duck DNS, SomfyProtect2MQTT, Home Assistant MCP Server.
- HACS zainstalowany (m.in. Mushroom, Advanced Camera Card, Xiaomi Miot, SpotifyPlus, Sonoff).
- Dashboardy w trybie storage (UI) – jest ich dużo (~50), część to stare testy.

## Strefy / pomieszczenia
Salon, kuchnia, sypialnia, przedpokój, łazienka, toaleta, piętro, pokój dzieci, ganek, wjazd, garaż, ogród (domek), balkon, warsztat.

## Ważne urządzenia
- **Kamery**: Kamera Wjazd (Frigate, rozpoznawanie twarzy i tablic rej.), Kamera ganek, Kamera domek / Ogród Domek, Kamera Somfy garaż, dzwonek do drzwi.
- **Brama wjazdowa i garażowa** – automatyzacje z powiadomieniem na telefon (zdjęcie + przycisk „Otwórz”), lista domowników (twarze, tablice).
- **Alarm**: Somfy Home Alarm.
- **Panele/ekrany**: Panel 1 – Brama i Pogoda, Panel Salon (ESPHome, Waveshare), tablet rk3566 w łazience (dashboard „Kiosk Gold”, url `kiosk-gold-test`).
- **Media**: TV Sony BRAVIA XR-75X90J, Philips TV (Ambilight), Radio – Łazienka, Spotify.
- **Lampa łazienka dół**: Yeelight ceiling4 (`light.yeelink_ceiling4_2d35_main_light`, `..._ambient_light`), tryb nocny = `yeelight.set_mode` moonlight.
- **Inne**: robot odkurzający, kosiarka, klimatyzacja (garaż, pokój Milenki), oświetlenie ganek/przedpokój/domek na czujnikach ruchu.
- **Ogrzewanie podłogowe (łazienka)**: panel Warmtec (oprogramowanie Beca, stara aplikacja WARMTEC wycofana), IP 192.168.0.34, MAC cc:50:e3:4c:b9:e0 (ESP) – **nie jest w HA**, Tuya go nie widzi.
- Tablet rk3566 (Kiosk Gold): kamery tylko jako zdjęcia co ~10 s (`camera_view: auto`) – tryb `live` mocno zamulał tablet, nie włączać.
- Telefon: Samsung SM-S928B (powiadomienia `notify`).

## Komputer
- Laptop Dell z Windows i Chrome (rozszerzenie Claude in Chrome). Rozmowy „lokalne” w aplikacji Claude działają na nim; rozmowy w chmurze nie mają do niego dostępu.
- Jak przejść na pracę lokalną: aplikacja Claude na laptopie → zakładka **Code** → nowa sesja, środowisko **Lokalnie / Local** (nie Cloud) i wybrany folder. Sesja w chmurze sama się nie przełączy – trzeba zacząć nową.

## Historia wcześniejszych rozmów (skrót)
- **wrz 2026** – podłączenie Home Assistant MCP do Claude; naprawa czujników Aqara (xiaomi_miot, 4/5 odzyskane; Tuya Local zainstalowane, nieskonfigurowane); polskie stacje radiowe w Music Assistant; dashboard „Dom” (17 stref, kamery, media, Kiosk Mode).
- **1 paź** – sprawdzenie sieci i HA.
- **3 paź** – tablet w łazience (rk3566): panel startowy „Kiosk Gold”, kafle responsywne (% ekranu + minimum px).
- **7–9 paź** – IPTV: listy M3U dla dekoderów Zgemma, skrypt „IPTV: Pobierz i przefiltruj listę” (tylko polskie kanały), plik do pobrania w dashboardzie Media (blok „IPTV – download only”); dane dostawcy trzymane w pomocnikach `input_text` w HA.
- **8–9 paź** – automatyzacja drzwi przesuwnych.
- **9 paź** – dashboard `kiosk-gold-test`: kamery 57% wysokości, Wjazd na `camera.kamera_wjazd`.
- **9–10 paź** – światło ganek/przedpokój/domek na czujnikach ruchu; ganek włączał się, gdy słońce było 6° pod horyzontem (od 29 paź bez tego warunku).
- **10 paź** – brama: lista „Ostatnie zdarzenia przy bramie” jako oś czasu z kolorowymi ikonami (panel); problem z przeładowaniem HA (Docker na hoście, pomógł restart zasilania).
- **13 paź** – porządki: złącza Claude (działają Gmail, GitHub, Spotify, Home Assistant MCP), pamięć w ustawieniach włączona, stare rozmowy zarchiwizowane, ten plik.
- **13 paź** – wzór wniosku urlopowego (PDF A4, `wydruki/wniosek_urlopowy.pdf` na gałęzi `ccr-8ed45c88-cs2lg3`); drukarki Epson brak w HA – z chmury drukować się nie da (opcja: e-mail Epson Connect).
- **14 paź** – panel ogrzewania podłogowego Warmtec: nie da się dodać przez Tuya (firmware Beca); opcje: aplikacja My BecaSmart, ESPHome na module ESP albo wymiana sterownika na wersję Tuya.
- **14 paź** – Kiosk Gold (`kiosk-gold-test`): kafel Kosiarka zastąpiony kaflem lampy łazienkowej (`light.yeelink_ceiling4_2d35_main_light` + Ambilight; jasność/barwa + przyciski Jasno/Ciepło/Noc przez skrypt `script.lampa_lazienka_tryb`); potem 2. wiersz „Góra” = Ambilight (jasność + kolor). Automatyka „po wejściu 30%” jest w aplikacji Yeelight, nie w HA.
- **14 paź** – Kiosk Gold: kafel Klima Garaż → „Światła w domu” (grupa `light.swiatla_dom`, licznik + strefy + „Wyłącz wszystkie”); kafel odkurzacza z baterią, ostatnim sprzątaniem i czasem (pomocniki `input_datetime.odkurzacz_*`, `input_number.odkurzacz_czas_ostatniego_sprzatania`, automatyzacja „Odkurzacz – zapisz ostatnie sprzątanie”).
- **14 paź** – Kiosk Gold ucinał dół o ~1 cm: kamery zmniejszone do `calc(100vh - 552px)` (było 512px), nowe kafle zablokowane na 17vh.

- **29 paź** – Kiosk Gold: z kafla Brama Garaż usunięta temperatura/wilgotność garażu (nachodziła na „od X h”). Kafel Kamera ganek (`camera.chuangmi_ipc020_5503_camera_control`, Xiaomi z chmury) pokazuje tylko miniaturę ostatniego nagrania ruchu z Mi Cloud, nie obraz na żywo – stało od 05:54.
- **29 paź** – Kiosk Gold: temperatura garażu wróciła na kafel Brama Garaż (sama °C, prawy górny róg); kafel Piec Garaż → nazwa „Piec”, opis = sama temperatura (stan pokazuje przełącznik).
- **29 paź** – światło ganek (czujniki ganek wejście + schody, gasi gdy oba bez ruchu; bez warunku słońca) i przedpokój osobno; zamknięcie drzwi przesuwnych od razu gasi ganek: zapalanie 7:00–22:30, gaszenie po 5 min do 18:00 / 2 min po 18:00; po restarcie HA / przeładowaniu automatyzacji gaszą światło przy braku ruchu (wcześniej edycja automatyzacji zostawiała ganek zapalony).
- **29 paź** – ganek: tryb ręczny pod przycisk Xiaomi/Aqara (ZHA, jeszcze niesparowany): `input_boolean.ganek_tryb_reczny_przycisk`, skrypt `script.ganek_przycisk_reczny` (7:00–22:30 = zgaś i blokada automatyki do północy, po 22:30 = świeci do północy, 2. wciśnięcie = powrót do automatyki), automatyzacja "Ganek - koniec trybu ręcznego" (00:00 i 7:00). Po sparowaniu przycisku dodać automatyzację: wciśnięcie → skrypt.

## To repozytorium
- `panel.yaml` – konfiguracja ESPHome panelu Waveshare.
