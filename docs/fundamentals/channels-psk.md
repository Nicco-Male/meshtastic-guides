# Canali & chiavi (PSK)

In Meshtastic il concetto di “canale” è la combinazione di:

- Parametri radio (regione + modem preset / canale LoRa)
- **Nome canale**
- **PSK** (Pre-Shared Key) per cifrare i messaggi del canale

Se due nodi hanno parametri radio compatibili e condividono **lo stesso canale (nome + PSK)**, allora:
- possono **scambiarsi messaggi** su quel canale
- possono **inoltrare** pacchetti (rebroadcast) in base alla configurazione (hop limit, rebroadcast mode, ecc.)

---

## Canale primario vs canali aggiuntivi

- **Canale primario**: è quello “di default” (quello su cui finiscono molte cose se non specifichi altro).
- **Canali secondari**: puoi aggiungerne altri (es: “team”, “solo famiglia”, “test”).

Suggerimento pratico:  
tieni il canale primario “pulito” e usa un canale secondario per test/esperimenti.

---

## PSK: cosa fa e cosa NON fa

### Cosa fa
- Cifra **il contenuto** dei messaggi del canale (testo, payload applicativi) con una chiave condivisa.

### Cosa NON fa (importante)
- Non rende “invisibile” l’esistenza del traffico radio.
- Alcune informazioni di rete/packet header non sono cifrate nello stesso modo del payload.
- La sicurezza pratica dipende anche dal tuo comportamento (es: condividere QR e PSK ovunque…).

!!! warning "Sicurezza ≠ magia"
    La LoRa è un mezzo condiviso. La cifratura è fondamentale, ma non sostituisce il buon senso.

---

## Condivisione canale (QR / link)

Le app Meshtastic offrono metodi comodi per condividere un canale:
- QR code
- Link / stringa da copiare
- Import/export configurazione

Quando condividi, stai condividendo *almeno*:
- nome canale
- PSK
- (spesso) preset e parametri radio collegati

Quindi: condividi solo con persone e contesti che vuoi veramente nella tua rete.

---

## Best practice consigliate

### 1) Niente PSK “ovvie”
Evita:
- `1234`
- `password`
- `meshtastic`
- nomi pubblici tipo “LoraItalia” se vuoi un canale privato

### 2) Differenzia “pubblico” e “privato”
Se vuoi partecipare a una mesh pubblica:
- usa un canale “pubblico” con PSK condivisa dalla community (se prevista)
Se vuoi parlare solo tra tuoi nodi:
- usa un canale privato, PSK forte, e valuta di limitare hop e traffico.

### 3) Attenzione alla posizione
La posizione può finire in rete (radio) e talvolta anche su MQTT o mappe pubbliche.  
Valuta:
- precisione posizione
- intervalli di invio
- quando disabilitare del tutto

---

## Troubleshooting rapido

### “Non vedo nessuno / non mi rispondono”
Controlla:
- Stessa **regione**
- Stesso **modem preset**
- Stesso **nome canale + PSK**
- Nodi a distanza ragionevole / antenne ok

### “Vedo nodi ma non leggo messaggi”
Probabile:
- parametri radio compatibili (quindi li “vedi”)
- ma canale/PSK diverso (quindi i payload risultano cifrati per te)
