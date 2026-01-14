# Varianti firmware (Italia)

In Italia, nella pratica, ti imbatti quasi sempre in **due “famiglie”** di firmware:

1) **Firmware ufficiale Meshtastic** (upstream)  
2) **Firmware con patch LoraItalia** (fork basato su Meshtastic)

Questa pagina ti aiuta a scegliere senza farti prendere in ostaggio dalle leggende metropolitane.

---

## Prima regola: cosa non è possibile

Meshtastic **non supporta aggiornamenti OTA via LoRa**: per aggiornare devi usare USB / DFU / flasher, a seconda dell’architettura.  
(Tradotto: niente “update over the air” via radio.)

---

## 1) Firmware ufficiale Meshtastic (upstream)

È il firmware “standard” del progetto Meshtastic.

### Release: Beta vs Alpha
Meshtastic pubblica due tipi di release:

- **Beta**: consigliata nella maggior parte dei casi (stabilità migliore).
- **Alpha**: per chi vuole testare novità e fix più recenti, accettando più rischio di bug/instabilità.

### Dove si scarica / come si flasha
- **Downloads & Web flasher**: il modo più semplice per ESP32 e in generale per iniziare.
- **Drag & drop / UF2**: per molte board nRF52 / RP2040 (modalità bootloader → copi il file).

---

## 2) Firmware con patch LoraItalia (Italia)

LoraItalia mantiene un firmware **basato sul firmware Meshtastic**, con patch pensate per l’ecosistema italiano.

### Cosa cambia (in sintesi)
Dalla documentazione LoraItalia, tra le modifiche più rilevanti:

- **Traceroute** richiedibile più spesso: intervallo minimo **5 secondi** (invece di 30s).
- **Topic MQTT di default** già impostato per essere pronto al server italiano.
- **Remote hardware module** (GPIO remoto) riaggiunto/riattivato.
- **Loghi e riferimenti** aggiornati (branding LoraItalia).
- **Neighbor**: trasmissione riattivata sul canale primario (ripristino comportamento precedente).
  - Per far “tornare” le linee neighbor in mappa: riattiva il modulo e abilita “Transmit over LoRa”.
  - Nota LoraItalia: **i nodi connessi a MQTT devono tenere “Transmit over LoRa” DISATTIVATO**.
- **MQTT forwarding**: “tutti i pacchetti verranno reinoltrati sulla rete indipendentemente dal flag OkToMqtt”.

> In pratica: ci sono scelte “opinionate” su neighbor e forwarding. Ottime se sai cosa vuoi, pericolose se fai da gateway senza capire il flusso.

### Firmware precompilati e “on demand”
LoraItalia:
- pubblica firmware precompilati per i device più comuni
- offre anche un servizio “on demand” per fissare nel firmware parametri come `longName`, `shortName`, `region`, `modem preset`  
  (utile per nodi remoti: maggiore resilienza se si corrompe il filesystem)

Sulla pagina LoraItalia trovi anche una **versione consigliata** “in questo momento” (ad esempio, in una fase è stata indicata 2.6.10): controlla sempre la pagina perché può cambiare.

### Come flashare (nota pratica)
- **nRF52**: tipicamente DFU/UF2 (flusso standard).
- **ESP32**: LoraItalia segnala che con il flasher ufficiale non sempre si ha successo su alcune schede e propone un flusso alternativo.
  - Se segui questa strada: fai SEMPRE **backup config + chiavi** perché alcune modalità di flash (es. `.factory` a `0x0`) possono essere **distruttive**.

---

## Quale scegliere? (scelta rapida)

### Scegli *Meshtastic ufficiale* se…
- vuoi stare “upstream”, con compatibilità ampia e doc ufficiali
- sei fuori dal contesto LoraItalia o vuoi una configurazione neutra
- vuoi provare feature nuove (Alpha) appena escono

### Scegli *LoraItalia patch* se…
- ti interessa l’integrazione pronta per l’ecosistema italiano (MQTT/topic default, behavior specifici, ecc.)
- vuoi usare le patch “di comunità” (neighbor, remote hardware, ecc.) seguendo le raccomandazioni LoraItalia

---

## Compatibilità tra nodi (mix firmware)
In generale i nodi Meshtastic parlano lo stesso “linguaggio” di base, ma:
- alcune funzioni possono comportarsi diversamente (es. neighbor/MQTT forwarding)
- i default (topic, moduli, policy) possono cambiare

Se fai da gateway MQTT, evita esperimenti creativi in produzione: prova prima in laboratorio.

---

## Fonti
- Meshtastic: FAQ, Downloads, Flashing firmware  
  - https://meshtastic.org/docs/faq/  
  - https://meshtastic.org/downloads/  
  - https://meshtastic.org/docs/getting-started/flashing-firmware/
- LoraItalia: Firmware LoraItalia + repo patch  
  - https://www.loraitalia.it/firmware-loraitalia/
  - https://github.com/LoraItalia/loraitalia-firmware
