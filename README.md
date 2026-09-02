# mokkio Theme

Discourse-Theme für app.mokkio.de. Farben, Schriften und Layout aus dem
mokkio-Designsystem.

## Farben

| Token     | Hex       | Verwendung                    |
|-----------|-----------|-------------------------------|
| Ink       | `#0B0D10` | Hintergrund                   |
| Frost     | `#E6EAEF` | Überschriften, Oberfläche     |
| Frost dim | `#C9D1DA` | Fließtext im Beitrag          |
| Volt      | `#C8FF38` | Links, Primärknopf, Aktives   |
| Graphite  | `#20242A` | Karten, Knöpfe, Eingabefelder |
| Steel     | `#747B84` | Sekundärtext, Zähler          |

## Schriften

Manrope 700 für Überschriften. IBM Plex Mono 400/500/600 für Oberfläche,
Fließtext und Code. Dateien liegen unter `assets/fonts/`.

## Struktur

    about.json          Metadaten, Assets, Farbpalette
    common/common.scss  Hauptstylesheet
    common/head_tag.html
    mobile/mobile.scss  Mobil-Anpassungen
    settings.yml        Theme-Einstellungen
    assets/fonts/       woff2-Dateien

## In Discourse einbinden

Admin → Anpassen → Themes → Installieren → Aus einem Git-Repository.
URL des Repos eintragen, Branch `main`.

Nach jedem Push: Theme öffnen, auf "Aktualisieren" klicken.
