# Android: configurazioni principali

La configurazione “vera” sta sul **nodo**. L’app è l’interfaccia.

Quasi tutte le opzioni importanti stanno in 4 aree:

1. **Radio / LoRa** (regione, preset, potenza, ecc.)
2. **Canali** (nome + PSK, secondari)
3. **Posizione** (GPS, intervalli, precisione, posizione fissa)
4. **Moduli** (MQTT, telemetria, range test, ecc.)

---

## Radio / LoRa (priorità alta)

Impostazioni tipiche:
- Regione (`EU_868` in Italia)
- Modem preset (es: `MediumFast`)
- (Se presente) potenza TX e limiti regionali

!!! tip "Se cambi regione o preset"
    Fallo all’inizio, poi riavvia il nodo e riconnetti l’app.
    Riduci i “fantasmi” dovuti a cache/riconfigurazioni parziali.

---

## Posizione

Opzioni tipiche:
- GPS on/off
- intervallo update
- precisione (se disponibile)
- “fixed position” per nodi fissi (se supportato)

---

## Risparmio energetico

Su nodi a batteria:
- disabilita cose non necessarie (display sempre acceso, BT sempre attivo, ecc.)
- limita telemetria frequente
- evita ruoli da router se non serve

---

## Salvare e ripristinare

Per backup/restore serio (anche quando cambi firmware):
- usa export/import configurazione (vedi Firmware → backup/restore)
