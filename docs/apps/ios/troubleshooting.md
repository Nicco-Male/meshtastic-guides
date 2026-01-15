# iOS: troubleshooting

Quando qualcosa “non torna”, di solito è uno di questi tre: **connessione**, **regione/LoRa**, **canali/chiavi**.

---

## Non trova il nodo in Bluetooth

Checklist rapida:

- Bluetooth acceso sul telefono
- Nodo vicino (pochi metri per il primo pairing)
- App aggiornata
- Riavvio del nodo (sì, anche lui ha bisogno di una “reset therapy”)

<div class="screenshot-grid">
  <a href="../../assets/screenshots/ios/ios-connect-01.png" class="glightbox" data-gallery="ios-tr-connect"><img src="../../assets/screenshots/ios/thumbs/ios-connect-01.webp" alt="Connect 01"></a>
  <a href="../../assets/screenshots/ios/ios-connect-02.png" class="glightbox" data-gallery="ios-tr-connect"><img src="../../assets/screenshots/ios/thumbs/ios-connect-02.webp" alt="Connect 02"></a>
  <a href="../../assets/screenshots/ios/ios-bluetooth-01.png" class="glightbox" data-gallery="ios-tr-connect"><img src="../../assets/screenshots/ios/thumbs/ios-bluetooth-01.webp" alt="Bluetooth 01"></a>
</div>

---

## Si connette ma non vede nodi / non arrivano messaggi

Qui spesso il colpevole è **Regione/Preset LoRa** o **canali/PSK**.

- Controlla che la **regione** sia corretta (Italia = EU_868)
- Verifica il preset LoRa/Modem e la potenza (se tocchi cose a caso, addio copertura)
- Controlla che tu e gli altri siate sullo **stesso canale** e con la **stessa PSK** (se cifrato)

<div class="screenshot-grid">
  <a href="../../assets/screenshots/ios/ios-lora-01.png" class="glightbox" data-gallery="ios-tr-lora"><img src="../../assets/screenshots/ios/thumbs/ios-lora-01.webp" alt="Lora 01"></a>
  <a href="../../assets/screenshots/ios/ios-lora-02.png" class="glightbox" data-gallery="ios-tr-lora"><img src="../../assets/screenshots/ios/thumbs/ios-lora-02.webp" alt="Lora 02"></a>
</div>

---

## Mappa vuota / posizioni non compaiono

- Il nodo deve avere **posizione** (GPS o posizione manuale) e deve essere autorizzato a condividerla
- Se la posizione arriva raramente, aumenta l’intervallo solo quanto serve (per non intasare la rete)

<div class="screenshot-grid">
  <a href="../../assets/screenshots/ios/ios-map-01.png" class="glightbox" data-gallery="ios-tr-map"><img src="../../assets/screenshots/ios/thumbs/ios-map-01.webp" alt="Map 01"></a>
  <a href="../../assets/screenshots/ios/ios-map-02.png" class="glightbox" data-gallery="ios-tr-map"><img src="../../assets/screenshots/ios/thumbs/ios-map-02.webp" alt="Map 02"></a>
  <a href="../../assets/screenshots/ios/ios-position-01.png" class="glightbox" data-gallery="ios-tr-map"><img src="../../assets/screenshots/ios/thumbs/ios-position-01.webp" alt="Position 01"></a>
  <a href="../../assets/screenshots/ios/ios-position-02.png" class="glightbox" data-gallery="ios-tr-map"><img src="../../assets/screenshots/ios/thumbs/ios-position-02.webp" alt="Position 02"></a>
</div>

---

## MQTT non funziona (se lo usi)

- Host/porta/credenziali corrette
- Topic giusto (e regione corretta nel path)
- Se usi un broker pubblico: attenzione ai limiti e alla privacy

<div class="screenshot-grid">
  <a href="../../assets/screenshots/ios/ios-mqtt-01.png" class="glightbox" data-gallery="ios-tr-mqtt"><img src="../../assets/screenshots/ios/thumbs/ios-mqtt-01.webp" alt="Mqtt 01"></a>
  <a href="../../assets/screenshots/ios/ios-mqtt-02.png" class="glightbox" data-gallery="ios-tr-mqtt"><img src="../../assets/screenshots/ios/thumbs/ios-mqtt-02.webp" alt="Mqtt 02"></a>
  <a href="../../assets/screenshots/ios/ios-mqtt-03.png" class="glightbox" data-gallery="ios-tr-mqtt"><img src="../../assets/screenshots/ios/thumbs/ios-mqtt-03.webp" alt="Mqtt 03"></a>
</div>

---

## Dopo un update firmware

- “Dimentica” il dispositivo in iOS e rifai pairing
- Se hai cambiato regione/preset: ripassa le impostazioni LoRa
