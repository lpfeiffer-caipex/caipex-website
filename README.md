# CAIPEX Website

Statische Marketing-Website (client-seitig gerendert). Wird als Container über Google Cloud Run bereitgestellt.

## Struktur
- `index.html` — Startseite
- `rechtliches.html` — Impressum & Datenschutz
- `support.js` — Runtime (nicht bearbeiten)
- `img/`, `fotos/`, `fonts/`, `uploads/`, `vendor/` — Assets
- `Dockerfile`, `nginx.conf` — Container-Setup (nginx, Port 8080)
- `robots.txt`, `sitemap.xml`

## Lokal testen
```bash
docker build -t caipex-web .
docker run -p 8080:8080 caipex-web
# → http://localhost:8080
```

## Deploy auf Google Cloud Run
```bash
gcloud run deploy caipex-web \
  --source . \
  --region europe-west3 \
  --allow-unauthenticated
```
Cloud Run baut das Image aus dem `Dockerfile`, startet den Container auf Port 8080 und liefert eine öffentliche URL. Danach eigene Domain (caipex.de) über „Manage Custom Domains" / Domain-Mapping verbinden.

## Vor dem Live-Gang noch offen
- Impressum: USt-IdNr. ergänzen; HRB-Nummer prüfen (Website vs. Vertrag)
- Datenschutz: Hosting-Anbieter dieser Website eintragen
- Backend/Cloud SQL: Backups & PITR aktivieren (siehe TOMs)
