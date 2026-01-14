# Meshtastic Guides

Repository “contenitore” per guide Meshtastic: **app**, **firmware**, **hardware**, **MQTT**, **mappe**, troubleshooting e best practice operative.

Fonti principali:
- https://meshtastic.org/
- https://www.loraitalia.it/

## Sito (documentazione)
Il sito è generato con **MkDocs + Material**.

### Avvio rapido (locale)
```bash
python -m venv .venv
source .venv/bin/activate

python -m pip install -r requirements.txt
python -m mkdocs serve
```

Apri: http://127.0.0.1:8000

> Nota: usare `python -m mkdocs ...` evita problemi di PATH quando il sistema ha già `mkdocs` installato via apt.

### Deploy su GitHub Pages
Il deploy è gestito da GitHub Actions (`.github/workflows/gh-pages.yml`).

Dopo il push su GitHub:
- **Settings → Pages → Build and deployment → Source: GitHub Actions**

## Lingue (ITA + EN)
Il sito è in italiano (default) ed è predisposto per inglese usando il plugin `mkdocs-static-i18n`.

- Italiano: `docs/*.md`
- Inglese: aggiungi traduzioni con suffisso `*.en.md` (fallback automatico all’italiano se manca)

## Struttura
- `docs/` contenuti del sito (Markdown + assets)
- `mkdocs.yml` configurazione e navigazione
- `templates/` template interni per scrivere le schede (non pubblicati sul sito)

## Licenze
- Documentazione: **CC BY-SA 4.0** (`LICENSE-DOCS`)
- Codice/config: **MIT** (`LICENSE-CODE`)
