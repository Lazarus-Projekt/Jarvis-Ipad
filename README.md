# JARVIS 2.0 – iPad Edition

## Installation über GitHub (ohne PC)

1. ZIP auf dem iPad entpacken.
2. Dein GitHub-Repository `Jarvis-ipad` öffnen.
3. **Add file → Upload files** auswählen und **alle vier Dateien** `index.html`, `manifest.webmanifest`, `icon.svg`, `sw.js` hochladen. Bestehende Dateien ersetzen (GitHub lässt Upload mit identischen Namen als Änderung zu). `README.md` kann ebenfalls ersetzt werden.
4. **Commit changes** bestätigen.
5. Unter **Settings → Pages**: Deploy from a branch, `main`, `/(root)` und Save. Falls Pages bereits aktiv ist, nichts ändern.
6. Nach der Veröffentlichung in Safari die GitHub-Pages-URL öffnen und **neu laden**. Bei alter Version Safari-Website-Daten löschen oder die Seite mit `?v=2` aufrufen.
7. Über Teilen → Zum Home-Bildschirm installieren.

## Sprachfunktionen – wichtige Einschränkung

- Die Schaltfläche **Stimme testen** aktiviert die lokale iPad-Sprachausgabe. Wähle in den Einstellungen eine verfügbare deutsche Stimme. Keine originalgetreue Iron-Man-Filmstimme enthalten.
- **Sprechen** nutzt die Browser-API SpeechRecognition, **nur wenn iPadOS/Safari diese bereitstellt**. Diese API kann auf iPads fehlen. **Audio prüfen** zeigt getrennt Mikrofonberechtigung, Browser-Spracherkennung und Sprachausgabe an.
- Verlässliche Alternative ohne zusätzliche Server: das Texteingabefeld antippen und **Diktat (Mikrofon) auf der iPad-Tastatur** nutzen.
- Keine dauerhafte „Hey Jarvis“-Hintergrundaktivierung auf iPadOS.
- Für zuverlässige Audio-Transkription über eine KI ist ein separater sicherer Backend-Dienst erforderlich. GitHub Pages hostet nur statische Dateien.

## Was funktioniert

Aufgaben lokal speichern und abhaken, Uhrzeit/Datum, Websuche, animierte Oberfläche, Systemstatus, einstellbare lokale Sprachausgabe und optionaler HTTPS-KI-Endpunkt (POST `{"message":"..."}`, Antwort `{"reply":"..."}`). **Niemals einen geheimen API-Schlüssel in GitHub Pages oder die Browser-Einstellungen eintragen.**

Dies ist eine verbesserte Version des lokalen Prototyps, keine vollständige autonome KI oder native iPad-App. Externe Aktionen brauchen sichere Berechtigungen und weitere Integrationen.
