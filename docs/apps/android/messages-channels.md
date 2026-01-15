# Android: messaggi & canali

<div class="screenshot-grid">
  <a href="../../assets/screenshots/android/android-message-states.webp"><img src="../../assets/screenshots/android/android-message-states.webp" alt="Icone stato messaggi"></a>
</div>

Questa pagina copre:

- invio messaggi su canali
- messaggi diretti (DM)
- gestione canali e PSK
- errori tipici (“non arriva”, “arriva in ritardo”, “vedo solo cifrato”)

---

## Conversations: come funziona

Di solito l’app mostra:
- una conversazione per **canale**
- conversazioni DM per singolo nodo (se supportato)

Tipi di invio:
- **Broadcast**: a tutti sul canale selezionato
- **Direct**: a un nodo specifico (DM)

---

## Canali: gestione pratica

### Cambio canale (per inviare su un altro canale)
1. Apri la schermata conversazione
2. Seleziona il canale dal menu (o tab)
3. Invia messaggio

### Creare / aggiungere un canale
- Vai nella sezione canali (settings/config)
- aggiungi canale secondario
- imposta nome + PSK
- salva sul nodo

### Condividere canali
- QR code / link (se presente)
- export configurazione (vedi Firmware → backup/restore)

---

## “Vedo nodi ma non leggo messaggi”

Quasi sempre significa:
- parametri radio ok (quindi “vedi” la rete)
- ma **PSK diversa** (quindi non puoi decifrare quel canale)

Soluzione:
- import corretto del canale (QR/link/config)
- verifica nome canale e PSK

---

## “Messaggi in ritardo / persi”

Cause comuni:
- preset troppo lento per la densità della rete
- hop limit alto
- troppa telemetria / range test
- RSSI/SNR scarsi (antenna / posizione)

Vedi anche: Fondamentali → hop limit & routing.
