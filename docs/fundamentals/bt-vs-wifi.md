# Bluetooth vs Wi‑Fi (connessione all’app)

Meshtastic non è “solo un’app”: l’app è un telecomando per configurare e usare il **nodo**.

Per parlare col nodo dal telefono hai più opzioni, a seconda dell’hardware:

- **Bluetooth** (tipico su T‑Beam, T‑Deck, ecc.)
- **Wi‑Fi** (ESP32: può fare AP o collegarsi a una rete)
- **USB** (soprattutto da PC, o Android con OTG in certi casi)

---

## Bluetooth: pro e contro

✅ Pro
- Funziona anche senza rete Wi‑Fi
- Semplice per uso “sul campo”
- Consuma poco (in generale)

⚠️ Contro
- Portata limitata
- A volte pairing/caching può fare scherzi (specie dopo update)

Quando usarlo:
- configurazioni rapide
- messaggi e gestione da vicino al nodo

---

## Wi‑Fi: pro e contro

✅ Pro
- Puoi collegarti anche da più lontano (dipende dalla rete)
- Utile per nodi “fissi” (casa/ufficio) e per integrazioni

⚠️ Contro
- Devi gestire credenziali e rete
- Se l’AP del nodo è aperto, attenzione alla sicurezza

Quando usarlo:
- nodi fissi con accesso rete
- uso con MQTT / telemetria / servizi locali

---

## USB: quando ha senso

- Aggiornamenti / flashing
- Debug
- Uso con PC (CLI Meshtastic, script, ecc.)

---

## Checklist “non si connette”

1. Il nodo è acceso e vicino (Bluetooth) / raggiungibile (Wi‑Fi)?
2. L’app ha i permessi (BT, posizione su Android)?
3. Hai più app collegate allo stesso nodo? (possono confliggere)
4. Dopo un update, prova:
   - “Forget device” / rimuovi pairing
   - riavvia nodo e telefono
