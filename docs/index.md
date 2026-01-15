# Meshtastic Guides (ITA)

Queste guide raccolgono **best practice** e procedure pratiche per usare Meshtastic in modo efficace (e senza trasformare la mesh in un… frullatore di pacchetti).

**Fonti principali**
- Documentazione ufficiale: https://meshtastic.org/
- Wiki e community italiana: https://www.loraitalia.it/

!!! note "Obiettivo del progetto"
    - Guide **dettagliate**, ma leggibili.
    - Focus operativo (cosa toccare, cosa non toccare, e perché).
    - Compatibile con **Android**, **iOS**, **Web Client**, firmware e MQTT.

---

## Cos’è Meshtastic (in 20 secondi)

Meshtastic è un ecosistema open source per creare una rete **mesh** a bassa potenza su radio LoRa (e non solo), pensata per messaggi, posizione e telemetria **anche senza Internet**.  
Ogni nodo può inoltrare (“rebroadcast”) i pacchetti, estendendo la copertura quando la rete è configurata bene.

---

## Quick Start super pratico (prima rete in 10 minuti)

1. **Scegli la regione**: per l’Italia di solito è `EU_868`.
2. **Scegli un preset LoRa** (modem preset): in Italia la community usa spesso `MediumFast`.
3. **Dai un nome al nodo** (short name + long name).
4. **Connettiti dall’app** (Bluetooth o Wi‑Fi) e invia un messaggio di test sul canale primario.
5. (Se serve) **condividi il canale** via QR / link (PSK e parametri devono combaciare).

👉 Trovi i dettagli nelle sezioni:
- **Fondamentali → Regione & preset LoRa**
- **App → Connessione**
- **Fondamentali → Canali & chiavi (PSK)**

---

## “Buon cittadino” della mesh (regole che salvano la rete)

La LoRa è potente, ma è anche una risorsa limitata: poche decine di byte alla volta e “time-on-air” prezioso.

### Impostazioni sane quasi sempre
- **Role**: `CLIENT` / `CLIENT_MUTE` / `CLIENT_BASE` (evita ruoli “strani” se non sai esattamente perché ti servono).
- **Max hops**: spesso `3` è il valore raccomandato. Aumentarlo ovunque è il modo più veloce per degradare la rete.
- **Telemetria**: non sparare aggiornamenti ogni 10 secondi. Scegli intervalli sensati.
- **Range test**: usalo per test, poi spegnilo (fa tantissimo traffico).

!!! tip "Se devi “pompare” una rete"
    Prima ottimizza **antenna**, **posizionamento**, **altezza**, **cavi**, e solo dopo ritocca parametri radio.

---

## Privacy & sicurezza (no paranoia, solo lucidità)

- La **crittografia** protegge il contenuto dei messaggi su canali privati, ma non “magicamente” tutto.
- Pubblicare posizione/telemetria su MQTT può rendere dati visibili oltre la tua rete locale.
- Imposta con cura la **precisione posizione** e valuta quando inviarla.

---

## Struttura del sito

- **Fondamentali**: concetti base (canali, PSK, preset, hop/routing, connessioni).
- **App**: Android, iOS e “cosa cambia davvero”.
- **Firmware**: update, preset, backup/restore config.
- **Hardware**: antenne, alimentazione, GPS/sensori.
- **MQTT**: modulo MQTT, bridge Mosquitto, telemetria.
- **Mappe**: offline, tile, device UI (T‑Deck, ecc.).
- **Reference**: glossario + changelog del sito.

---

## Contribuire (velocissimo)

Questo repo è pensato per essere “forkabile” e migliorabile:

1. Apri una issue (“manca questa funzione”, “questa guida è confusa”, “serve screenshot”).
2. Oppure fai una PR con modifiche ai `.md`.

Linee guida e template: **Come usare queste guide**.
