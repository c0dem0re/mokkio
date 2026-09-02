# Struktur, Zugriff und Bezahlung

Entwurf für den Aufbau von app.mokkio.de. Grundlage ist das alte Portal unter
`portal.greatik.de`, dessen Inhaltsmodell hier nach Discourse übersetzt wird.

---

## Was aus dem alten Portal kommt

| Bereich | Umfang | Zugang bisher |
|---|---|---|
| KI-Tools | 28 Tools, Preisvergleich, Bewertungen | Beschreibungen frei, Deep-Dives PRO |
| Prompts | Copy-Paste-Bibliothek, Platzhalter-System | teils frei, teils PRO |
| Tutorials | 10+ Videos unter 15 Minuten | PRO |
| Video-Kurse | 6 Kurse mit Lektionen und Übungen | PRO |
| Blog und Guides | Artikel zu Trends und Strategien | frei |
| KI-Glossar | 45+ Begriffe in 5 Kategorien | frei |

Preise: FREE 0 Euro, PRO 19 Euro im Monat.

---

## Was Discourse davon kann und was nicht

Bevor die Struktur steht, gehört auf den Tisch, was ein Forum nicht leistet.

**Trägt Discourse gut**

Prompts. Der Kopier-Knopf an Codeblöcken ist eingebaut, Kommentare hängen direkt
am Prompt, Tags ersetzen die Filter. Das wird im Forum besser als im alten
Portal, weil Nutzer eigene Varianten darunter posten können.

Blog, Guides, Tutorials. Ein Beitrag mit eingebettetem Video und Text darunter
funktioniert. Diskussion inklusive.

Community. Fragen, Austausch, Feedback. Das hatte das alte Portal gar nicht.

**Trägt Discourse nicht**

Fortschritts-Tracking. Es gibt keine Anzeige, welche Lektion abgeschlossen ist.
Discourse merkt sich Gelesen und Ungelesen, mehr nicht. Das Plugin
`discourse-checklist` erlaubt Kästchen zum Abhaken in Beiträgen, das muss
geprüft werden, ist aber selbst gesetzt und nicht auswertbar.

Zertifikate. Gibt es nicht, in keiner Form.

Filterbare Tool-Datenbank. 28 Tools mit Preisvergleich und Kategorie-Filter sind
in einem Forum eine Themenliste mit Tags. Weniger komfortabel als vorher.

Glossar von A bis Z. Die Themenliste sortiert nach Aktivität, nicht nach
Alphabet. Ein Register-Beitrag muss das auffangen, siehe unten.

**Entschieden am 02.09.2026: alles geht nach Discourse.** Fortschritt und
Zertifikate werden nicht gebraucht. Das Vorbild ist Skool und Circle, also
Community und Kurse in einem Werkzeug, ohne Lernplattform-Beiwerk. Die beiden
Lücken oben sind damit keine Lücken mehr, sondern gestrichener Umfang.

Was bleibt, ist die Tool-Datenbank. 28 Tools mit Preisvergleich werden im Forum
unbequemer als im alten Portal. Das ist der Preis für eine Plattform statt
zwei.

---

## Zugriffsmodell

Die Instanz steht auf privat, jeder Inhalt braucht ein Konto. Frei heißt hier
also frei nach Anmeldung, nicht öffentlich lesbar.

Zwei Gruppen reichen:

| Gruppe | Wer | Wofür |
|---|---|---|
| `trust_level_0` | jedes registrierte Konto | freie Bereiche |
| `pro` | zahlende Abonnenten | bezahlte Bereiche |

Mehr Stufen erst, wenn es einen Grund gibt. Jede zusätzliche Gruppe verdoppelt
die Rechtematrix.

**Wichtig zur Sichtbarkeit.** Discourse kennt nur Sehen, Antworten, Erstellen.
Es gibt kein Anlesen. Eine PRO-Kategorie ist für Nichtzahler entweder ganz
sichtbar oder gar nicht vorhanden. Werbung für PRO läuft deshalb über einen
freien Beitrag und die Abo-Seite, nicht über halb sichtbare Inhalte.

---

## Kategorien

Acht oben, PRO jeweils als Unterkategorie darunter. Wenige Kategorien und viele
Tags tragen besser als das Gegenteil, weil leere Kategorien tot wirken.

| Kategorie | Sehen | Antworten | Erstellen |
|---|---|---|---|
| Start | alle | niemand | Team |
| Prompts | alle | alle | Team |
| ‣ Prompt-Bibliothek PRO | `pro` | `pro` | Team |
| KI-Tools | alle | alle | Team |
| ‣ Tool Deep-Dives | `pro` | `pro` | Team |
| Tutorials | alle | alle | Team |
| ‣ Tutorials PRO | `pro` | `pro` | Team |
| Kurse | `pro` | `pro` | Team |
| Glossar | alle | alle | Team |
| Blog und Trends | alle | alle | Team |
| Fragen und Austausch | alle | alle | alle |
| ‣ PRO-Lounge | `pro` | `pro` | `pro` |

**Farbregel.** Alle Kategorien in Steel `#747B84`, die bezahlten in Volt
`#C8FF38`. Dann trägt die Farbe eine Bedeutung und man sieht auf der
Kategorieseite sofort, wo die Grenze läuft. Die Farbe wird pro Kategorie im
Admin gesetzt, nicht im CSS.

**Zu den bestehenden Kategorien.** `Allgemein` geht in `Start` auf,
`Website-Feedback` bleibt, `Team` bleibt als Staff-Bereich.

**Kurse.** Sechs Unterkategorien für sechs Kurse wären zu viel Gerüst. Statt
dessen eine Kategorie `Kurse` und darin je Kurs:

- ein angehefteter Lehrplan-Beitrag, der alle Lektionen in Reihenfolge verlinkt
- ein Thema je Lektion, Titel mit vorangestellter Nummer, etwa
  `03 · Prompts strukturieren`
- ein Tag je Kurs, etwa `kurs-prompting`, an allen Themen des Kurses

Der Lehrplan-Beitrag ist die Kursseite. Er trägt Beschreibung, Dauer,
Voraussetzungen und die Lektionsliste. Über den Tag kommt man von jeder Lektion
zurück zum ganzen Kurs.

Eine Lektion besteht aus eingebettetem Video, den Kernpunkten als Text, der
Übung und den Kommentaren darunter. Der Textteil ist keine Zugabe: Er macht die
Lektion durchsuchbar, Video allein findet die Suche nicht.

Anders als bei Skool gibt es keinen Kurs-Reiter mit Kacheln und keine Anzeige,
wie weit jemand ist. Der Lehrplan-Beitrag übernimmt beides, angeheftet und
verlinkt.

---

## Glossar

45 Begriffe aus dem alten Portal, in fünf Kategorien: Grundbegriffe,
Prompt-Wissen, KI-Modelle und Tools, Technik, Automatisierung.

**Ein Thema je Begriff**, nicht fünf Sammelbeiträge. Der Grund liegt darin, was
Discourse mit einem Thema kann und mit einem Absatz nicht: Ein Begriff ist
verlinkbar, und ein eingefügter Link zeigt eine Vorschaukarte mit der
Definition. Er ist über den Titel auffindbar. Und unter ihm kann jemand
nachfragen, was in einem Sammelbeitrag nicht geht.

**Titel: Begriff, Mittelpunkt, Kurzdefinition.**

    Token · die Einheit, in der KI Text zählt

Der Begriff steht vorn, damit die Liste alphabetisch lesbar bleibt. Die
Kurzdefinition macht die Themenliste selbsterklärend. Nebenbei löst das die
Mindestlänge von 15 Zeichen für Titel, an der ein blankes `API` scheitern
würde.

**Aufbau des Beitrags**, gleich für jeden Begriff:

    **Kurz gesagt.** Ein Satz, der reicht, wenn man nur den kennen will.

    Zwei bis vier Sätze Erklärung, bei Bedarf mit Codeblock.

    **Im Alltag.** Wofür man das praktisch braucht.

    **Verwandt:** zwei bis drei andere Begriffe

**Ein Tag je Kategorie**, also `grundbegriffe`, `prompt-wissen`, `ki-modelle`,
`technik`, `automatisierung`. Ersetzt den Kategorie-Filter des alten Portals.

### Produkte gehören nicht ins Glossar

Von den 45 Einträgen sind 13 keine Begriffe, sondern Produkte: ChatGPT, Claude,
Copilot, DALL-E, GPT-4o, Gemini, Midjourney, Perplexity, Wispr Flow, Make, n8n,
Zapier, Stable Diffusion.

Die gehören nach `KI-Tools`, wo ohnehin Steckbriefe mit Preis und Bewertung
geplant sind. Sonst steht ChatGPT zweimal im Portal und altert an zwei Stellen
unterschiedlich. Es bleiben 32 echte Begriffe im Glossar.

Der Unterschied ist nicht formal. Ein Begriff wie Token oder Halluzination gilt
in fünf Jahren noch. Ein Produkteintrag ist eine Momentaufnahme und braucht
Pflege. Die beiden in einer Kategorie zu mischen heißt, alles wie das
Kurzlebigste behandeln zu müssen.

### Keine Versionsnummern

Auch in den verbleibenden Begriffen: keine Modellnamen, keine Versionen, kein
„aktuell" und kein „neueste". Der Eintrag `Multimodal` erklärt sich ohne den
Zusatz, welches Modell das gerade kann.

### Alphabetisch sortieren, der Umweg

Am 02.09.2026 an der laufenden Instanz getestet.

`sort_order: title` nimmt Discourse an, aber nur absteigend. Aufsteigend fällt
still auf die Standardsortierung zurück, sowohl als Kategorie-Einstellung als
auch als `?order=title&ascending=true` in der Adresse. Sortierung nach Titel
ist auf Meta seit Jahren ein Wunsch, keine Zusage.

`sort_order: created` mit `sort_ascending: true` wird dagegen sauber
umgesetzt. Damit gilt: Ist die Erstellungsreihenfolge alphabetisch, ist die
Liste alphabetisch.

Deshalb tragen alle 32 Begriffe gesetzte Zeitstempel, beginnend am 01.09.2026
um 08:00 Uhr, je Begriff eine Minute in alphabetischer Reihenfolge. Die
Kategorie steht auf `created` aufsteigend.

**Der Haken:** Ein später ergänzter Begriff landet unten, nicht an seiner
alphabetischen Stelle. Wer einen hinzufügt, setzt über das Schraubenschlüssel-
Menü unter „Zeitstempel ändern" einen Wert, der zwischen die Nachbarn passt.
Und trägt ihn im Register nach.

Die Kategorie ist schreibgeschützt: `jeder` hat nur Ansehen, nur das Team legt
an. Nachrichten unter Glossareinträgen gäbe es sonst, und ein Glossar ist keine
Diskussion. Nebeneffekt: Ohne Antworten kann die Sortierung auch nicht durch
Aktivität durcheinandergeraten.

**Ein angehefteter Register-Beitrag** mit allen Begriffen nach Alphabet,
jeder verlinkt. Das ersetzt die A-bis-Z-Leiste, denn die Themenliste sortiert
nach Aktivität und nicht nach Alphabet. Ohne Register findet niemand einen
bestimmten Begriff.

---

## Tags

Tags tragen die Achse, die quer zu den Kategorien liegt.

- Werkzeug: `chatgpt`, `claude`, `midjourney`, `n8n`
- Aufgabe: `texten`, `recherche`, `bilder`, `code`, `automatisierung`
- Kurs: `kurs-grundlagen`, `kurs-prompting`, und so weiter, einer je Kurs
- Glossar: die fünf Kategorien aus dem alten Glossar

Tags gehören in Tag-Gruppen, sonst wuchert die Liste. Freies Vergeben durch
Nutzer bleibt aus, nur das Team vergibt.

---

## Bezahlung

Discourse bringt `discourse-subscriptions` mit. Das Plugin steckt inzwischen im
Kern, muss also nicht installiert, nur eingeschaltet werden. Es verkauft
wiederkehrende und einmalige Abos und steckt den Käufer nach Zahlung in eine
Gruppe. Es setzt zwingend Stripe voraus.

Damit gibt es zwei Wege.

### Weg A: Stripe mit dem Bordmittel

Stripe-Konto anlegen, Schlüssel eintragen, Produkt mit 19 Euro im Monat
anlegen, als Zielgruppe `pro` setzen. Fertig.

Dafür spricht: kein Eigenbau, keine Wartung, Nutzer verwalten ihr Abo selbst
über das Kundenportal, Kündigung entfernt die Gruppe automatisch.

**Stripe Tax lässt sich dazuschalten.** Seit Juli 2024 hat das Plugin dafür das
Site Setting `discourse_subscriptions_enable_automatic_tax`. Stripe berechnet
dann den richtigen Satz je Land, prüft Umsatzsteuer-IDs und setzt bei
Geschäftskunden im EU-Ausland das Reverse-Charge-Verfahren. Wer Stripe Checkout
statt der klassischen Methode nutzt, bekommt dasselbe über Stripe direkt.

Dagegen spricht: Stripe Tax rechnet und zieht ein, übernimmt aber nicht die
Haftung. Registrierung in den Ländern, Voranmeldung und Abführung bleiben bei
dir. Gegenüber dem Finanzamt bist weiterhin du der Verkäufer, nicht Stripe. Und
es kommt ein fünfter Zahlungsanbieter zu Fastbill, Paddle und Lemon Squeezy
dazu.

**Neu seit Februar 2026: Stripe Managed Payments.** Das ist Stripes eigenes
Merchant-of-Record-Produkt und damit ein dritter Weg. Ob
`discourse-subscriptions` das ansprechen kann, ist ungeprüft. Das Plugin
arbeitet gegen die normale Subscriptions-API, Managed Payments ist eine andere
Integration. Vor einer Entscheidung dafür nachsehen.

### Weg B: Lemon Squeezy oder Paddle über n8n

Beide sind Merchant of Record. Sie treten als Verkäufer auf, kümmern sich um
Umsatzsteuer in der EU und stellen die Rechnung. Du nutzt beide bereits.

Der Ablauf: Kauf löst einen Webhook aus, n8n nimmt ihn an und ruft die
Discourse-API auf, die den Nutzer in die Gruppe `pro` legt. Kündigung oder
Zahlungsausfall lösen den umgekehrten Weg aus.

    subscription_created    →  PUT    /groups/{id}/members.json
    subscription_cancelled  →  DELETE /groups/{id}/members.json
    subscription_expired    →  DELETE /groups/{id}/members.json

Dafür spricht: die Umsatzsteuer ist erledigt, die Rechnung auch, dein
bestehender Stack bleibt. n8n steht ohnehin auf der Liste.

Dagegen spricht: Eigenbau, den du pflegen musst. Der Nutzer verwaltet sein Abo
beim Anbieter, nicht im Portal. Kein Abo-Bereich in Discourse.

### Lässt sich der Verkauf auf DACH beschränken?

Das hilft steuerlich nicht, weil DACH drei verschiedene Regime sind.

Deutschland ist der einfache Fall. Österreich ist EU-Ausland, für Verkäufe an
Verbraucher dort greift ab der EU-weiten Schwelle von 10.000 Euro das
OSS-Verfahren. Die Schweiz ist gar nicht in der EU und hat eigene Regeln mit
eigener Registrierungspflicht für ausländische Anbieter digitaler Leistungen.

Eine Beschränkung auf DACH nimmt dir also nichts ab, sie fügt mit der Schweiz
sogar ein weiteres Regime hinzu. Was wirklich vereinfacht, ist eine
Beschränkung auf Deutschland allein.

Technisch ist die Beschränkung ohnehin wacklig. Das Plugin hat keine
Länderauswahl. Über Stripe Radar lassen sich Zahlungen nach Kartenland
blockieren, aber das Kartenland ist nicht der Wohnsitz. Ein Deutscher mit
Auslandskarte fliegt raus, ein Auslandskunde mit deutscher Karte kommt rein.

### Was den Ausschlag gibt

Nicht die Technik, sondern die Frage, wer die Steuer schuldet und meldet.

Weg A mit Stripe Tax rechnet richtig, lässt die Pflichten aber bei dir. Das ist
überschaubar, solange nur Deutschland im Spiel ist oder du unter der
10.000-Euro-Schwelle bleibst. Weg B nimmt dir die Pflichten ab, kostet dafür
Eigenbau und einen Prozentpunkt mehr Gebühr.

Das ist eine Frage an deinen Steuerberater, nicht an das Theme. Die Antwort
entscheidet den Weg.

---

## Reihenfolge zum Aufbau

1. Entscheiden, ob Kurse mit Fortschritt und Zertifikat gebraucht werden
2. Gruppe `pro` anlegen
3. Kategorien anlegen, Rechte setzen, Farben nach der Regel oben
4. Tag-Gruppen anlegen
5. Startthemen schreiben, `@system`-Beiträge ersetzen
6. Inhalte aus dem alten Portal übertragen, freie zuerst
7. Bezahlweg entscheiden und einrichten
8. Testkonto ohne `pro` anlegen und jede Kategorie gegenprüfen

Schritt 8 wird gern übersprungen. Ohne ihn merkst du erst am ersten zahlenden
Kunden, dass eine Kategorie falsch steht.

---

## Videohosting für die Kurse

Das steht in `mokkio-projekt.md` unter offenen Entscheidungen und rückt jetzt
auf den kritischen Pfad. Die Kategorierechte schützen den Beitrag, nicht das
Video darin. Ein eingebettetes YouTube-Video ist über seine Adresse für jeden
erreichbar, der sie hat, auch ohne Konto und ohne Abo. Bezahlte Lektionen
laufen damit aus.

Was hilft: Bunny Stream mit signierten Links, die nur befristet und nur auf der
eigenen Domain funktionieren. Vimeo kann Domain-Sperren, das ist schwächer,
aber vorhanden. Vor der ersten bezahlten Lektion muss das stehen.

---

## Offene Fragen

- Bleibt es bei einer Stufe PRO, oder kommt später ein Jahresabo dazu?
- Was passiert mit `portal.greatik.de`, sobald mokkio steht? Abschalten,
  umleiten oder als Landingpage behalten?
- Bleiben die 28 Tools im Portal, oder wandern sie mit?
