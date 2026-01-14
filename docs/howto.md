# Come usare queste guide (e contribuire)

Questa pagina è la “cassetta degli attrezzi” del repository: come è organizzato, come far girare il sito, come scrivere pagine nuove, e come evitare i classici errori.

---

## Come avviare il sito in locale (consigliato: virtualenv)

```bash
python -m venv .venv
source .venv/bin/activate

python -m pip install -r requirements.txt
python -m mkdocs serve
```

Apri: `http://127.0.0.1:8000/`

!!! tip "Se `mkdocs` punta a /usr/bin anche con la venv attiva"
    Usa sempre `python -m mkdocs ...` (così sei sicuro di usare i pacchetti della venv).

---

## Struttura cartelle

- `docs/`  
  Tutto ciò che finisce pubblicato sul sito (Markdown + immagini + CSS).
- `mkdocs.yml`  
  Config del sito (theme, plugin, navigazione).
- `.github/workflows/gh-pages.yml`  
  Deploy automatico su GitHub Pages tramite Actions.
- `templates/`  
  Template interni per scrivere nuove guide (non pubblicati).

---

## Stile editoriale (linee guida)

### 1) Scrivi per chi sta facendo, non per chi sta leggendo
- “Clicca qui → imposta questo valore → ecco cosa succede”.
- Inserisci check-list, tabelle piccole, “se vedi X allora Y”.

### 2) Separare “procedura” da “spiegazione”
- Prima la procedura, poi il perché (così l’utente non si perde).

### 3) Evita di “inventare”
Se un dettaglio è incerto o cambia tra versioni:
- scrivi “può variare”  
- metti il link ufficiale in **Link utili**

---

## Aggiungere una nuova pagina

1. Crea un file in `docs/...` (es: `docs/apps/android/foobar.md`)
2. Aggiungilo in `mkdocs.yml` sotto `nav:`
3. `python -m mkdocs serve` e verifica la navigazione

---

## Screenshot e immagini

- Metti le immagini in `docs/assets/...`
- Referenziale dal markdown:

```md
![Descrizione](../assets/nomefile.png)
```

Consiglio pratico:
- Usa immagini “crop” (solo la parte utile)
- Oscura dati personali (nome nodo, coordinate, ecc.)

---

## Lingue (ITA + EN)

Il sito nasce in **italiano**, ma è predisposto per **inglese** usando file con suffisso `.en.md`.

Esempio:
- `docs/index.md` → italiano (default)
- `docs/index.en.md` → inglese (traduzione)

Se una traduzione manca, l’inglese “eredita” il contenuto italiano (fallback).  
Questo ci permette di crescere gradualmente senza “bloccare” il sito.

---

## Licenze

- Testi e documentazione: **CC BY-SA 4.0**
- Codice/configurazioni: **MIT**

---

## Checklist PR (quando fai una Pull Request)

- [ ] La pagina è in `docs/` e appare nel `nav` se serve
- [ ] I comandi sono testati o dichiarati come “non testati”
- [ ] Nessun dato personale o chiave/PSK pubblicata
- [ ] Le impostazioni “controverse” hanno una nota (es: hop limit alto)
