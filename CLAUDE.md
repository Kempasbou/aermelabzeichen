# Regeln für Claude – Ärmelabzeichen-Sammlung

Dieses Repo ist das Second Brain für die Feuerwehr-Ärmelabzeichen-Sammlung eines Feuerwehrkameraden. Gepflegt wird es von Daniel (Kempasbou) mit Claude. Der Sammler selbst arbeitet nicht mit GitHub.

## Aufbau

- `sammlung.csv` – die Liste aller vorhandenen Abzeichen (Trennzeichen `;`, UTF-8)
- `fotos/` – ein Foto pro Abzeichen, Dateiname = `id` aus der Liste, z. B. `fotos/0001-altdorf-lau.jpg`

### Spalten in `sammlung.csv`

| Spalte | Inhalt |
|---|---|
| `id` | laufende Nummer, 4-stellig (`0001`) |
| `gemeinde` | Ortsname, wie auf dem Abzeichen |
| `ortsteil` | falls das Abzeichen zu einer Ortsteilwehr gehört, sonst leer |
| `landkreis` | Landkreis bzw. kreisfreie Stadt |
| `regierungsbezirk` | nur in Bayern (Oberbayern, Niederbayern, Oberpfalz, Oberfranken, Mittelfranken, Unterfranken, Schwaben); in anderen Ländern leer oder der dortige Regierungsbezirk |
| `bundesland` | Bundesland; bei ausländischen Abzeichen das Land |
| `wappen` | kurze Wappenbeschreibung (Farben, Figuren), damit gleichnamige Orte unterscheidbar sind |
| `aufschrift` | Text auf dem Abzeichen, soweit lesbar |
| `foto` | Dateiname in `fotos/` |
| `erfasst` | Datum der Aufnahme in die Liste (JJJJ-MM-TT) |
| `notiz` | optional, z. B. „doppelt vorhanden“, „Sonderabzeichen“ |

## Ablauf bei einem neuen Foto

1. **Ablesen**: Aufschrift (Ortsname, ggf. „Freiwillige Feuerwehr …“, Landkreis) lesen.
2. **Wappen beschreiben**: Farben, Teilung, Figuren.
3. **Gemeinde bestimmen**: Bei gleichnamigen Orten (z. B. mehrere „Neustadt“, „Altdorf“, „Kirchberg“) entscheidet das Wappen, ggf. der Landkreis auf dem Abzeichen. Wappen im Zweifel per Websuche gegenprüfen (Wikipedia-Artikel der Gemeinde). Wenn es nicht eindeutig ist: die Kandidaten nennen und nachfragen, nicht raten.
4. **Abgleich mit `sammlung.csv`**: gleiche Gemeinde **und** passendes Wappen/Ortsteil = vorhanden.
5. **Antwort** – kurz, in dieser Form:
   - ✅ **Schon vorhanden** – Gemeinde, Landkreis, Regierungsbezirk/Bundesland (Nr. `id`)
   - 🆕 **Neu** – Gemeinde, Landkreis, Regierungsbezirk/Bundesland
   - ❓ **Unklar** – Kandidaten mit Unterscheidungsmerkmal
6. **Eintragen**: Neue Abzeichen nur auf ausdrückliche Bestätigung („aufnehmen“, „ja, eintragen“) in die Liste schreiben und das Foto unter `fotos/` ablegen. Ein reiner Abgleich ändert nichts.

## Git

- Eine Änderung pro Commit, Message auf Deutsch im Präsens (z. B. „Nimmt Abzeichen Altdorf b. Nürnberg auf“).
- Pushen: `git fetch origin main && git rebase origin/main && git push origin HEAD:main`, danach prüfen, dass der Commit auf `origin/main` liegt. Erst dann „gespeichert“ melden.
- Nichts löschen; Fehleinträge in der Spalte `notiz` kennzeichnen, außer Daniel sagt ausdrücklich „löschen“.

## Stil

Antworten knapp und auf Deutsch. Der Sammler ist kein Computer-Mensch: keine Fachbegriffe, keine Git-Details in der Antwort.
