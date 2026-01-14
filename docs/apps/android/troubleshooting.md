# Android: troubleshooting

Checklist ordinata per probabilità (le cause più comuni in alto).

---

## 1) Non trova il nodo in Bluetooth

- [ ] Bluetooth acceso
- [ ] Permessi concessi (Bluetooth / dispositivi vicini / posizione)
- [ ] Nodo vicino (1–2 metri per test)
- [ ] Il nodo non è già collegato a un altro telefono/app
- [ ] Riavvia nodo e telefono

---

## 2) Si connette ma poi “sparisce”

Cause comuni:
- battery saver / ottimizzazione aggressiva
- app in background terminata

Soluzioni:
- escludi l’app da ottimizzazione batteria
- tieni lo schermo acceso durante la prima configurazione

---

## 3) Wi‑Fi: l’IP non risponde

- [ ] Sei sulla rete giusta?
- [ ] L’IP del nodo è corretto?
- [ ] Il nodo è in modalità AP o client come credi?
- [ ] Firewall o isolamento client sulla rete?

---

## 4) Messaggi non arrivano

- [ ] Regione + preset corretti
- [ ] Canale + PSK corretti
- [ ] Hop limit sensato
- [ ] RSSI/SNR accettabili (antenna/posizione)

---

## 5) Dopo update firmware “è tutto strano”

- Rimuovi pairing BT e riconnetti
- Reimporta configurazione (se hai backup)
- Verifica che regione/preset non siano tornati default
