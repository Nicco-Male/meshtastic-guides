# How to use these guides (and contribute)

## Run locally (recommended: virtualenv)

```bash
python -m venv .venv
source .venv/bin/activate

python -m pip install -r requirements.txt
python -m mkdocs serve
```

Open: `http://127.0.0.1:8000/`

> Tip: using `python -m mkdocs ...` avoids PATH issues when MkDocs is installed system-wide.

## Languages (IT + EN)

- Italian is the default (`docs/*.md`)
- English translations use the suffix `*.en.md`
- Missing translations automatically fall back to Italian
