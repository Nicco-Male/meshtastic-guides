# Tile / download (mappe dettagliate)

Se vuoi mappe molto dettagliate (es. Toscana super zoomata, Europa dettagliata, mondo più “generico”), la strategia tipica è:

1. scegliere sorgente tile (OpenStreetMap / provider)
2. scaricare tile per bounding box + zoom
3. impacchettare nel formato richiesto (a seconda del client/device)
4. copiare su SD / storage

---

## Strategia consigliata “mix dettaglio”

- **Mondo**: zoom bassi (panoramica)
- **Europa**: zoom medi
- **Italia**: zoom più alti
- **Toscana / zona critica**: zoom alti (massimo dettaglio)

Questo evita SD “in fiamme” e download inutili.

---

## Consigli per non esplodere lo storage

- Scarica in **pezzi** (bbox più piccole)
- Evita zoom altissimi su aree enormi
- Misura il “peso” con `--dry-run` quando possibile

---

## Tool utili (idee)

- downloader tile (bbox, zoom, output)
- script di merge/organizzazione
- compressione e cache
