# Alimentazione & solare

Meshtastic brilla quando un nodo può stare acceso per giorni/mesi:
- batteria
- pannello solare
- power management sensato

---

## Batteria: concetti base

- Quasi tutti i nodi usano LiPo / Li-Ion (1S)
- La capacità reale dipende moltissimo da:
  - preset e traffico
  - display (se presente)
  - GPS
  - Bluetooth / Wi‑Fi
  - moduli attivi

---

## Solare (idea generale)

Obiettivo:
- avere un pannello che copra consumi medi + ricarica batteria
- usare un charge controller decente (o integrato sul device)

Consigli pratici:
- dimensiona il pannello in modo conservativo (inverno ≠ estate)
- evita di tenere display sempre acceso
- limita telemetria troppo frequente

---

## Power saving “soft” (senza saldatore)

- disabilita cose non necessarie (Wi‑Fi se non serve)
- usa intervalli lunghi per telemetria
- spegni LED se possibile
- valuta “position fixed” per nodi fissi

---

## Power saving “hard” (per smanettoni)

- regolatori più efficienti
- controllo profondo periferiche
- sensori a basso consumo
- firmware/branch ottimizzati (se disponibili)
