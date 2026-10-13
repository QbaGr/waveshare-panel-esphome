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
- **Panele/ekrany**: Panel 1 – Brama i Pogoda, Panel Salon (ESPHome, Waveshare), tablet rk3566 w łazience (dashboard „Kiosk Gold”).
- **Media**: TV Sony BRAVIA XR-75X90J, Philips TV (Ambilight), Radio – Łazienka, Spotify.
- **Inne**: robot odkurzający, kosiarka, klimatyzacja (garaż, pokój Milenki), oświetlenie ganek/przedpokój/domek na czujnikach ruchu.
- Telefon: Samsung SM-S928B (powiadomienia `notify`).

## Komputer
- Laptop Dell z Windows i Chrome (rozszerzenie Claude in Chrome). Rozmowy „lokalne” w aplikacji Claude działają na nim; rozmowy w chmurze nie mają do niego dostępu.

## Historia wcześniejszych rozmów (skrót)
- **wrz 2026** – podłączenie Home Assistant MCP do Claude; naprawa czujników Aqara (xiaomi_miot, 4/5 odzyskane; Tuya Local zainstalowane, nieskonfigurowane); polskie stacje radiowe w Music Assistant; dashboard „Dom” (17 stref, kamery, media, Kiosk Mode).
- **1 paź** – sprawdzenie sieci i HA.
- **3 paź** – tablet w łazience (rk3566): panel startowy „Kiosk Gold”, kafle responsywne (% ekranu + minimum px).
- **7–9 paź** – IPTV: listy M3U dla dekoderów Zgemma, skrypt „IPTV: Pobierz i przefiltruj listę” (tylko polskie kanały), plik do pobrania w dashboardzie Media (blok „IPTV – download only”); dane dostawcy trzymane w pomocnikach `input_text` w HA.
- **8–9 paź** – automatyzacja drzwi przesuwnych.
- **9 paź** – dashboard `kiosk-gold-test`: kamery 57% wysokości, Wjazd na `camera.kamera_wjazd`.
- **9–10 paź** – światło ganek/przedpokój/domek na czujnikach ruchu; ganek włącza się dopiero, gdy słońce jest 6° pod horyzontem.
- **10 paź** – brama: lista „Ostatnie zdarzenia przy bramie” jako oś czasu z kolorowymi ikonami (panel); problem z przeładowaniem HA (Docker na hoście, pomógł restart zasilania).
- **13 paź** – porządki: złącza Claude (działają Gmail, GitHub, Spotify, Home Assistant MCP), pamięć w ustawieniach włączona, stare rozmowy zarchiwizowane, ten plik.

## To repozytorium
- `panel.yaml` – konfiguracja ESPHome panelu Waveshare.
