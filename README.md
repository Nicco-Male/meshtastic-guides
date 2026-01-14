# Meshtastic Guides

Repository “contenitore” per guide Meshtastic: **app**, **firmware**, **hardware**, **MQTT**, **mappe**, troubleshooting e best practice operative.

## Sito (documentazione)
Il sito è generato con **MkDocs + Material** (statico, veloce, ottimo per docs).

### Avvio rapido (locale)
```bash
python -m venv .venv
# Windows: .venv\Scripts\activate
source .venv/bin/activate

pip install -r requirements.txt
mkdocs serve
```
Apri: http://127.0.0.1:8000

### Deploy su GitHub Pages
Il deploy è gestito da GitHub Actions (`.github/workflows/gh-pages.yml`).

Dopo il push su GitHub:
- **Settings → Pages → Build and deployment → Source: GitHub Actions**

## Struttura
- `docs/` contenuti del sito (Markdown + assets)
- `mkdocs.yml` configurazione e navigazione
- `templates/` template interni per scrivere le schede (non pubblicati sul sito)

## Licenze
- Documentazione: **CC BY-SA 4.0** (`LICENSE-DOCS`)
- Codice/config: **MIT** (`LICENSE-CODE`)
