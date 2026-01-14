# Backup / restore configurazione

Questa è la tua assicurazione: ti salva quando:
- cambi firmware
- cambi telefono
- cloni un nodo
- ti esplode una configurazione sperimentale

---

## Opzione A — Export/Import da app

Molte app permettono:
- esportare config
- importare config
- condividere via file/QR

È comodo, ma a volte non include tutto o può essere “version-sensitive”.

---

## Opzione B — CLI Meshtastic (consigliato per backup serio)

Da PC puoi usare la CLI ufficiale `meshtastic` per esportare/importare la configurazione.

Esempio (seriale):
```bash
meshtastic --port /dev/ttyACM0 --export-config > backup.yaml
```

Per ripristinare:
```bash
meshtastic --port /dev/ttyACM0 --configure backup.yaml
```

Nota:
- la porta cambia (`/dev/ttyUSB0`, `/dev/ttyACM0`, COMx su Windows)
- su Wi‑Fi esistono modalità equivalenti (dipende dal setup)

---

## Best practice

- nomina i backup con data + nome nodo
- conserva i file in un posto sicuro (PSK inclusa!)
- se condividi screenshot/config, oscura PSK
