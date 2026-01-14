# Modulo MQTT (client / proxy)

Il modulo MQTT sta **sul nodo** (firmware) e decide:
- cosa pubblicare sul broker
- cosa sottoscrivere dal broker
- quali topic usare

---

## Prerequisiti

- nodo con connettività IP (tipicamente ESP32 via Wi‑Fi)
- broker MQTT raggiungibile (locale o remoto)
- credenziali (se il broker le richiede)

---

## Config consigliata (approccio sicuro)

1. Pubblica solo ciò che ti serve (es. telemetria, non tutto)
2. Se la rete è pubblica: evita di inviare su MQTT dati sensibili (posizione precisa)
3. Usa topic chiari e “namespaced” (es: `msh/EU_868/...` oppure `nicco/...`)

---

## Opzioni da capire bene

- **Root topic**: il prefisso di tutti i topic
- **Pubblica posizione**: utile ma delicato
- **Pubblica telemetria**: ottimo per dashboard
- **Sottoscrizioni**: “porta dentro” messaggi dal broker alla mesh (da usare con cautela)

---

## Troubleshooting rapido

- Broker non raggiungibile → controlla DNS, firewall, rete
- Connesso ma niente dati → controlla filtri, topic, e se il nodo sta generando telemetria/posizione
- Dati “troppi” → stai pubblicando tutto, riduci scope o intervalli
