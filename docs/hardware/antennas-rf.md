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

---

## Troubleshooting avanzato (antenne, rumore, normativa)

### “Portata bassa nonostante antenna buona”
Possibili cause:
- antenna **fuori banda** (es. 915 MHz usata su 868 MHz)
- cavo lungo o scadente (perdite reali)
- connessione SMA/U.FL non serrata o con adattatore difettoso

### “Messaggi instabili o RSSI che oscilla”
Controlla:
- **interferenze locali** (alimentatori, router Wi‑Fi, dispositivi industriali)
- posizione: allontanati da metallo e schermature
- prova a spostare il nodo di 1–2 metri (a volte cambia tutto)

### “Dubbi sulla banda/regione”
Se la regione è sbagliata:
- potresti essere **fuori legge** (potenza/frequenza)
- potresti **non agganciare** gli altri nodi

Se hai nodi in Paesi diversi, verifica:
- **EU_868** vs **US_915/AU_915**
- canali e limiti di potenza/duty‑cycle specifici
