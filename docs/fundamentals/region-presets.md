# Regione & preset LoRa (modem preset)

Questa è la pagina più importante dopo “connessione”: **se la regione o il preset sono sbagliati, la mesh non funziona** (o funziona male).

---

## Regione: perché conta

La regione determina vincoli e parametri radio in base alla banda LoRa (frequenze, potenza massima, duty cycle, ecc.).

Per l’Italia, nella maggior parte dei casi userai:

- `EU_868`

!!! warning "Nota legale (pratica)"
    Non improvvisare frequenze/potenze: le impostazioni regionali esistono proprio per rispettare i limiti normativi.

---

## Modem preset: il compromesso “portata vs traffico”

Il modem preset (es: `LongFast`, `MediumFast`, `ShortFast`, …) definisce un set di parametri LoRa (spreading factor, bandwidth, coding rate, ecc.) che impattano:

- **Portata** (quanto “lontano” arriva)
- **Airtime** (quanto “tempo radio” consuma ogni pacchetto)
- **Affidabilità** (quanto regge il rumore / segnali deboli)
- **Capacità della rete** (quanti messaggi regge prima di saturarsi)

Regola semplice:
- preset “**Long** / **Slow**” → più portata, **molto** più airtime
- preset “**Medium/Short** / **Fast**” → meno airtime, rete più “scorrevole”

---

## Preset consigliato in Italia (pratica comune)

Nella community italiana si usa spesso:
- **Regione:** `EU_868`
- **Preset:** `MediumFast`

Motivo tipico: buona portata reale, ma senza distruggere la capacità della rete con pacchetti lunghissimi.

---

## Quando cambiare preset (casi reali)

### Scenario A — rete locale in città / paesi, tanti nodi
- Preferisci preset più “fast” (es: `MediumFast`, o più rapido) per ridurre airtime.

### Scenario B — collegamenti lunghi (monti, dorsali, pochi nodi)
- Potresti valutare preset più “long” *solo* se serve davvero.

### Scenario C — sensori/telemetria frequente
- Evita preset troppo lenti: la telemetria “mangia” airtime.

---

## Dove si imposta (in breve)

- App **Android/iOS**: sezione **Radio / LoRa** (o “Radio Configuration”)
- Web Client: simile (config radio)

Nota: la UI può variare leggermente tra app e versione firmware, ma i concetti restano gli stessi.

---

## Errori tipici da evitare

1. **Cambiare preset “a caso”** per “prendere più”  
   Spesso il vero problema è antenna/posizionamento.

2. **Usare preset molto lenti su reti dense**  
   Risultato: saturazione, “spam”, messaggi che arrivano tardi o non arrivano.

3. **Preset diversi nello stesso gruppo**  
   Se la community usa un preset comune (es: MediumFast), restare allineati aiuta tutti.
