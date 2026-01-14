# Android: moduli

I “moduli” sono funzionalità aggiuntive del firmware (e quindi del nodo).  
L’app ti permette di abilitarli e configurarli.

Esempi comuni (può variare in base a firmware e hardware):
- **Telemetry** (sensori, batteria, clima, ecc.)
- **MQTT** (pubblicare su broker / integrazioni)
- **Range test**
- **Store & Forward**
- integrazioni esterne (es. ATAK in certi setup)

!!! note "Dipende dalla versione"
    L’elenco dei moduli cambia nel tempo: se non trovi un modulo, non è “rotto”, può essere non disponibile sul tuo device o firmware.

---

## Strategia consigliata

1. Prima fai funzionare:
   - radio + canale + messaggi
2. Poi abilita **un modulo alla volta**
3. Verifica traffico e batteria
4. Solo dopo attivi cose “pesanti” (telemetria frequente, MQTT pubblico, range test)

---

## Modulo MQTT (nota rapida)

MQTT è potentissimo, ma:
- può pubblicare posizione/telemetria fuori dalla mesh radio
- può creare “effetto spam” se configurato male

Per dettagli: MQTT & integrazioni → Modulo MQTT.
