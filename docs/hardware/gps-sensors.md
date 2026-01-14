# GPS & sensori

La posizione è una delle funzioni più utili di Meshtastic, ma va gestita bene.

---

## GPS: cosa serve davvero

- Per nodi **mobili**: GPS con fix rapido e invio a intervalli sensati
- Per nodi **fissi**: spesso conviene una **posizione fissa** (se supportata) invece di tenere un GPS sempre acceso

---

## Precisione e frequenza

- Precisione alta + invio frequente = più traffico + più consumo
- Precisione “umana” (decine di metri) è spesso sufficiente per mappe mesh

---

## Sensori (telemetria)

Tipi comuni:
- batteria (voltaggio)
- temperatura/umidità
- corrente/pannello solare (per nodi “solar”)

Best practice:
- invia telemetria a intervalli lunghi (minuti/ore), non ogni pochi secondi
- se la rete è pubblica, evita telemetria inutile
