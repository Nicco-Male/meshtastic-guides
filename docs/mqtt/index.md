# MQTT & integrazioni

MQTT è il ponte tra Meshtastic e il mondo “IP”:
- home automation
- dashboard
- storage
- analisi telemetria
- bridge tra siti (con molta cautela)

Questa sezione è pratica: come abilitarlo, cosa pubblica, e come evitare di fare danni.

---

## Concetto chiave

Meshtastic può:
- pubblicare messaggi/telemetria su un broker MQTT
- (opzionale) ricevere messaggi da MQTT e inviarli nella mesh radio

!!! warning "MQTT non è sempre “solo telemetria”"
    Dipende da come configuri il modulo. In una mesh condivisa, la configurazione sbagliata può generare spam o leak di dati.

---

## Dove andare

- **Modulo MQTT (client/proxy)**: configurazione sul nodo
- **Bridge Mosquitto**: lato server (tua infrastruttura)
- **Telemetria**: come pubblicarla e usarla bene
