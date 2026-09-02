# Schriftdateien

Hier gehören sechs Dateien rein, jeweils als woff2 mit latin-Subset:

Manrope trägt nur die Überschriften:

- Manrope-Regular.woff2     (400)
- Manrope-SemiBold.woff2    (600)
- Manrope-Bold.woff2        (700)

IBM Plex Mono trägt Oberfläche, Fließtext und Code:

- IBMPlexMono-Regular.woff2  (400)
- IBMPlexMono-Medium.woff2   (500)
- IBMPlexMono-SemiBold.woff2 (600, Fettsatz im Fließtext)

Die Namen müssen exakt so lauten, sonst findet about.json sie nicht.
Fehlt eine Datei, bricht die Theme-Kompilierung in Discourse ab.

Falls du IBMPlexMono-Medium nicht brauchst: den Eintrag aus about.json
und den zugehörigen @font-face-Block aus common/common.scss entfernen.
