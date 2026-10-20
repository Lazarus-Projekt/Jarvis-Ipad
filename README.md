# JARVIS – iPad Edition

## Was wirklich funktioniert
- Als eigenständige Website auf iPad ohne PC-Server nutzbar, sobald sie über HTTPS gehostet wird.
- Futuristische Oberfläche, lokale Aufgaben, Uhrzeit/Datum, Textbefehle, Websuche und systemeigene Sprachausgabe.
- Mikrofoneingabe nur, wenn Safari/iPadOS die Web Speech Recognition API anbietet und die Berechtigung erteilt wurde. Als Alternative iPad-Tastaturdiktat verwenden.
- Offline nach erfolgreicher Installation über HTTPS und Service Worker für lokale Funktionen; KI/Websuche brauchen Internet.
- Optional: selbst betriebener sicherer HTTPS-KI-Server, der POST JSON {"message":"..."} annimmt und {"reply":"..."} zurückgibt. Niemals einen geheimen API-Schlüssel im Browser speichern.

## Auf dem iPad installieren – ohne laufenden PC
1. ZIP entpacken, die vier Dateien `index.html`, `icon.svg`, `manifest.webmanifest`, `sw.js` auf einen statischen HTTPS-Webhost hochladen (z.B. GitHub Pages, Netlify Drop oder Cloudflare Pages). Auf dem iPad kann das z.B. über Safari und den Dateien-Dialog erfolgen. Die Datei allein in der Dateien-App zu öffnen ist **keine** zuverlässige PWA-Installation.
2. Die öffentliche HTTPS-Adresse in Safari öffnen.
3. Teilen > Zum Home-Bildschirm > Hinzufügen.
4. Das neue JARVIS-Symbol antippen. Für Sprache ggf. Mikrofonberechtigung erlauben.

## Grenzen
- Kein permanentes „Hey Jarvis“ im Hintergrund: iPadOS schränkt kontinuierliche Hintergrund-Mikrofonaktivierung für Websites ein. Im Vordergrund den Button „Sprechen“ antippen.
- Keine exakte Iron-Man-Filmstimme; es wird die auf dem Gerät verfügbare deutsche Systemstimme genutzt.
- Kein eigenständiges E-Mail-Senden, App-Steuern oder freie PC-Automation. Solche Aktionen erfordern sichere Integrationen und eine serverseitige KI-/Tool-Schicht.
- Das ZIP kann ich nicht selbst auf deinem iPad installieren oder öffentlich hosten.

## Später Raspberry Pi
Die Oberfläche ist statisch und lässt sich auf dem Pi mit nginx oder einem anderen Webserver hosten. Für KI-Funktionen und Sprachhardware wird zusätzlich ein Backend benötigt.
