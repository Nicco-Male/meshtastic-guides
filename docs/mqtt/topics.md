# Topic e sotto-topic (Meshtastic su MQTT)

![Albero mentale dei topic](../assets/diagrams/mqtt-topic-tree.svg)


Qui mettiamo ordine nel caos: **la struttura dei topic** è il vero “cavo di rete mentale” di Meshtastic su MQTT.

---

## Root topic: il primo taglio “grosso”

Se non configuri un root topic, Meshtastic usa di default:

`msh/REGION`

Esempi:
- `msh/EU_868`
- `msh/EU_433`
- `msh/US`

Il root topic serve anche per ACL: separi reti diverse sullo stesso broker.

---

## Due famiglie di topic: protobuf e JSON

Per ogni canale dove abiliti uplink e/o downlink, Meshtastic usa **topic diversi**.

### 1) Protobuf (raw MeshPackets)
Topic:

`msh/REGION/2/e/CHANNELNAME/USERID`

- `CHANNELNAME` = nome canale (es. `LongFast`)
- `USERID` = id nodo in formato esadecimale con `!` (es. `!abcd1234`)
- Nota: firmware < 2.3.0 pubblicava con `/c/` al posto di `/e/`.

Esempio:

`msh/US/2/e/LongFast/!abcd1234`

Payload: protobuf. Se `encryption_enabled=true`, il payload resta cifrato con la chiave del canale.

### 2) JSON (solo alcuni portnum)
Se abiliti `JSON Enabled`, alcuni tipi di pacchetto vengono serializzati in JSON e finiscono in:

`msh/REGION/2/json/CHANNELNAME/USERID`

⚠️ JSON **non è supportato su nRF52**.

Meshtastic elenca i portnum serializzati (testo, telemetria, nodeinfo, posizione, waypoint, ecc.).

---

## “Sotto-topic” utili per inviare comandi dalla parte IP → mesh

Esiste anche un canale “trucchetto” per dire a un gateway di inviare roba sulla mesh via MQTT:

Topic:

`msh/REGION/2/json/mqtt/`

Per farlo funzionare:
- crea un canale Meshtastic chiamato **mqtt**
- abilita **Downlink**
- riavvia il device

Formato envelope (semplificato):

```json
{
  "from": 2130636288,
  "to": -1,
  "type": "sendtext",
  "payload": "ciao mesh"
}
```

Tipi supportati: `sendtext`, `sendposition`.

---

## Pattern pratico per “sezionare bene” (senza impazzire)

### 1) Taglia per regione (sempre)
- `msh/EU_868/...`
- `msh/EU_433/...`

### 2) Taglia per rete/community (se broker privato)
Metti un root topic tuo:
- `msh/EU_868/NiccoMesh/...`

### 3) Taglia per sito/gateway
- `.../faeta/...`
- `.../ufficio/...`

Così puoi fare ACL e bridge Mosquitto senza “aspirare il mondo intero”.

---

## Debug veloce
- Vedere solo JSON (più leggibile):
  - `mosquitto_sub -t 'msh/EU_868/2/json/#' -v`
- Vedere tutto (protobuf incluso): utile solo per test brevi:
  - `mosquitto_sub -t 'msh/EU_868/#' -v`

