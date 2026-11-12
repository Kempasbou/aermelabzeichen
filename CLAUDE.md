# Regeln für Claude – Ärmelabzeichen-Sammlung

Dieses Repo ist das Second Brain für die Feuerwehr-Ärmelabzeichen-Sammlung eines Feuerwehrkameraden. Gepflegt wird es von Daniel (Kempasbou) mit Claude. Der Sammler selbst arbeitet nicht mit GitHub.

## Aufbau

- `sammlung.csv` – die Liste aller vorhandenen Abzeichen (Trennzeichen `;`, UTF-8)
- `fotos/` – ein Foto pro Abzeichen, Dateiname = `id` aus der Liste, z. B. `fotos/0001-altdorf-lau.jpg`
- `fotos/sammelfotos/` – Originalfotos mit mehreren Abzeichen; Einzelbilder werden daraus ausgeschnitten, die Herkunft steht in `notiz` („Sammelfoto 1“)

### Spalten in `sammlung.csv`

| Spalte | Inhalt |
|---|---|
| `id` | laufende Nummer, 4-stellig (`0001`) |
| `gemeinde` | politische Gemeinde (bei Ortsteilwehren die heutige Gemeinde, z. B. Vaterstetten für Baldham) |
| `ortsteil` | falls das Abzeichen zu einer Ortsteilwehr gehört, sonst leer |
| `landkreis` | Landkreis bzw. kreisfreie Stadt |
| `regierungsbezirk` | nur in Bayern (Oberbayern, Niederbayern, Oberpfalz, Oberfranken, Mittelfranken, Unterfranken, Schwaben); in anderen Ländern leer oder der dortige Regierungsbezirk |
| `bundesland` | Bundesland; bei ausländischen Abzeichen das Land (z. B. `USA`, `Ungarn`) |
| `wappen` | kurze Wappenbeschreibung (Farben, Figuren), damit gleichnamige Orte unterscheidbar sind |
| `aufschrift` | Text auf dem Abzeichen, soweit lesbar |
| `anzahl` | wie viele Exemplare vorhanden sind (Zahl, Standard 1) |
| `foto` | Dateiname in `fotos/` |
| `erfasst` | Datum der Aufnahme in die Liste (JJJJ-MM-TT) |
| `notiz` | optional, z. B. „doppelt vorhanden“, „Sonderabzeichen“ |
| `ablage` | wo das Abzeichen physisch liegt, z. B. `Ordner 1 „FFW Bayern m. Wappen“`; Fotos der Ordnerrücken in `fotos/ordner/`. Nennt Daniel beim Erfassen einen Ordner, hier eintragen. |
| `kategorie` | `Deutschland` (Gemeinde-, Stadt-, Kreis- und KatS-Abzeichen), `Werkfeuerwehr` (Werk- und Betriebsfeuerwehren, auch Verbände wie AGBB), `Ausland` (alles außerhalb Deutschlands, auch US-Streitkräfte in Deutschland), `Sonstige Organisationen` (THW, Polizei-/Ortspolizeibehörden, Werkschutz, Selbstschutz, Reservisten, DDR), `Sonderabzeichen` (ohne Ort, Werbung, Vereine, Spaßabzeichen, Aufkleber) |

### Felder bei Werkfeuerwehr und Ausland

- **Werkfeuerwehr**: `gemeinde` = Ort des Werks, `ortsteil` = Firma (z. B. `Gersthofen` / `Clariant`), Landkreis/Bezirk/Bundesland wie bei Gemeinden. Auf der Webseite eine gemeinsame Gruppe „Werkfeuerwehren“, unterteilt nach Bundesland.
- **Ausland**: `bundesland` = Land, `regierungsbezirk` = Bundesstaat/Provinz/Region (z. B. `New York`, `Komitat Tolna`, `Ontario`), `landkreis` = County/Bezirk falls bekannt. US-Militärfeuerwehren in Deutschland: `bundesland` = `USA`, `regierungsbezirk` = `US-Streitkräfte`, deutscher Standort in `notiz`.

## Ablauf bei einem neuen Foto

1. **Ablesen**: Aufschrift (Ortsname, ggf. „Freiwillige Feuerwehr …“, Landkreis) lesen.
2. **Wappen beschreiben**: Farben, Teilung, Figuren.
3. **Gemeinde bestimmen**: Bei gleichnamigen Orten (z. B. mehrere „Neustadt“, „Altdorf“, „Kirchberg“) entscheidet das Wappen, ggf. der Landkreis auf dem Abzeichen. Wappen im Zweifel per Websuche gegenprüfen (Wikipedia-Artikel der Gemeinde, Begriffsklärungsseite für gleichnamige Orte).
   - **Immer festlegen**: Auch wenn es mehrere Kandidaten gibt, den wahrscheinlichsten Ort benennen (Bundesland + Regierungsbezirk) – nicht offen lassen, nicht nur Kandidaten aufzählen. Unsicherheit wird mit „vermutlich“ gekennzeichnet, nicht mit „unklar“.
   - **Einordnung erläutern**: Zu jeder Festlegung, die nicht offensichtlich ist, kurz begründen, woran sie hängt – Wappen (Farben, Figuren, typische Motive wie Rauten/Pfälzer Löwe), Abzeichenstil (bayerischer Stil), Bezeichnung („Stadt“, „Markt“), frühere Gemeindezugehörigkeit – und die verworfenen gleichnamigen Orte mit Bundesland/Bezirk nennen.
4. **Abgleich mit `sammlung.csv`**: gleiche Gemeinde **und** passendes Wappen/Ortsteil = vorhanden.
5. **Antwort** – kurz, in dieser Form:
   - ✅ **Schon vorhanden** – Gemeinde, Landkreis, Regierungsbezirk/Bundesland (Nr. `id`, bisher `anzahl`×)
   - 🆕 **Neu** – Gemeinde, Landkreis, Regierungsbezirk/Bundesland
   - ⚠️ **Vermutlich** – wahrscheinlichster Ort mit Bundesland/Regierungsbezirk, dazu die Begründung und die verworfenen Alternativen
   - Bei mehreren Abzeichen auf einem Foto: Reihenfolge von links oben nach rechts unten, nummeriert, jeweils mit Bundesland und Regierungsbezirk.
6. **Eintragen**: Neue Abzeichen nur auf ausdrückliche Bestätigung („aufnehmen“, „ja, eintragen“) in die Liste schreiben und das Foto unter `fotos/` ablegen. Ein reiner Abgleich ändert nichts.

## Anzahl / Mehrfachstücke

- Pro Abzeichen gibt es **eine Zeile**; Mehrfachstücke stehen in `anzahl`, nicht als eigene Zeilen.
- Daniel gibt die Anzahl beim Erfassen im Prompt mit (z. B. „3×“, „Anzahl 2“). Ohne Angabe gilt 1.
- Ist ein Abzeichen schon vorhanden und Daniel sagt „aufnehmen“ bzw. „noch eins“, wird `anzahl` um die genannte Zahl (sonst 1) erhöht, keine neue Zeile.
- Das bestehende Foto bleibt; ein neues Foto nur ersetzen, wenn Daniel es sagt.
- Ordnerfotos: Gezählt wird nur das vorne sichtbare Abzeichen je Fach. Was dahinter steckt bzw. spiegelverkehrt durchscheint, ist die Rückseite (bzw. die Rückseite des Blatts) und wird nicht gezählt.

## Eingang (Fotos von der Webseite)

- Über die Webseite (Repo `aermelabzeichen-app`) hochgeladene Fotos landen in `eingang/` als `JJJJ-MM-TT-HHMMSS-n.jpg`, eine optionale Bemerkung (z. B. Anzahl) als `…-bemerkung.txt` mit gleichem Zeitstempel.
- Sagt Daniel „Eingang verarbeiten“, „neue Fotos eintragen“ o. ä., gilt das als Bestätigung: alle Fotos in `eingang/` wie Sammelfotos abarbeiten (Ablauf oben, Reihenfolge links oben → rechts unten), neue Abzeichen aufnehmen, vorhandene in `anzahl` erhöhen, Bemerkungen berücksichtigen. Sagt er nur „Eingang prüfen“, nur abgleichen und berichten.
- Nach dem Eintragen jedes verarbeitete Foto mit `git mv` nach `fotos/sammelfotos/` verschieben (Bemerkung mit verschieben), damit `eingang/` leer ist. In `notiz` den Dateinamen des Sammelfotos angeben.

## Git

- Eine Änderung pro Commit, Message auf Deutsch im Präsens (z. B. „Nimmt Abzeichen Altdorf b. Nürnberg auf“).
- Pushen: `git fetch origin main && git rebase origin/main && git push origin HEAD:main`, danach prüfen, dass der Commit auf `origin/main` liegt. Erst dann „gespeichert“ melden.
- Nichts löschen; Fehleinträge in der Spalte `notiz` kennzeichnen, außer Daniel sagt ausdrücklich „löschen“.

## Stil

Antworten knapp und auf Deutsch. Der Sammler ist kein Computer-Mensch: keine Fachbegriffe, keine Git-Details in der Antwort.
