# Cloudflare Zero Trust – Custom Block Page

Eine benutzerfreundliche, weiß-orange Block Page für Cloudflare Zero Trust Gateway.

## Deployment auf Cloudflare Pages

### 1. GitHub Repo einrichten

```bash
git init cf-block-page
cd cf-block-page
cp /pfad/zu/index.html .
cp /pfad/zu/_headers .
git add .
git commit -m "Initial block page"
git remote add origin https://github.com/DEIN-USER/cf-block-page.git
git push -u origin main
```

### 2. Cloudflare Pages verknüpfen

1. [dash.cloudflare.com](https://dash.cloudflare.com) → **Workers & Pages** → **Create application** → **Pages**
2. GitHub-Repo `cf-block-page` auswählen
3. Build-Einstellungen:
   - **Build command:** *(leer lassen)*
   - **Build output directory:** `/`
4. **Save and Deploy**

Du bekommst eine URL wie: `https://cf-block-page.pages.dev`

### 3. In Zero Trust als Custom Block Page eintragen

1. [one.dash.cloudflare.com](https://one.dash.cloudflare.com) → **Settings** → **Custom Pages**
2. Bei **Block Page** → **Custom** aktivieren
3. URL eintragen: `https://cf-block-page.pages.dev`
4. Speichern

Cloudflare hängt automatisch alle Parameter an (url, timestamp, device_id, query_id usw.) – die Seite wertet sie clientseitig aus.

## Ausgewertete URL-Parameter

| Parameter | Beschreibung |
|---|---|
| `url` | Blockierte URL |
| `name` | Name der Organisation |
| `header_text` | Überschriften-Text |
| `footer_text` | Erklärungstext |
| `block_reason` | Grund der Blockierung |
| `timestamp` | Unix-Zeitstempel |
| `source_ip` | IP-Adresse des Nutzers |
| `device_id` | Geräte-ID |
| `query_id` | Anfrage-ID (für Support) |
| `rule_id` | Gateway-Regel-ID |
| `user_id` | Nutzer-ID |
| `mailto_address` | Kontakt-E-Mail |
| `mailto_subject` | E-Mail-Betreff |
