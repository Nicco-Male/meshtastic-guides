# Bridge Mosquitto (server side)

Un “bridge” Mosquitto collega due broker MQTT:
- puoi ricevere topic da un broker remoto
- e ripubblicarli localmente (o viceversa)

Uso tipico in Meshtastic:
- importare feed pubblici (con filtro severo)
- alimentare dashboard locali
- unificare telemetria da più siti

---

## Regola d’oro: filtra!

Non fare subscribe “a tutto” (es. `msh/#`) a meno che tu sappia cosa stai facendo:
- consumo banda
- storage
- spam
- rischio di leak dati

---

## Pattern consigliato

- un broker “edge” vicino ai nodi
- un broker “core” per storage/dash
- bridge solo su topic selezionati (telemetria, map report, ecc.)

---

## Debug rapido

- usa `mosquitto_sub` su topic specifici
- abilita log di mosquitto
- testa prima senza bridge, poi aggiungi un collegamento alla volta
