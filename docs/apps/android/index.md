# App Android: panoramica

## Screenshot (Android)

<div class="screenshot-grid">
  <a href="../../assets/screenshots/android/android-home-empty.webp"><img src="../../assets/screenshots/android/android-home-empty.webp" alt="Fresh install: schermata Nodes vuota"></a>
  <a href="../../assets/screenshots/android/android-pairing-list.webp"><img src="../../assets/screenshots/android/android-pairing-list.webp" alt="Connessione: lista dispositivi Bluetooth"></a>
  <a href="../../assets/screenshots/android/android-nav-connected.webp"><img src="../../assets/screenshots/android/android-nav-connected.webp" alt="Connessione: nodo collegato"></a>
</div>

> Screenshot ufficiali dal sito Meshtastic (Android App).

L’app Meshtastic per Android è in genere la più “completa” e usata, e supporta connessioni via:

- Bluetooth
- Wi‑Fi / rete
- (in alcuni setup) USB/seriale tramite OTG

Questa sezione ti guida schermata per schermata, con attenzione alle differenze che contano davvero.

---

## Cosa trovi nell’app (macro)

- **Conversations / Messaggi**: chat per canale e DM (direct message)
- **Nodes**: elenco nodi, dettagli, distanza, hop, batterie, ecc.
- **Map**: posizione nodi, tracking, strumenti mappa
- **Settings / Config**: configurazioni del nodo (radio, canali, moduli)

---

## Prima configurazione (ordine raccomandato)

1. Connettiti al nodo (Bluetooth o Wi‑Fi)
2. Imposta:
   - **Regione**
   - **Preset LoRa**
3. Imposta canale:
   - nome + PSK
4. Verifica in “Nodes” che compaia il tuo nodo con nome corretto
5. Invia un messaggio sul canale primario

---

## Problemi tipici su Android

- permessi Bluetooth / posizione
- battery saver aggressivo (app che perde la connessione)
- pairing “sporco” dopo cambio firmware

Vedi **Troubleshooting** per la checklist completa.
