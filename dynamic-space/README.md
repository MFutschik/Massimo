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
| 02 | Würfel → Dose (Form aus Code) | offen |
| 03 | Metall-Material (gebürstet / poliert) | offen |
| 04 | Fotostudio-Licht | offen |
| 05 | Kamera per Scroll | offen |
| 06 | Explosionsansicht (Deckel, Dose, Boden) | offen |

## Offene Punkte

- Maße der Dose (Durchmesser, Höhe, Randstärke): nichts erfunden, bis jetzt nur Platzhalter. Angabe von Jan/Team nötig, sobald Schritt 02 startet.
- Soll die Dose eine bestimmte Aufschrift/Etikett bekommen? Wenn ja: Material von MOUTH, nichts ausgedacht.
- Ob die Bewegung auf einem echten Handy flüssig läuft: nur auf dem Gerät prüfbar, nicht hier.
- three.js liegt als Kopie in `lib/` (Version 0.170, MIT-Lizenz). Aktualisieren erst bei Bedarf.
