# Glossario

Termini che trovi spesso in Meshtastic (e cosa vogliono dire davvero).

---

## Airtime (Time-on-air)
Tempo durante il quale un pacchetto occupa il canale radio. In LoRa è una risorsa preziosa.

## Band / Regione
Impostazioni che definiscono frequenze e vincoli legali (es. `EU_868`).

## Broadcast
Messaggio inviato a tutti i nodi che ascoltano quel canale.

## Channel (Canale)
Combinazione di nome + PSK + (in pratica) parametri radio compatibili.

## Client / Router / Repeater (Role)
Ruolo del nodo, che influenza comportamento e inoltro pacchetti.

## DM (Direct Message)
Messaggio diretto a un nodo specifico.

## Hop
“Salto” da un nodo al successivo. Un pacchetto può attraversare più hop.

## Hop limit / Max hops
Numero massimo di inoltri consentiti per un pacchetto (TTL della mesh).

## LoRa (Modulation)
Modulazione radio a spettro espanso, ottima per lunga portata e basso consumo.

## Modem preset
Preset LoRa (LongFast, MediumFast, …). Determina il compromesso portata/airtime.

## MQTT
Protocollo publish/subscribe usato per integrare nodi con servizi IP e dashboard.

## Node
Un dispositivo Meshtastic (radio + firmware) con un’identità e configurazione.

## PSK (Pre-Shared Key)
Chiave condivisa del canale, usata per cifrare i messaggi del canale.

## RSSI / SNR
Indicatori di qualità del segnale radio:
- RSSI = potenza del segnale ricevuto
- SNR = rapporto segnale/rumore

## Telemetry
Dati non chat (batteria, sensori, stato nodo).
