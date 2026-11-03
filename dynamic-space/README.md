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
| 02 | Dose-Form nach Vorlagenbild: Falzrand, Riefen im Deckel, Ringlasche | überarbeitet nach Vorlage, im Testbrowser geprüft; Details aus dem Bild geschätzt |
| 03 | Metall-Material nach Vorlage (Deckel satiniert, Rand/Lasche poliert, Etikett schwarz mit feiner Längsmaserung) | überarbeitet nach Vorlage, im Testbrowser geprüft; Umgebung nur Platzhalter |
| 04 | Fotostudio-Licht (dunkler Raum, Softbox, 2 Lichtstreifen, Cursor dreht das Studio) | fertig, im Testbrowser geprüft; Abstimmung nach Augenmaß, mit selbstgebauter Dose |
| 05 | Kamera per Scroll | offen |
| 06 | Explosionsansicht (Deckel, Dose, Boden) | offen |

## Arbeitsregel

Das Vorlagenbild von Jan („YOUR BRAND"-Dose) ist die Referenz. Nichts hinzuerfinden, was
dort nicht zu sehen ist. Was aus dem Bild geschätzt ist, steht im Code als „geschätzt".

## Offene Punkte

- Maße: 73 mm Durchmesser und 38 mm Höhe der ganzen Dose (von Jan bestätigt). Alles andere (Falzhöhe, Tiefe und Lage der Riefen, Laschengröße, Winkel) ist aus dem Bild geschätzt, für das Lernprojekt ausreichend.
- Noch nicht nachgebaut, aber im Vorlagenbild zu sehen: die gepresste Mulde im Deckel rund um die Lasche, die Nietform im Detail, die Rundung des Lasche-Hebels, der Fuß-Falz am Boden im Detail (derzeit gespiegelter Deckel-Rand).
- Schriftzug „YOUR BRAND" auf dem Etikett ist ein Platzhalter der Vorlage und wird nicht übernommen. Echter Text/Logo kommt von MOUTH.
- Farben (Gold, Schwarz) stammen aus der Vorlage, nicht aus einem MOUTH-Farbwert.
- Entscheidung Jan: Die finale Dose kommt als Modell aus Blender (`.glb`, Teile `Deckel`, `Lasche`, `Koerper`, `Boden`, 73 × 38 mm). Die selbstgebaute Dose dient bis dahin nur zum Lernen. Sobald das Modell da ist: Dateinamen/Teile prüfen, Lader (`GLTFLoader`) und kleinen lokalen Server einrichten, Studio-Licht aus Schritt 04 übernehmen.
- Schritt 04: Draufsicht von oben ist dunkel, weil das Metall dann den dunklen Studiohimmel spiegelt. Das ist physikalisch richtig, wirkt aber anders als die Vorlage. Entscheidung offen, ob wir oben noch ein Licht ergänzen.
- Schritt 04: Die Helligkeit des Etiketts (dunkelgrau) ist nach Augenmaß aus der Vorlage abgestimmt, kein Messwert.
- Die Dose ist innen hohl und ohne Wandstärke (nur Oberflächen). Für die Explosionsansicht (Schritt 06) muss das ggf. nachgezogen werden.
- Ob die Bewegung auf einem echten Handy flüssig läuft: nur auf dem Gerät prüfbar, nicht hier.
- three.js liegt als Kopie in `lib/` (Version 0.170, MIT-Lizenz). Aktualisieren erst bei Bedarf.
