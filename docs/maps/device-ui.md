# Device UI maps (T‑Deck, ecc.)

Alcuni device (es. T‑Deck con firmware/UI dedicata) possono caricare mappe da SD.

In generale il flusso è:

1. preparare i file mappa nel formato richiesto dalla Device UI
2. copiare sulla SD nella cartella corretta
3. verificare che la UI trovi le tile e le mostri

---

## Debug rapido “mappa grigia”

- SD non letta / filesystem non compatibile
- path cartelle sbagliato
- zoom/tiles mancanti per la zona
- formati non compatibili

---

## Consiglio pratico

Prima prova con:
- un’area piccola + pochi zoom  
poi aumenta dettaglio.
