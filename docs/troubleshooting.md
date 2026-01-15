# Troubleshooting & FAQ

Risoluzione rapida dei problemi più comuni in Meshtastic. Se il problema persiste, raccogli **log**, **versione app/firmware** e **modello dispositivo** prima di aprire una issue.

## Connessione app (Bluetooth/Wi‑Fi)

**Sintomi**: la radio non appare, pairing fallisce, connessione instabile.

**Soluzioni rapide**:
- Attiva/disattiva il Bluetooth (o il Wi‑Fi) e riavvia l’app.
- Verifica che il dispositivo non sia già connesso a un altro telefono.
- Aggiorna all’ultima versione di app e firmware compatibili.
- Su Android, consenti **Posizione** per la scansione BLE.
- Su iOS, controlla l’autorizzazione Bluetooth nelle impostazioni.

## GPS non aggancia

**Sintomi**: posizione assente o aggiornata raramente.

**Soluzioni rapide**:
- Attendi alcuni minuti all’aperto (prima acquisizione più lenta).
- Verifica che l’antenna GPS sia collegata e supportata dal board.
- Controlla che il modulo GPS sia abilitato nella configurazione.

## MQTT non riceve dati

**Sintomi**: nessun messaggio su broker o topic vuoti.

**Soluzioni rapide**:
- Ricontrolla **broker, porta, username/password**.
- Verifica che il dispositivo abbia connettività Internet.
- Controlla la corretta configurazione dei **topic** e del namespace.
- Prova con un client MQTT esterno (es. mosquitto_sub) per isolare il problema.

## Range test scarso

**Sintomi**: pochi nodi visibili, pacchetti persi.

**Soluzioni rapide**:
- Controlla **antenna**, connettori e frequenza corretta.
- Evita ostacoli e prova con line-of-sight.
- Riduci data rate o usa preset LoRa più robusti.
- Verifica che tutti i nodi usino **regione** e **preset** compatibili.

## Quando aprire una issue

Prima di segnalare un bug, prepara:
- Versione app e firmware.
- Modello dispositivo e regione LoRa.
- Passi per riprodurre il problema.
- Log o screenshot rilevanti.
