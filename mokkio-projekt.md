# mokkio

Community- und Kursportal auf Discourse, selbst gehostet. Dieser Ordner ist der
Arbeitsplatz für Aufbau, Theme und Inhalte.

---

## Worum es geht

mokkio ist ein Portal für Prompts, KI-Tools und Kurse. Nutzer legen ein Konto an,
kostenlose Bereiche stehen allen offen, bezahlte Inhalte hängen an Gruppen.
Discourse liefert Login, Konten, Diskussionen, Kopier-Knopf für Codeblöcke und
Gruppenrechte ohne Eigenbau.

**Warum Discourse und nicht WordPress:** Login, Nutzerkonten und
Mitgliedschaftslogik sind fertig. Ein WordPress-Aufbau hätte drei bis vier
Plugins gebraucht, die zusammen gepflegt werden wollen.

### Abgrenzung zu den anderen Marken

| Marke | Domain | Rolle |
|---|---|---|
| mokkio | `app.mokkio.de` | Portal, Community, Kurse |
| Marcel Ehrhardt | `marcelehrhardt.de` | KI-Berater, persönliche Marke |
| Greatik | greatik-Domain | Agentur, Websites, SEO, Design |

Die drei sehen unterschiedlich aus. mokkio übernimmt das Volt-Designsystem,
Greatik behält sein eigenes Auftreten.

---

## Technischer Stand

**Server**
Hetzner CX23, Nürnberg, Ubuntu 24.04 LTS. Zugang per SSH-Key, kein
Passwort-Login. Discourse läuft über das offizielle `discourse_docker`-Setup.

**Domain und DNS**
`app.mokkio.de` mit A- und AAAA-Record. Die Wurzeldomain `mokkio.de` bleibt frei
für eine spätere Landingpage. SSL über Let's Encrypt.

**Mailversand**
Resend, Region Irland. SMTP über `smtp.resend.com`, Port 587, Benutzer `resend`.
Absenderadresse `noreply@mokkio.de`. SPF und DKIM sind gesetzt und verifiziert,
Testversand läuft.

**Zugang**
Die Instanz steht auf privat, neue Registrierungen brauchen Freigabe durch einen
Moderator. Das bleibt so, bis Struktur und Aussehen stehen.

**Theme**
mokkio ist installiert, hängt am Repo und ist als Standard gesetzt. Die alte von
Hand angelegte Palette ist gelöscht, es gilt nur noch die aus `about.json`.

---

## Designsystem

| Token | Hex | Verwendung |
|---|---|---|
| Ink | `#0B0D10` | Hintergrund |
| Frost | `#E6EAEF` | Text |
| Volt | `#C8FF38` | Akzent: Links, Primärknopf, aktive Zustände |
| Graphite | `#20242A` | Karten, Knöpfe, Eingabefelder |
| Graphite hell | `#30343A` | Kanten, Hover |
| Steel | `#747B84` | Sekundärtext, Zähler |

**Schriften**
Manrope in 700 für Überschriften, sonst nichts. IBM Plex Mono in 400, 500 und
600 für Oberfläche, Fließtext und Code. Sechs Dateien, zusammen 88 KB, selbst
gehostet als woff2 mit latin-Subset, keine Einbindung über Google Fonts.

Monospace läuft breiter als eine Proportionalschrift. Der Fließtext steht darum
auf 0.9375rem mit 1.7 Durchschuss und leicht negativer Laufweite.

**Volt-Regel**
Volt trägt die Links, genau einen gefüllten Knopf pro Ansicht, die Kante am
aktiven Sidebar-Eintrag und die Unterkante am aktiven Tab. Links tragen Volt
bewusst, damit sie als Links erkennbar sind. Flächen, Zähler und alle übrigen
Knöpfe bleiben Graphite oder Steel. Discourse färbt von Haus aus zu viel in der
Tertiärfarbe, das korrigiert das Theme-CSS.

Discourse setzt außerdem einige Hover- und Auswahlflächen als feste helle Werte,
`#f2f2f2` und `#d1f0ff`, die nicht aus der Palette kommen. Auf einem dunklen
Theme wird der Text darauf unlesbar. Abschnitt 9 im Stylesheet biegt sie um.

---

## Theme-Repository

`github.com/c0dem0re/mokkio`, privat, Branch `main`. Discourse zieht über SSH
mit einem Deploy-Key, der nur Lesezugriff hat. Diese Projektdatei liegt seit dem
Umzug mit im Repo, damit Doku und Code denselben Stand teilen.

    about.json           Metadaten, Schrift-Assets, Farbpalette mokkio
    common/common.scss   Hauptstylesheet, neun Abschnitte
    common/head_tag.html
    mobile/mobile.scss   Mobil-Anpassungen
    settings.yml         Theme-Einstellungen
    assets/fonts/        sechs woff2-Dateien
    mokkio-projekt.md    diese Datei

**Ablauf bei Änderungen:** im Repo arbeiten, pushen, im Discourse-Admin unter
Erscheinungsbild → Themes & Komponenten → mokkio auf "Nach Updates suchen"
klicken.

**Theme-Einstellungen.** `settings.yml` erzeugt Schalter im Admin. Discourse
liefert die Werte im Stylesheet als unquoted string, nicht als Boolean. Ein
`@if $setting` ist deshalb immer wahr, auch bei "false". Es muss
`@if $setting == "true"` heißen.

**Regel:** Farben und CSS gehören ins Repo. Wer im Admin-Interface an der Palette
schraubt, erzeugt eine zweite Wahrheit und weiß in vier Wochen nicht mehr,
welche greift.

---

## Was als Nächstes ansteht

1. **Fließtext-Helligkeit entscheiden.** Frost steht mit 16,1:1 auf Ink. Das ist
   Kontrast am oberen Anschlag und liest sich hart. Vorschlag: Fließtext auf
   `#C9D1DA` bei 12,6:1 abdunkeln, Überschriften auf Frost lassen. Das gäbe eine
   Hierarchie, die bisher fehlt. Noch nicht entschieden.
2. **Kategoriestruktur** aufbauen. Welche Kurse, welche Prompt-Bereiche, was frei
   und was bezahlt ist. Die Farben setzt man pro Kategorie im Admin, nicht im
   CSS. Vorschlag: alle Kategorien in Steel, bezahlte Bereiche in Volt, dann
   trägt die Farbe eine Bedeutung.
3. **Startthemen aufräumen.** Die drei Beiträge von `@system` sind
   Standardtexte mit Discourse-Logo als Avatar. Vor den ersten echten Nutzern
   umschreiben oder löschen, Avatar tauschen.

---

## Offene Entscheidungen

**Videohosting.** Für bezahlte Inhalte gehören die Videos nicht auf YouTube.
Bunny Stream steht als Vorschlag im Raum, kostet wenige Euro im Monat und liefert
signierte Links, die außerhalb der Community nicht funktionieren. Noch nicht
entschieden.

**Bezahlung.** Discourse koppelt Gruppen an Stripe. Marcel arbeitet sonst mit
Fastbill, Paddle und Lemon Squeezy. Ob Stripe dazukommt oder ein anderer Weg
passt, ist offen.

**n8n.** Die selbst gehostete Instanz hängt noch nicht dran. Sinnvoll wird das
beim Befüllen und bei der Anbindung an ActiveCampaign, also nachdem die Struktur
steht.

---

## Arbeitsweise

**Server-Befehle** laufen über SSH vom Windows-Rechner oder aus Claude Code.
Befehle vorbereiten, Ausgabe zurückgeben, gemeinsam auswerten.

**Theme-Arbeit** läuft über Claude Code im Repository. Kein Copy-Paste ins
Admin-Interface.

**Texte** folgen den Schreibregeln aus den persönlichen Einstellungen. Kein
Marketing-Ton, kein "einfach", keine Gedankenstriche als Satztrenner. Konkret vor
abstrakt, Zahlen vor Adjektiven.

---

## Nicht in dieser Datei

Zugangsdaten, API-Schlüssel, SMTP-Passwörter und der Root-Zugang gehören in den
Passwortmanager, nicht in ein Repository oder eine Notizdatei.
