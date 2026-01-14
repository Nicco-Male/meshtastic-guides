# Aggiornare firmware (senza farsi male)

Meshtastic gira su tanti device diversi (ESP32, nRF52, ecc.), quindi il metodo di update dipende dall’hardware.

---

## Metodo 1 — Web Flasher (spesso il più comodo)

Per molti device è disponibile un flasher web:
- scegli il modello
- metti il device in modalità flash
- carichi il firmware

Pro:
- facile
- riduce errori “a mano”

Contro:
- richiede browser compatibile e permessi USB

---

## Metodo 2 — UF2 / drag&drop (tipico nRF52)

Alcuni device entrano in modalità “storage” e accettano un file UF2 tramite copia-incolla.

---

## Metodo 3 — CLI / script (power user)

Utile per:
- automazioni
- debug
- CI in laboratorio

---

## Cosa controllare dopo un update

- Regione e preset non siano tornati default
- Canali presenti e corretti
- Moduli (MQTT/telemetria) ancora configurati
- Connessione BT/Wi‑Fi stabile

!!! tip "Se dopo update è instabile"
    Spesso risolvi con:
    - forget pairing BT
    - reimport configurazione
    - riavvio completo del nodo
