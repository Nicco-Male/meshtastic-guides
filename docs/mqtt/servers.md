# Server MQTT & credenziali

Questa pagina serve a **collegare bene** tre mondi diversi:

1) **Il tuo broker** (privato: controlli tu ACL, TLS, retention, ecc.)
2) **Il broker pubblico Meshtastic** (globale, con regole/limiti)
3) **LoraItalia** (ecosistema/community italiana: linee guida e firmware dedicato)

> Nota di sopravvivenza: **non mettere password reali in una repo pubblica.**
> In queste guide mettiamo *solo* credenziali “pubbliche” e/o **placeholder**.

---

## 1) Il broker pubblico Meshtastic (default)

Se **non imposti** `mqtt.address` (e spesso anche user/pass), Meshtastic usa il **server pubblico** di default.

Valori di default (firmware/CLI):
- **Address:** `mqtt.meshtastic.org`
- **Username:** `meshdev`
- **Password:** `large4cats`

### Restrizioni importanti (per non fare danni)
Il broker pubblico applica limitazioni per non trasformare LoRa in un tostapane in fiamme:

- **Zero-hop policy:** i pacchetti ricevuti da MQTT arrivano ai nodi collegati, ma non “rimbalzano” poi nella mesh come un’epidemia.
- **Filtri di traffico:** con la PSK di default vengono privilegiati solo alcuni tipi di pacchetto (testi, posizione, telemetria, routing, ecc.).
- **Precisione posizione ridotta** sul canale di default per privacy.

### Quando NON usarlo
Meshtastic consiglia di **non usare la PSK di default su broker privati**, perché rischi di importare traffico “pubblico” in una rete che non ha i filtri del server pubblico.
Per i broker privati: canali privati + PSK private, sempre.

---

## 2) LoraItalia (server “italiano” e buone pratiche)

LoraItalia ragiona in termini di mesh efficiente (client/router/gateway) e il **gateway** è il nodo che instrada su un broker MQTT via Internet.

Sul loro firmware dichiarano che:
- il **topic MQTT di default** è già pronto per collegarsi al “server italiano”
- ci sono regole operative specifiche (es. nota sui neighbor e sull’uso di “Transmit over LoRa” per nodi connessi a MQTT)

⚠️ **Cosa NON mettiamo qui (finché non è pubblico in modo chiaro):**
host/porta/credenziali “LoraItalia” se non sono pubblicate in una pagina ufficiale.
In pratica: in questa guida lasciamo i campi come placeholder e mettiamo il link alla loro documentazione/forum.

Esempio (placeholder):
- **Address:** `BROKER_LORAITALIA_HOST:1883`
- **Username:** `BROKER_LORAITALIA_USER`
- **Password:** `BROKER_LORAITALIA_PASS`
- **Root topic:** (dipende dalla rete; spesso `msh/EU_868` o simili)

---

## 3) Il tuo broker (consigliato per reti serie)

Se vuoi stabilità e controllo, fai così:

### A) Organizza bene i topic
Usa un **root topic dedicato** per separare reti/regioni e fare ACL pulite. Meshtastic usa di default `msh/REGION`, ma puoi cambiarlo proprio per questo.

Esempi pratici:
- `msh/EU_868` (standard “pubblico” per regione)
- `msh/EU_868/NiccoMesh` (tua dorsale / tua community)
- `msh/EU_868/NiccoMesh/lab` (ambiente test)

### B) Sicurezza minima (non negoziabile)
- **TLS** se esponi il broker su Internet.
- **ACL per topic** (ogni gateway deve pubblicare/leggere solo dove serve).
- **Password in `.env`** o in secret manager (mai nel repo).

### C) Esempio Mosquitto (super base)
> Questo è un esempio “pattern”, non una config completa.

```
# listener 1883
allow_anonymous false
password_file /etc/mosquitto/passwd

# ACL: ogni user vede solo il suo sotto-albero
acl_file /etc/mosquitto/acl
```

E ACL tipo:

```
user gateway_faeta
topic readwrite msh/EU_868/NiccoMesh/faeta/#
```

---

## Checklist rapida (gateway Meshtastic)
1) Imposta **wifi/ethernet** sul nodo
2) Abilita **MQTT**
3) Imposta **address/user/pass**
4) Imposta **root topic**
5) Abilita **uplink/downlink** solo dove serve (canali)
6) Testa con `mosquitto_sub` su `.../#` (su un ramo piccolo, non su tutto il mondo 😄)
---

## Regola operativa (consiglio Italia)
In molte reti/community italiane, **MQTT viene usato come telemetria/ingest** (mappe, dashboard, storico),
non per “rimbalzare pacchetti” e amplificare traffico.

Se fai bridge tra broker, fallo in modo **selettivo** (topic filtrati, niente loop) e con regole chiare.
