# JARVIS 3.0 – iPad AI Edition

## Was funktioniert
- Sprachaufnahme über Mikrofontaste (Start/Stopp) mit iPad Safari MediaRecorder; Übertragung an Whisper via Groq.
- KI-Dialoge über Groq, sichere Vermittlung via Cloudflare Worker.
- Vorlesen über iPad Systemstimme (keine Film-Stimmenkopie).
- Aufgaben, Uhrzeit und Notizen lokal; installierbare Web-App.
- Keine permanente Wake-Word-Erkennung, keine externe Computersteuerung, keine Gmail-/Kalenderaktionen.

## 1. GitHub Pages aktualisieren
1. `index.html`, `icon.svg`, `manifest.webmanifest`, `sw.js`, `README.md` im vorhandenen Repository `Lazarus-Projekt/Jarvis-ipad` hochladen und vorhandene Dateien ersetzen. `worker.js` NICHT nach GitHub Pages hochladen; Worker separat bei Cloudflare einfügen.
2. GitHub Pages: Settings → Pages → Deploy from a branch → main → /(root).
3. App unter `https://lazarus-projekt.github.io/Jarvis-ipad/` öffnen, nach Veröffentlichung neu laden. Falls alte Version angezeigt wird, Webseite schließen und Safari-Daten für die Seite löschen oder auf neues Update warten.

## 2. Kostenlosen Groq API-Schlüssel holen
1. https://console.groq.com öffnen und anmelden.
2. Unter API Keys einen neuen Key erstellen. Nur in Cloudflare Secrets speichern, niemals in GitHub oder in der Web-App.
3. Gratisnutzung ist limitiert; Limits können sich ändern.

## 3. Cloudflare Worker im Browser erstellen
1. https://dash.cloudflare.com öffnen, kostenloses Konto erstellen.
2. Workers & Pages → Create → Worker → Hello World / Start with Hello World → Deploy.
3. Worker → Edit code. Standardcode durch den gesamten Inhalt von `worker.js` ersetzen, Deploy klicken.
4. Worker → Settings → Variables and Secrets → Add. Diese drei Einträge anlegen:
   - `GROQ_API_KEY` als **Secret**, Wert: Groq API Key.
   - `JARVIS_PIN` als **Secret**, Wert: ein langes eigenes Passwort (mind. 16 zufällige Zeichen empfohlen).
   - `ALLOWED_ORIGIN` als Variable, Wert: `https://lazarus-projekt.github.io` (OHNE Slash am Ende).
5. Speichern/Deploy. Optional `CHAT_MODEL` als Variable auf `openai/gpt-oss-20b` setzen; wenn Groq dieses Modell künftig nicht mehr anbietet, die ID durch ein aktuelles Groq-Chatmodell ersetzen.
6. Kopiere deine Worker-Adresse, z. B. `https://jarvis-abc.DEINNAME.workers.dev`.

## 4. Auf dem iPad verbinden
1. Öffne JARVIS in Safari.
2. Unter Einstellungen Worker-Adresse und JARVIS_PIN eingeben.
3. „Serveradresse speichern“ und „Verbindung testen“ drücken.
4. Bei Erfolg: Text eingeben oder Mikrofon starten, sprechen, Aufnahme beenden.
5. Safari → Teilen → Zum Home-Bildschirm.

## Sicherheit und Grenzen
- `worker.js` ist öffentlicher Anwendungscode, enthält aber keine Geheimnisse.
- PIN wird nur im Arbeitsspeicher des Tabs gehalten, nicht persistent gespeichert; nach Neuladen neu eingeben.
- Der Server erlaubt ausschließlich den konfigurierten GitHub-Pages-Origin. Das ist **keine vollwertige Authentifizierung**; der PIN ist zusätzlich erforderlich. Bei öffentlicher Nutzung besser Cloudflare Access oder echte Benutzeranmeldung ergänzen, sowie Rate Limiting.
- Kein API-Key in GitHub, lokalen Einstellungen oder JavaScript hinterlegen.
- Groq erhält die eingesprochenen Audiodaten zur Transkription und Textnachrichten zur Beantwortung.
- Browser-Sprachausgabe kann je nach iPadOS eingeschränkt sein; teste „Stimme testen“.
- Kein 24/7-„Hey Jarvis“ auf iPad im Hintergrund.
- Der freie Tarif ist nicht unbegrenzt und kann sich ändern.
- Wenn die Seite nach Aktualisierung noch alt ist, iPad-Web-App schließen und erneut öffnen. Der Service Worker aktualisiert die App ggf. erst beim nächsten Laden.
