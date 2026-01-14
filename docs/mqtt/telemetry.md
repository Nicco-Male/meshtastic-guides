# Telemetria

Telemetria = dati “non chat”:
- batteria
- sensori
- qualità link
- stato nodo

---

## Frequenza: meno è meglio

In molte reti pubbliche:
- telemetria troppo frequente = congestione
- non serve il dato ogni 10 secondi per sapere che una batteria è al 78%

---

## Cosa pubblicare (idea pratica)

- batteria e stato nodo (utile)
- sensori ambientali (se servono davvero)
- qualità link (RSSI/SNR) per diagnosi

---

## Telemetria + MQTT

MQTT è perfetto per:
- database time series
- grafici (Grafana)
- alert (Telegram, ecc.)

Ma:
- evita topic pubblici “universali” per dati privati
- limita precisione e dettaglio dove serve
