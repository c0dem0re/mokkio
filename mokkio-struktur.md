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

Glossar von A bis Z. 45 Begriffe als 45 Themen macht die Liste unbrauchbar.
Besser: fünf Sammelbeiträge nach Kategorie mit Sprungmarken.

**Konsequenz.** Wenn Fortschritt und Zertifikate für die Kurse wichtig sind,
bleibt Discourse die Community und der Kurs liegt woanders. Wenn sie
verzichtbar sind, geht alles in eine Plattform. Das ist die erste Entscheidung,
alles Weitere hängt daran.

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
dessen eine Kategorie `Kurse`, ein Thema je Lektion, ein Tag je Kurs, dazu ein
angehefteter Übersichtsbeitrag pro Kurs, der die Lektionen in Reihenfolge
verlinkt. Der Übersichtsbeitrag ersetzt das Fortschritts-Tracking, so gut es
ohne Technik geht.

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

Dagegen spricht: Stripe ist reiner Zahlungsabwickler, kein Verkäufer. Umsatz-
steuer, Rechnungsstellung und die Meldung für Verkäufe in andere EU-Länder
bleiben bei dir. Und es kommt ein fünfter Zahlungsanbieter zu Fastbill, Paddle
und Lemon Squeezy dazu.

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

### Was den Ausschlag gibt

Nicht die Technik, sondern die Umsatzsteuer. Wenn du Kleinunternehmer bist oder
unter der Schwelle für grenzüberschreitende digitale Leistungen bleibst, ist
Weg A deutlich weniger Arbeit und du bist an einem Tag live. Sobald du regulär
versteuerst und an Verbraucher in mehreren EU-Ländern verkaufst, nimmt dir Weg B
den größeren Brocken ab.

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

## Offene Fragen

- Kurse mit Fortschritt und Zertifikat, oder reicht die Übersicht als Beitrag?
- Bleibt es bei einer Stufe PRO, oder kommt später ein Jahresabo dazu?
- Was passiert mit `portal.greatik.de`, sobald mokkio steht? Abschalten,
  umleiten oder als Landingpage behalten?
- Bleiben die 28 Tools im Portal, oder wandern sie mit?
