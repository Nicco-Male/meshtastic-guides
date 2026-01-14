# Android: mappa

La mappa serve a visualizzare:
- posizione dei nodi (se trasmessa)
- tracce (se abilitate)
- info base per ogni marker (nome, distanza, ultimi report)

---

## Prima di tutto: posizione sì/no

La posizione non è “obbligatoria” per usare Meshtastic.
Puoi:
- inviare solo messaggi testuali
- oppure inviare posizione e telemetria

Se abiliti la posizione, scegli:
- quanto spesso inviarla
- con quale precisione
- su quali canali

!!! warning "Privacy"
    Posizione + nomi nodi + MQTT pubblico = potenziale tracciamento.
    Pensa sempre a “chi può vedere questi dati”.

---

## Interpretare i simboli (concetto generale)

Senza fissarsi sull’icona esatta (può cambiare tra versioni), in genere puoi leggere:
- nome nodo
- ultimo “visto”
- batteria (se inviata)
- distanza stimata (se hai posizione anche tu)

---

## “Mappa vuota” — cause comuni

- nessuno sta inviando posizione
- GPS non fixato (se nodo senza posizione fissa)
- posizione disabilitata sul tuo canale
- stai guardando una zona sbagliata (zoom/centro mappa)

---

## Consigli per usare bene la mappa

- Per nodi fissi: valuta **posizione fissa** (se supportata) e invio più raro.
- Per nodi mobili: invio posizione a intervalli ragionevoli (non ogni 5 secondi).
- Se fai test copertura: usa “range test” e poi disattivalo.
