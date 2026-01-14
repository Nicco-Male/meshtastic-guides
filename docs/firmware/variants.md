# Varianti firmware (Italia)

![Scelta firmware (Italia)](../assets/diagrams/firmware-italy-choices.svg)


In Italia, nella pratica, trovi quasi sempre **due scelte**:

1) **Firmware ufficiale Meshtastic**
2) **Firmware LoraItalia (con patch)**

Questa pagina ti aiuta a scegliere senza confondere le idee.

---

## Prima regola: come si aggiorna davvero

Meshtastic **non aggiorna “over-the-air” via LoRa**.  
Per aggiornare firmware si usa **USB / DFU / flasher** a seconda del dispositivo.

> Quindi: prima di toccare un nodo remoto, pianifica come ci rimetti mano se qualcosa va storto.

---

## 1) Firmware ufficiale Meshtastic

È la scelta “standard”: documentazione, tool e flussi sono allineati con il progetto.

### Beta vs Alpha (in due righe)
- **Beta**: scelta consigliata per uso normale (più stabile).
- **Alpha**: per testare novità/fix recenti (più rischio).

### Flash: cosa aspettarti
Dipende dall’hardware:
- molte board **ESP32** usano web flasher / seriale
- molte **nRF52** usano DFU/UF2 (drag & drop) o DFU via tool

**Sempre:** fai backup config prima (vedi pagina *Backup/Restore*).

---

## 2) Firmware LoraItalia (con patch)

È un firmware basato su Meshtastic con modifiche pensate per l’ecosistema italiano.

### Cosa cambia (in pratica)
Dalle note pubbliche LoraItalia, le differenze più tipiche includono:
- impostazioni **MQTT** più “pronte” per i server/community
- comportamenti legati a **neighbor / collegamenti** (attenzione se fai da gateway)
- funzionalità abilitate/riaggiunte in base alle esigenze community

> Importante: **se un nodo è collegato a MQTT**, segui le raccomandazioni LoraItalia su cosa trasmettere o non trasmettere via LoRa, per non aumentare rumore/spam in mesh.

### Quando sceglierlo
- se vuoi un setup “Italia-friendly” con impostazioni già in linea con la community
- se segui le linee guida LoraItalia (soprattutto per MQTT/neighbor)

---

## Scelta rapida

- **Scegli ufficiale Meshtastic** se vuoi neutralità, compatibilità e doc ufficiale.
- **Scegli LoraItalia (patch)** se vuoi essere allineato alla community italiana e alle sue regole operative.

---

## Fonti (da consultare sempre, perché possono cambiare)
- Meshtastic docs: https://meshtastic.org/docs/
- LoraItalia: https://www.loraitalia.it/
