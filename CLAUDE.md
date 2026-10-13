# Dom – notatki dla Claude

Ten plik Claude Code czyta na starcie każdej rozmowy. Dopisuj tu rzeczy, które mają być pamiętane na stałe.

## Jak rozmawiać
- Zawsze po polsku, krótko i konkretnie.
- Przed usuwaniem czegokolwiek (encje, automatyzacje, dashboardy, dodatki) – pokaż listę i poczekaj na OK.

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

## To repozytorium
- `panel.yaml` – konfiguracja ESPHome panelu Waveshare.
