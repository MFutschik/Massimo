# Wissen aus den beiden Mouth-Server-Chats (verdichtet)

Stand: 09.11.2026. Quelle: die lesbaren Verläufe (nur Nachrichten und Werkzeugaufrufe) der Chats
"MOUTH Server" (22.10.–08.11.) und "MOUTH server" (29.10.–08.11.). Beide laufen nicht mehr.
Gelesen werden konnten nur Ausschnitte: Chat 1 vor allem 29.–31.10., Chat 2 vor allem 22.10., 28.10.–02.11.
Zeiträume ohne lesbaren Verlauf: 01.–07.11. (Chat 1) und 03.–07.11. (Chat 2). Passwörter und Schlüssel stehen
hier nicht, nur wo sie liegen. **Maßgeblich ist immer die Übergabedatei auf dem Server, nicht dieser Text.**

## 1. Warum die Chats nicht mehr gehen
- Beide meldeten am 08.11.: "Failed to authenticate: OAuth session expired and could not be refreshed"
  (Anmeldung abgelaufen, nicht erneuerbar).
- Beim Wiederöffnen am 09.11.: "environment deleted" – die Fernsteuerungs-Umgebung (`env_01VQSaxm…`), auf der beide
  liefen, ist gelöscht. Der Chat-Stand ist nicht wiederherstellbar.
- Die Chats liefen als Claude Code **auf dem Server selbst** (Benutzer `mouth`, tmux-Fenster `mouth-remote`).
  Vermutung (nicht belegt): Die Claude-Anmeldung auf dem Server ist abgelaufen; Abhilfe wäre dort neu anmelden
  und die Fernsteuerung neu starten. Ob die Umgebung durch den Ablauf oder von Hand gelöscht wurde, ist offen.
- Ein Chat vom 29.10. ("Test") nennt außerdem: "Server stopped at 14:52 without clean shutdown, cause unknown;
  restarted 17:35". Im gelesenen Verlauf der beiden Chats steht das nicht.

## 2. Was „der Mouth-Server" ist
- Ubuntu-Server, ca. 1,8 GB RAM (knapp), 58 GB Platte, IP 31.70.116.70, Domain `mauspropaganda.com`
  (so steht es in den Verläufen; die Firmenwebsite `mouthpropaganda.com` liegt dagegen bei Strato).
  Firewall: offen 22, 80, 443, 993. fail2ban aktiv.
- **Mouth Server (Dienst `mcp-connector`)** stellt claude.ai die Werkzeuge bereit: Aufgabenliste, Mails suchen/Entwurf/Senden,
  Kalender, Drive, sevDesk (nur lesen), awork, Pipedrive, Slack, Spam-Filter, Wissen/Gespräche, Aufträge an Claude Code
  und an Claude in Chrome (Browser-Brücke). Code `/opt/mouth-automation`, Quelle Repo `~/projekte/imap-connector`,
  einspielen mit `bash deploy/aktualisieren.sh` (spielt nur den eingecheckten Stand ein).
- Weitere Dienste: Zentrale `mouth-konfigurator` (`https://mauspropaganda.com/konfigurator/`), `mouth-startseite`,
  `mouth-prog@*` (u. a. roxy, spamfilter, leitstand, mailuebersicht), `mouth-mailer`, `mouth-monitor`, `mouth-watcher`,
  `mouth-abo-bruecke`, nginx, Dovecot (Mail-Spiegel der 6 Postfächer; Original bleibt bei Strato).
- Zeitpläne: Morgenmeldung als Push Mo–Fr 8 Uhr; nächtlich Mail-Nachladen und Spam-Selbstprüfung;
  Vorschau-Ordner laufen nach 7 Tagen ab.
- Wichtige Pfade: Übergabedatei `/home/mouth/projekte/UEBERGABE-MOUTH-SERVER.md`, Arbeitsbrett `~/work/ARBEITSBRETT.md`,
  Bibliothek `/srv/mouth/wissen/` (Einstieg `wegweiser.md`), Gedächtnis `~/.claude/projects/-home-mouth-projekte/memory/`,
  Aufgaben `/srv/mouth/aufgaben/aufgaben.sqlite`, Ablage `/srv/mouth/ablage/`, Board
  `…/konfigurator/apps/hq/board.html`.
- Zugänge (nur Namen): 6 Postfächer bei mouthpropaganda.com, Strato-Kundenkonto (Login nicht auf dem Server),
  1Password, Seite "KI-Schlüssel" in der Zentrale, Google Drive/Kalender, Pipedrive, Slack, sevDesk, awork,
  WordPress-Admin, Europages-Konto, Claude in Chrome. API-Guthaben (Anthropic/OpenAI) war leer; die Abo-Brücke springt ein.

## 3. Regeln und Entscheidungen
- Passwörter nie im Chat, nie per Mail/Slack; nur 1Password oder Seite "KI-Schlüssel". Hook `geheimnis-check.py` blockiert sie.
- Mails nur nach Massimos Ja senden, höchstens 10 pro Stunde.
- Vor Änderungen an gemeinsamen Projekten eine Zeile im Arbeitsbrett eintragen, danach auf "fertig"; unfertige Änderungen
  anderer Chats nicht anfassen. Übergabedatei am Chat-Ende aktualisieren.
- Stil: Du, kurz, einfach, Fortschritt in Zahlen; neue Funktionen erst mit Nutzen erklären und fragen.
- Jans Regel (29.10.): Aufgaben lassen sich per Knopf "An Jan weiterleiten" an Jan geben. Massimos Listen zeigen nur Aufgaben für ihn.
- Website-Texte: keine Preise, Wettbewerber, Vertriebspartner oder Kundennamen; Du-Ansprache. Jan bekommt eigene Zugänge
  (WordPress-Admin, SFTP), nicht Massimos Login und keinen Strato-Kundenbereich.
- Live schalten nur mit Massimos Ja, vorher Sicherung der jetzigen Seite (Vorschlag des Chats, nicht ausdrücklich bestätigt).
- Angebots- und Mail-Skill kommen später in CORTELA mit Jan, nicht auf dem Server.
- Europages (02.11.): Menge, Einheit, Preis und MHD leer; 1–15 Schlagwörter; ein Eintrag je Produkt (Premium Pop,
  Essential Pop, Essential Cup); YouTube-Link zum Imagevideo.
- Chat-Wechsel bei vollem Speicher: alter Chat aktualisiert Übergabedatei, neuer Chat startet mit "Mach weiter.".

## 4. Stand und bekannte Ausfälle
- Fertig bis 31.10.: Zentrale, Roxy, Spam-Filter, Mail-Übersicht, Leitstand, Morgenmeldung, Passwort-Hook, Board für Massimo mit
  Freitextantwort, "An Jan weiterleiten", Feld "beantwortet von", Bereich "Fertig auf der Homepage", Textgrenze 4.000 Zeichen.
- 30.10. Board ohne Verbindung / "unable to open database file": `aufgaben.py` schloss Datenbankverbindungen nie
  (1.019 von 1.024 Dateien offen). Behoben mit imap-connector-Commit f171b89, eingespielt.
  Nicht geprüft: ob `gespraeche.py` dasselbe Leck hat.
- 30.10. iPhone kann nicht senden ("Zeitlimit überschritten" bei `smtp.strato.de`): Ursache nicht gefunden.
- 29.10. Phishing-Mail an sales@ im Namen von Strato (getarnter Absender); echte Strato-Rechnungen kommen von service@strato.de.
- 02.11. Europages: Texte geschrieben, 9 Bilder auf max. 1200 px verkleinert, geheime Bilderadresse läuft **am 09.11.2026 ab**.
  Browser-Auftrag `20261102-163925-b21450` wartet auf Claude in Chrome.

## 5. Offene Punkte (aus den Chats, Stand 02.–08.11.; nicht auf Aktualität geprüft)
**Wartet auf Jan / Massimo**
- Strato-Zugang für den Server (Aufgabe 82dadbddfc); WordPress-Admin für Jan (Auftrag c915b1, Jans Mailadresse fehlt).
- Sichtprüfungen durch Claude in Chrome: 20261029-120325, -120634, -140105, -145144, dazu ältere Aufträge (Sparkasse, Premium Pop, LinkedIn).
- Widersprüchliche Zahlen: Essential Pop 4 oder 5 Wochen Produktionszeit, 3 oder 6 Monate Haltbarkeit; Essential Cup 490 oder 640 Mindestmenge.
- Wettbewerber-Recherche: alter Chat nicht gefunden; Neu-Recherche braucht Massimos Ja.
- Strato WordPress Hosting Plus verlängert sich um den 20.11.2026 (Kündigen oder behalten?).
- Freigaben für `sudo` und `/root` (rechnung@ in den Mail-Proxy); Rechnungen für Antonia (Berner, Miro gefunden, Rest fehlt).
- Info-Liste "Start SEO & Eintragung": Google-Ads-, Bing-, Apple-Konto, LinkedIn-Admin, Handelsregisterauszug, Logo-PNG, Aktionsfotos fehlen.
**Technisch offen**
- Nicht gespeicherte Dateien anderer Chats nicht anfassen (`claude_auftrag_tools.py`, `claude_auftrag_worker.py`, `google_tools.py`, `register.js`).
- Slack-Berechtigung `files:read` für Roxy; Konzept "Homepage ausrollen" (nicht gebaut); Produktseiten auf `mouthpropaganda.com` noch 404.
- Kontaktabgleich Mail/Pipedrive halb fertig; Mail-Zahlen-Fehler vom 29.10. ungeklärt.

## 6. So geht es weiter
1. Auf dem Server neuen Chat starten, "Mach weiter." schreiben; er liest `UEBERGABE-MOUTH-SERVER.md` und das Arbeitsbrett.
2. Zuerst prüfen: `~/bin/browser-auftrag liste`, Aufgabenliste, Dienste, `free -m`, ob die Bilderadresse noch läuft.
3. Einträge der Übergabedatei vom 28.10.–08.11. sind in den lesbaren Verläufen nicht sichtbar – dort nachsehen und nachtragen.
