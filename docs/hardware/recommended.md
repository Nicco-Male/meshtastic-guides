# Hardware consigliato

Questa pagina non è una “classifica universale”: è una guida pratica per scegliere **in base all’uso**.

Meshtastic gira su tantissimi dispositivi (RAK, LILYGO, Heltec, Seeed, ecc.) e l’elenco ufficiale è lungo.
Qui lo rendiamo digeribile.

---

## 1) Nodo “client” (da tasca / da zaino)

### T-Deck (chat e tastiera)
È un dispositivo standalone con **schermo + tastiera**.
Pro:
- ottimo per chattare senza telefono
- Wi‑Fi + BT integrati (ESP32‑S3)
Contro:
- consumi tipicamente più alti rispetto a nRF52 (dipende da uso display/Wi‑Fi)

### T-Echo (autonomia)
All‑in‑one con e‑ink e GPS, basato su **nRF52840 “low‑power”** per lunga durata batteria.
Pro:
- autonomia ottima
- GPS integrato
Contro:
- niente Wi‑Fi (di solito non serve su un client)
- JSON su MQTT non supportato su nRF52 (se ti interessa fare gateway con JSON)

---

## 2) Nodo fisso “router” (solare / dorsale)

Qui vince la triade: **bassi consumi + SX1262 + stabilità**.

### Heltec Mesh Node T114 (nRF52840 + SX1262)
È in lista ufficiale come modello nRF52840 + SX1262, con GPS opzionale.
Per un nodo fisso:
- nRF52840 = profilo consumi più favorevole
- perfetto per ruolo router / repeater (soprattutto se alimentato a batteria/solare)

### RAK / WisMesh basati su nRF52840
Esempio: WisMesh Pocket V2 (nRF52840 + SX1262).
RAK ha anche un ecosistema di moduli (GPS, RTC, sensori, ethernet).

---

## 3) Gateway MQTT (LoRa ↔ Internet)

Se il nodo deve fare davvero da ponte MQTT, ti serve:
- **connessione Internet** (Wi‑Fi o Ethernet)
- stabilità energetica (spesso alimentazione fissa)

Esempio in lista ufficiale:
- **WisMesh WiFi MQTT Gateway** (ESP32 + SX1262, quindi Wi‑Fi presente).

---

## 4) Una regola che batte tutto: antenna e posizionamento
Hardware “top” con antenna scarsa = performance da citofono rotto.

Parti così:
1) antenna decente
2) altezza e visuale
3) solo dopo: cambiare board o preset

---

## Mini-consigli d’acquisto (pratici)
- **Vuoi autonomia?** guarda nRF52840.
- **Vuoi Wi‑Fi/MQTT on-board?** spesso ESP32‑S3.
- **Vuoi “testare e smanettare”?** ESP32 va benissimo, ma occhio ai consumi in campo.

