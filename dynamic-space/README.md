# Dynamic Space

Eigenes Lernprojekt, unabhängig von der MOUTH-Website. Ziel: verstehen, wie eine
3D-Seite entsteht, die komplett aus Code besteht (three.js), am Beispiel
einer **Konservendose**.

Quellen: `live-3d-guide.pdf` (@uijonah, 9 Schritte) und der Claude-Code-Setup-Guide
(nur als Hilfsmittel, nicht als Vorlage).

## Ausprobieren

Datei `schritt-XX-…/index.html` per Doppelklick im Browser öffnen. Kein Server nötig.

## Schritte

| Schritt | Inhalt | Stand |
| --- | --- | --- |
| 01 | Würfel, Licht, Drehen per Ziehen | fertig, im Testbrowser geprüft |
| 02 | Würfel → Dose (Form aus Code), Falzdeckeldose 73/38 mm | fertig, im Testbrowser geprüft; Falz/Mulde geschätzt |
| 03 | Metall-Material (gebürstet / poliert) | offen |
| 04 | Fotostudio-Licht | offen |
| 05 | Kamera per Scroll | offen |
| 06 | Explosionsansicht (Deckel, Dose, Boden) | offen |

## Offene Punkte

- Dose: Durchmesser 73 mm und Höhe 38 mm sind von MOUTH angegeben (Falzdeckeldose 073/038). Geschätzt aus einem Vorlagenbild und NICHT bestätigt: Falzhöhe (4,5 mm), Falzüberstand (0,6 mm), Deckelmulde (2 mm tief), Rundungen. Stehen als Block `MASS` oben im Code von Schritt 02. Echte Werte (Datenblatt) nachtragen.
- Ringzuglasche (Aufreißlasche) fehlt noch. Gehört die zur echten Dose? Und: ist die Deckelfarbe gold? Das Vorlagenbild zeigt Gold, ob das Eurer Dose entspricht, ist offen.
- Die Dose ist innen hohl und ohne Wandstärke (nur Oberflächen). Für die Explosionsansicht (Schritt 06) muss das ggf. nachgezogen werden.
- Soll die Dose eine bestimmte Aufschrift/Etikett bekommen? Wenn ja: Material von MOUTH, nichts ausgedacht.
- Ob die Bewegung auf einem echten Handy flüssig läuft: nur auf dem Gerät prüfbar, nicht hier.
- three.js liegt als Kopie in `lib/` (Version 0.170, MIT-Lizenz). Aktualisieren erst bei Bedarf.
