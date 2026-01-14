# Hop limit & routing

“Hop” = un salto da un nodo al successivo.

Quando mandi un messaggio, può arrivare al destinatario direttamente (0-1 hop) oppure attraversare più nodi che lo inoltrano (2-3 hop…).

---

## Hop limit (TTL): cos’è

L’**hop limit** (a volte mostrato come “max hops”) è il limite massimo di inoltri consentiti per un pacchetto.

- Se hop limit = 3, il pacchetto può attraversare al massimo 3 “rilanci”.
- Aumentarlo **aumenta** la portata potenziale, ma aumenta anche **il traffico**.

!!! warning "Più hop ≠ più magia"
    Su una mesh LoRa, “più hop” spesso significa “più congestione”.

---

## Perché 3 è spesso il numero “sano”

Nelle reti reali:
- 1–2 hop coprono già moltissimo se i nodi sono posizionati bene.
- oltre 3 hop, il costo in airtime cresce e il vantaggio decresce.

---

## Rebroadcast (inoltro) in parole semplici

I nodi Meshtastic, a seconda della configurazione, possono:
- inoltrare pacchetti che ricevono (rebroadcast)
- limitare quanto inoltrano (per risparmiare batteria o ridurre traffico)
- cambiare comportamento in base al ruolo (client/router/repeater ecc.)

Se un nodo inoltra “troppo”, può diventare una sorgente di congestione.
Se un nodo inoltra “troppo poco”, può spezzare collegamenti.

---

## Best practice per reti “pulite”

- Mantieni hop limit sensato (spesso 3).
- Se vuoi coprire più area, investi in:
  - antenne migliori
  - altezza e line-of-sight
  - un paio di nodi “ben piazzati” invece di “tutti con hop 7”
- Evita di trasformare nodi a batteria in router involontari.

---

## Troubleshooting rapido

### “I messaggi arrivano in ritardo”
Possibili cause:
- rete congestionata (troppo traffico)
- hop limit alto (più rebroadcast)
- preset troppo lento per la densità della rete

### “Non arrivo oltre un certo punto”
Prima verifica:
- esiste davvero un percorso di nodi (line-of-sight / copertura)?
- i nodi intermedi inoltrano?
Poi valuta:
- aggiungere un nodo intermedio in posizione migliore
