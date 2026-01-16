# Come apparire sulla mappa LoRaItalia

La mappa dinamica di LoRaItalia (<https://map.loraitalia.it>) mostra i nodi connessi alla rete mesh italiana. È uno strumento utile per visualizzare la topologia della rete e la posizione dei nodi, ma **non elenca i nodi isolati**: se un dispositivo non ha contatti radio con almeno un altro nodo della rete, per la mappa semplicemente “non esiste”.

Questa guida spiega come configurare correttamente il proprio nodo Meshtastic per farlo apparire sulla mappa, quali sono i prerequisiti di connettività e come procedere se si opera in un’area completamente isolata.

---

## 1. Prerequisiti e configurazione di base

Perché la mappa possa visualizzare il nodo, è necessario che esso invii periodicamente pacchetti **nodeInfo** e **position** alla rete. Tali pacchetti contengono **LongName**, **ShortName** e coordinate GPS (o statiche) e devono raggiungere almeno un nodo collegato a Internet che inoltri i dati al server MQTT di LoRaItalia. Prima di accendere il dispositivo assicurarsi di:

### Impostare i nomi correttamente

Il **LongName** viene usato nell’elenco dei nodi e sulla mappa. Può contenere lettere, numeri e simboli. Lo **ShortName** (massimo 4 caratteri) identifica il nodo in chat. È consigliabile impostarli con la CLI:

```bash
# imposta il LongName
meshtastic --set-owner "IL_TUO_NOME_LUNGO"

# imposta lo ShortName (4 caratteri)
meshtastic --set-owner-short "A1B2"
```

### Selezionare la regione corretta

In Italia bisogna usare la regione **EU_868** e il preset **MediumFast** per rimanere nei limiti di legge e mantenere efficiente la mesh. Con la CLI si imposta così:

```bash
# regione EU_868 (codice 3)
meshtastic --set lora.region 3

# preset MediumFast
meshtastic --set lora.modem_preset MEDIUM_FAST
```

### Configurare il ruolo

Un nodo che vuole comparire in mappa dovrebbe essere di tipo **CLIENT** (non ROUTER o REPEATER), con **OK to MQTT** attivo e **Ignore MQTT** disattivato. In CLI:

```bash
meshtastic --set device.role CLIENT
meshtastic --set device.ok_to_mqtt true
meshtastic --set device.ignore_mqtt false
```

### Impostare le coordinate

Se il dispositivo dispone di GPS integrato, le coordinate vengono acquisite automaticamente. In caso contrario è possibile impostare una posizione statica (latitudine e longitudine) tramite l’app Meshtastic oppure con il comando CLI. **Senza coordinate non sarà possibile visualizzare il nodo sulla mappa.**

### Tempi di broadcasting

I pacchetti **nodeInfo** e **position** non devono essere inviati troppo spesso per non saturare la rete. La wiki consiglia **3.600 s** per nodi mobili e **10.800 s** per nodi fissi per il **nodeInfo**, e **3.600 s** (mobili) / **43.200 s** (fissi) per il **position**. Esempio di configurazione CLI per un nodo fisso:

```bash
meshtastic --set device.node_info_broadcast_secs 10800
meshtastic --set position.position_broadcast_secs 43200
```

### Neighbor Info (opzionale)

Attivando il modulo **Neighbor Info** sui nodi fissi, la mappa può mostrare la topologia dei link radio. È consigliabile impostare un intervallo di almeno **10.800 s**.

---

## Configurazione tramite app mobile e Web

Se non avete dimestichezza con la CLI, potete configurare la maggior parte dei parametri direttamente dall’app Meshtastic (Android o iOS/macOS) o attraverso il Web Client integrato nel nodo. Le opzioni sono suddivise in sezioni analoghe a quelle descritte in precedenza: **User**, **LoRa**, **Device** e **Position**. Di seguito sono riportate le operazioni fondamentali per far apparire il nodo sulla mappa e dove trovarle nell’interfaccia grafica.

### Impostare LongName e ShortName

Aprite l’app Meshtastic sul telefono, collegate il nodo via Bluetooth o Wi‑Fi e andate in **Settings > User** (Android) oppure **Settings > Device Configuration > User** (iOS/macOS). In questa sezione potete personalizzare **Long Name** e **Short Name**. Nel web client trovate le stesse opzioni nella scheda **User**.

### Selezionare regione e preset LoRa

Dall’app andate in **Settings > LoRa** (Android) o **Settings > Radio Configuration > LoRa** (iOS). Qui potete scegliere la **Region** (impostate **EU_868** per l’Italia) e il **Modem Preset** (consigliato **MediumFast**) così come faresti da CLI. Nel web client le stesse impostazioni sono accessibili nella sezione **LoRa**.

### Configurare il ruolo e l’intervallo Node Info

Nel menu **Settings > Device** (Android) o **Settings > Device Configuration > Device** (iOS) potete impostare il **Role** su **Client** e modificare il valore **Node Info Broadcast Seconds**. Impostate **Client** come ruolo e specificate un intervallo di trasmissione adeguato (**10.800 s** per nodi fissi o **3.600 s** per nodi mobili). Sempre in questa sezione trovate l’opzione **OK to MQTT** (lasciarla abilitata) e **Ignore MQTT** (da disabilitare).

### Posizione, posizione fissa e intervallo di trasmissione

Aprite **Settings > Position** sull’app Android o **Settings > Device Configuration > Position** su iOS/macOS. Qui potete scegliere se usare il GPS del dispositivo o impostare una posizione fissa (**Fixed Position**) inserendo manualmente latitudine, longitudine e altitudine. Nella stessa sezione potete configurare l’intervallo di trasmissione della posizione (**position_broadcast_secs**): per un nodo fisso è consigliato un valore elevato (fino a **43.200 s**) mentre per nodi mobili **3.600 s**. Se non avete GPS integrato, l’app userà il GPS del telefono per rilevare la posizione iniziale e potete abilitare **Fixed Position** per mantenere coordinate statiche.

### Accedere al Web client

Ogni nodo Meshtastic dispone di un’interfaccia web accessibile tramite il browser collegandosi all’indirizzo IP del nodo (solitamente <http://192.168.4.1> quando è in modalità access point). Una volta aperto il Web client, troverete le stesse sezioni **User**, **LoRa**, **Device** e **Position**, e potete configurare LongName/ShortName, regione, ruolo, tempi di broadcast e posizione come descritto sopra. L’interfaccia web è comoda se non si dispone di uno smartphone o se si desidera configurare rapidamente più nodi.

In sintesi, l’app mobile e il web client forniscono un modo intuitivo per impostare tutti i parametri necessari senza usare la CLI. Assicuratevi di salvare le modifiche dopo averle applicate e, come per la CLI, attendete uno o due cicli di invio prima di vedere il nodo sulla mappa.

---

## 2. Connettività alla rete LoRaItalia

La condizione più importante per apparire in mappa è raggiungere **almeno un nodo** della rete LoRaItalia. Se il vostro nodo riceve e trasmette solo con dispositivi locali ma non è collegato via radio a un nodo che inoltra i pacchetti al server MQTT, la mappa non potrà rilevarvi. Alcuni suggerimenti:

- **Verificare la presenza di nodi vicini** – Attraverso l’app Meshtastic potete cercare nella lista dei nodi i contatti ricevuti. Se non vedete nodi connessi, provate a cambiare posizione (per esempio spostando l’antenna in esterno). La mappa sul sito mostra solo i nodi connessi.
- **Effettuare un traceroute** – Dal menu dell’app potete inviare un traceroute verso un nodo noto (ad esempio c004 o altri elencati nel gruppo Telegram). Se il traceroute supera uno o più hop, significa che siete in contatto con la rete.
- **Rivolgersi a un nodo connesso a Internet** – Se nella vostra zona ci sono nodi di LoRaItalia connessi a Internet, i vostri pacchetti arriveranno automaticamente al server MQTT e comparirete in mappa. In caso contrario, potete configurare uno dei vostri nodi come **router_client** con accesso Wi‑Fi e impostare i parametri MQTT forniti da LoRaItalia per inoltrare i pacchetti.

---

## 3. Tempi di aggiornamento

Anche con la configurazione corretta, il nodo potrebbe impiegare un po’ di tempo prima di apparire sulla mappa. La frequenza di invio dei pacchetti (es. 3.600 s o 10.800 s) e la propagazione attraverso la mesh fanno sì che possano servire alcune decine di minuti. Mantenete il nodo alimentato e lasciate che trasmetta la posizione più volte.

---

## 4. Come fare se il nodo rimane isolato

La FAQ ufficiale sottolinea che la mappa è gestita in modo automatico e visualizza solo i nodi connessi. Se siete in una zona priva di copertura e non riuscite a raggiungere alcun nodo LoRaItalia, avete due possibilità:

1. **Trasferire temporaneamente i pacchetti via Internet** – Potete configurare il nodo come client MQTT collegandolo al Wi‑Fi, impostare le credenziali del broker LoRaItalia e inoltrare i pacchetti. In questo modo il nodo comparirà in mappa anche se non ci sono altri nodi radio nei dintorni.
2. **Inserimento manuale** – LoRaItalia offre un foglio di calcolo dove è possibile registrare manualmente il proprio nodo con nome, coordinate, canale e altre informazioni. Il link è disponibile nella sezione **F.A.Q.** del sito. Dopo la compilazione, gli amministratori aggiungeranno il nodo a mano.

---

## 5. FAQ (domande comuni)

### Il mio nodo è acceso ma non compare in mappa. Cosa sto sbagliando?

- Verifica di avere contatto radio con la rete LoRaItalia. Se non ricevi alcun nodo, la mappa non potrà rilevare il tuo dispositivo.
- Controlla di aver impostato regione, preset e hopLimit corretti (**EU_868**, **MediumFast**, **hopLimit = 3**).
- Assicurati di aver impostato un LongName e di trasmettere i pacchetti nodeInfo/position a intervalli adeguati.
- Se non hai un GPS, imposta una posizione statica altrimenti il nodo verrà ricevuto ma senza coordinate.
- Attendi almeno 1–2 cicli di trasmissione (fino a un paio d’ore) prima di considerare la comparsa definitiva.

### Come imposto una posizione statica?

Nell’app Meshtastic apri le impostazioni del nodo, disattiva GPS automatico e inserisci manualmente latitudine, longitudine e altitudine. In alternativa puoi usare la CLI:

```bash
meshtastic --set position.latitude  43.847
meshtastic --set position.longitude 10.502
meshtastic --set position.altitude  35
```

Ricordati di adeguare i valori alla tua posizione reale.

### Il mio nodo si vede nella lista dell’app ma non sul sito; perché?

La lista nell’app mostra i nodi che ricevi via radio, mentre il sito mostra solo quelli che raggiungono il server MQTT di LoRaItalia. Se nella tua zona non c’è un nodo connesso a Internet, potresti vedere altri nodi localmente ma nessuno dei vostri pacchetti viene inoltrato al server.

### Mi serve accesso a MQTT per comparire in mappa?

No. I dati del tuo nodo viaggiano nella rete mesh e **compari in mappa quando almeno un nodo collegato a MQTT inoltra i pacchetti**. Ricordati di:

- abilitare la condivisione della posizione sul canale principale (anche approssimativa va bene);
- disattivare **Smart Position** sui nodi fissi, altrimenti la posizione viene trasmessa solo una volta;
- mantenere **OK to MQTT** attivo sul nodo.

### Devo abilitare Neighbor Info?

Non è obbligatorio. Il modulo **Neighbor Info** serve a visualizzare la topologia dei link sulla mappa e a valutare la qualità delle connessioni. Può essere utile sui nodi fissi ma va configurato con un intervallo di almeno **10.800 s** per non appesantire la rete.

### Quanto tempo devo tenere acceso il nodo per apparire?

Dipende dagli intervalli di trasmissione configurati e dalla capacità del nodo di raggiungere la rete. Con gli intervalli suggeriti (3.600–10.800 s) potrebbe essere necessario da qualche decina di minuti a un paio d’ore. Lascia il nodo acceso e assicurati che sia in un luogo con buona copertura radio.

Se dopo aver seguito questi passi il nodo non appare ancora, chiedi supporto sul gruppo Telegram di Meshtastic Italia oppure consulta la sezione **F.A.Q.** del sito LoRaItalia per ulteriori dettagli.
