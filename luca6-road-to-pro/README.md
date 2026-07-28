# LUCA6 – Road to Pro

Fertige, installierbare GitHub-Pages-Web-App in Blau/Weiß.

## Sofort online stellen

1. Alle Dateien aus diesem Ordner in das GitHub-Repository `luca-6-performance` hochladen.
2. Bestehende Dateien ersetzen.
3. GitHub Pages lädt die neue Version meist nach 1–3 Minuten.
4. Auf dem iPhone in Safari öffnen → Teilen → „Zum Home-Bildschirm“.

## Bereits funktionsfähig

- Tages-Check-in
- regelbasierter KI-Coach 1.0
- Belastungsampel
- Trainingslog mit lokaler Speicherung
- Wochenumfang und Konstanz
- Road-to-Pro-Score und 6er-Profil
- PWA/Offline-Modus
- Strava-OAuth-Schaltfläche vorbereitet

## Strava sicher verbinden

GitHub Pages darf den geheimen Client-Schlüssel niemals enthalten. Darum wird ein kostenloser Cloudflare Worker als Sicherheitsbrücke verwendet.

1. Den auf dem Screenshot sichtbaren alten Strava-Clientschlüssel zuerst neu generieren.
2. Bei Cloudflare einen Worker anlegen und den Inhalt aus `worker/strava-worker.js` einsetzen.
3. Im Worker diese Variablen/Secrets hinterlegen:
   - `STRAVA_CLIENT_ID` = 268349
   - `STRAVA_CLIENT_SECRET` = der neu erzeugte geheime Schlüssel
   - `APP_URL` = `https://rupert1982.github.io/luca-6-performance/`
4. In Strava als „Authorization Callback Domain“ nur die Domain des Workers eintragen, z. B. `luca6-strava.rupert.workers.dev` – ohne `https://` und ohne Pfad.
5. In `config.js` die Worker-Adresse bei `STRAVA_BACKEND_URL` eintragen.

## Sicherheit

Der Client Secret gehört ausschließlich in die geschützten Worker-Secrets. Nicht in `config.js`, GitHub, Screenshots oder Chatnachrichten eintragen.

## Nächste Ausbaustufen

- Cloud-Datenbank und Anmeldung
- echter serverseitiger OpenAI-Coach
- automatische Strava-Aktivitätsanzeige inklusive Token-Erneuerung
- Matchday-Modus und Saisonplanung
- native iPhone-App für Apple Health/HealthKit
