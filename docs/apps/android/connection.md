# Android: connessione al nodo (Bluetooth / Wi‑Fi)

Questa guida assume che il nodo sia già acceso.

---

## Bluetooth (consigliato per iniziare)

### 1) Permessi (prima volta)
Su Android, l’app richiede permessi per:
- Bluetooth
- (spesso) posizione / Nearby devices

Concedili, altrimenti la scansione non trova nulla.

### 2) Pairing + connessione
1. Apri l’app Meshtastic
2. Vai su **Connect / Devices** (il nome può variare)
3. Avvia la scansione Bluetooth
4. Seleziona il tuo dispositivo
5. Attendi che compaia “Connected”

!!! tip "Se non compare"
    - avvicina il telefono al nodo
    - disattiva/riattiva Bluetooth
    - riavvia il nodo

---

## Wi‑Fi / IP (utile per nodi fissi)

Esistono due scenari comuni:

### A) Nodo in modalità Access Point (AP)
- Il nodo crea una rete Wi‑Fi (SSID del nodo)
- Ti colleghi dal telefono a quella rete
- Nell’app inserisci/usa l’IP del nodo (spesso `192.168.4.1`, dipende dal firmware)

### B) Nodo collegato alla tua rete (client)
- Il nodo è sulla tua LAN
- Tu inserisci l’IP del nodo nell’app e ti colleghi

Consiglio: per nodi “in casa/ufficio”, usa la modalità client, così eviti AP aperti.

---

## “Connected ma non risponde”

Sintomi:
- l’app dice “connected”
- ma non ricevi nodi / non invii messaggi

Checklist:
1. Sei collegato al **nodo giusto**?
2. Il nodo ha appena cambiato firmware e l’app ha cache vecchia?
3. Se sei in Wi‑Fi: l’IP è corretto? hai conflitti di rete?

---

## Disconnessione pulita

Prima di cambiare dispositivo o provare un’altra modalità:
- usa “Disconnect” nell’app (se presente)
- poi disattiva BT/Wi‑Fi e riattiva

Questo riduce i casi di “connessione zombie”.
