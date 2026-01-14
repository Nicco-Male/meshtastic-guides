# Antenne & RF (linee guida pratiche)

Se Meshtastic fosse un videogame, l’antenna sarebbe il pezzo “legendary”.

---

## Tre regole che evitano disastri

1. **Antenna giusta per la banda** (EU_868 ≈ 868 MHz)
2. **Cavo corto** (ogni metro di cavo scadente è un nemico)
3. **Posizione alta e libera** (line-of-sight vince)

---

## Antenna stock vs antenna “buona”

Molti device arrivano con antenne “ok per test”, ma:
- non sempre sono tarate bene
- non sempre sono davvero per 868 MHz
- spesso hanno guadagno e qualità variabili

Se stai facendo una dorsale o un nodo fisso:
- valuta un’antenna esterna decente
- verifica con misure (SWR/VNA se puoi)

---

## Connettori & adattatori

Attenzione a:
- SMA vs RP-SMA
- U.FL / IPEX fragili
- adattatori economici (possono introdurre perdite o contatti ballerini)

---

## Troubleshooting RF rapido

### “Vedo pochi nodi”
- prova antenna diversa
- sposta il nodo vicino a finestra/alto
- controlla che l’antenna sia ben avvitata
- verifica che non sia un’antenna 433/915 venduta come “universale”

### “RSSI ok ma SNR pessimo”
- possibile rumore/interferenze
- migliorare posizione e lontananza da elettronica rumorosa
