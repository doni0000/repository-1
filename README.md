# repository-Amazon Go e Bluetooth LE
<h1 color=red>Amazon Go</h1>
Amazon Go è una catena di negozi fondata da Amazon che elimina la necessità di casse e commessi<br>
Funziona grazie all'utilizzo di diverse tecnologie tra cui: sensori IoT, IA e Bluetooth LE.

<h1>Sensori IoT</h1>
<h3>Cosa sono?</h3>
I sensori IoT (Internet of Things) sono dispositivi che rilevano dati dall'ambiente (come movimento, luce, umidità ecc.) e li trasmettono a una rete per l'elaborazione e l'analisi. Sono fondamentali per  creare sistemi automatizzati e intelligenti in vari settori, come smart home, sanità, agricoltura e industria.
<br>
Esempio: Un sensore di peso permette di rilevare quando un oggetto viene rimosso o aggiunto ad uno scaffale.

<h3>Come funzionano</h3>
Funzionamento di un sensore IoT:

  - Acquisizione dati → Il sensore raccoglie informazioni dall’ambiente.
  - Elaborazione locale → Un microcontrollore può elaborare i dati direttamente.
  - Trasmissione dati → I dati vengono inviati a un gateway o un cloud tramite protocolli di comunicazione (Wi-Fi, Bluetooth ecc.).
  - Analisi e azione → I dati vengono analizzati su server o cloud, e un sistema può prendere decisioni automatiche.

Esempio:<br>
Un sensore di peso rileva se un oggetto è stato tolto o aggiunto ad uno scaffale e lo comunica al sistema centrale.

Non esistono solo sensori di peso ma anche:
  -  Sensori di temperatura → Rilevano variazioni di temperatura.
  -  Sensori di umidità → Misurano il livello di umidità.
  -  Sensori di movimento  → Rilevano il movimento (es.allarmi).
  -  Sensori di prossimità → Utilizzati in veicoli per il parcheggio assistito e automazione industriale.
  -  Sensori di gas → Monitorano la qualità dell’aria e rilevano gas pericolosi .
  -  Sensori di luce → Regolano automaticamente la luminosità negli ambienti.
  -  Sensori di vibrazione → Utilizzati nel monitoraggio strutturale di edifici e macchinari.

<h3>Vantaggi e Svantaggi</h3>
Sebbene i sensori IoT offrano numerosi vantaggi come l'automazione, la riduzione dei costi e migliorare la vita quotidiana, hanno anche molti svantaggi.<br>
Ad esempio essendo dipendenti dalla rete wi-fi in caso di un problema nella connessione essi non possono essere utilizzati, oppure ci potrebbero essere dei problemi di privacy in caso essi non siano protetti adeguatamente.

<h1 color=red>Bluethoot LE</h1>
Il Bluetooth Low Energy è una tecnologia wireless progettata e commercializzata dal Bluetooth SIG per nuove applicazioni nel settore dall'assistenza sanitari, per le industrie automobilistiche e industrie dell'intrattenimento domestico.
Rispetto al Bluetooth classico, il Bluetooth Low Energy ha lo scopo di fornire un consumo energetico e un costo notevolmente ridotto, mantenendo un intervallo di comunicazione simile.
Bluetooth Low Energy utilizza le stesse frequenze radio a 2.4 GHz come il Bluetooth classico.

<h1>Autenticazione BLE</h1>
L'autenticazione è un processo che verifica l'identità di un dispositivo prima di stabilire una connessione sicura. Questo avviene tramite il protocollo UART e viene utilizzato principalmente nelle comunicazioni con un'APP.

Il protocollo **UART (Universal Asynchronous Receiver-Transmitter)** è un metodo di comunicazione seriale asincrona utilizzato per lo scambio di dati tra dispositivi elettronici. È ampiamente usato nei sistemi embedded, nei moduli Bluetooth e in molte applicazioni di comunicazione tra microcontrollori e periferiche.

<h4>Procedura di autenticazione:</h4> <ol>
   <li> Abilitazione della funzione di autenticazione: Sul dispositivo slave deve essere abilitata la funzione di autenticazione e viene impostata una password predefinita, passaggio cruciale perché determina la chiave condivisa che verrà usata per le connessioni successive.  </li>
   <li> Scambio della password: quando un dispositivo master tenta di connettersi, deve inviare la password tramite un canale UART specifico. </li>
   <li> Verifica della password: Lo slave, al ricevere il dato, confronta la password trasmessa con quella memorizzata internamente. Se la password corrisponde, la connessione viene accettata e mantenuta, se invece la verifica fallisce, la connessione viene immediatamente interrotta o disabilitata, impedendo l’accesso non autorizzato.</li>
    </ol>
<h4>Caratteristiche principali dell'autenticazione:</h4>
    • È richiesta per ogni connessione, garantendo un controllo continuo. <br>
    • Effettiva solo per APP o dispositivi che supportano la gestione della password tramite UART. <br>
    • Previene accessi non autorizzati, ma non memorizza automaticamente i dispositivi fidati. <br>
<h3>Abbinamento BLE (Pairing)</h3>
L’accoppiamento, invece, si basa sul protocollo Bluetooth sottostante e serve a creare una relazione “fidata” tra i dispositivi, salvando le informazioni di pairing in una lista interna. Ciò consente al master  che può essere un modulo BLE o un telefono cellulare di riconnettersi successivamente senza dover ripetere la procedura di autenticazione completa tramite password. 
<h4>Per le prime associazioni:</h4>
Durante il primo collegamento, oltre al passaggio di autenticazione, viene eseguita la procedura di pairing che registra il dispositivo master nell’elenco degli accoppiamenti dello slave. 
<h4>Per le associazioni successive: </h4>                                                                                                              Dopo l’associazione iniziale, il modulo BLE riconosce il dispositivo accoppiato e permette la connessione diretta, senza dover richiedere nuovamente la password. Questa funzionalità facilita le comunicazioni ricorrenti e semplifica il processo di riconnessione. 
<h4>Caratteristiche principali dell'abbinamento:</h4>
    • Supportato nativamente dal protocollo Bluetooth senza necessità di gestione manuale della password dopo il primo pairing. <br>
    • Se l’indirizzo MAC del dispositivo viene eliminato dall’elenco di pairing, sarà necessaria una nuova autenticazione per ristabilire la connessione. <br>
    • Permette connessioni rapide e senza intervento dell'utente una volta effettuato il primo pairing. <br>

<h3>Differenze chiave tra autenticazione e abbinamento</h3>
<strong>Autenticazione</strong><br>
    • l’obbiettivo è controllare  gli accessi ogni volta <br>
    • verifica la password tramite UART<br>
    • password richiesta ad ogni connessione<br>
    • non memorizza i dispositivi e di conseguenza deve verificare ogni volta il dispositivo<br>
    • gestisce il bluetooth a livello applicativo tramite UART<br><br>
<strong>Abbinamento</strong><br>
    • l’obbiettivo è avere una connessione rapida e automatizzata<br>
    • verifica l’autenticazione tramite chiavi crittografiche<br>
    • richiede l’autenticazione solo la prima volta, per le successive  la connessione sarà diretta<br>
    • memorizza i dispositivi in un elenco di pairing<br>
    • gestisce il bluetooth a livello del protocollo BLE<br><br>

Entrambi i meccanismi possono coesistere: l'autenticazione può essere usata per un ulteriore livello di sicurezza, mentre l'abbinamento facilita le connessioni successive senza dover reinserire credenziali ogni volta.
Questi due meccanismi lavorano insieme per bilanciare sicurezza e comodità: mentre l’autenticazione garantisce la verifica di identità per ogni sessione, l’accoppiamento assicura che una volta stabilita una connessione sicura, le operazioni successive siano semplificate senza compromettere la protezione del sistema. 

<h3>Localizzazione tramite  BLE</h3>
La localizzazione basata su Bluetooth Low Energy (BLE) è una tecnologia ampiamente utilizzata per il tracciamento in tempo reale di oggetti e persone in ambienti indoor.<br>
La tecnologia si basa su un sistema di tag BLE applicati agli oggetti da monitorare e di antenne riceventi installate nell’ambiente. Il segnale BLE trasmesso dai tag viene rilevato dalle antenne, che inviano i dati a un software di localizzazione per determinare la posizione degli asset.
<h3>Componenti principali del sistema</h3>
    • <strong>Tag BLE:</strong> piccoli dispositivi che trasmettono segnali BLE a intervalli regolari. Possono avere diverse forme a seconda dell’uso specifico.<br>
    • <strong>Antenne riceventi: </strong>installate su pareti o soffitti per rilevare i segnali BLE inviati dai tag. Il numero e la disposizione delle antenne influiscono sulla precisione del sistema.<br>
    • <strong>Software di localizzazione:</strong> elabora i dati ricevuti dalle antenne per calcolare la posizione degli asset e integrarli con altri sistemi aziendali.<br>
<h3>Tecniche di localizzazione BLE</h3>
Esistono diverse tecniche per determinare la posizione dei tag BLE, con livelli di precisione variabili. Le principali sono:<br>
<h4><strong>1. Received Signal Strength Indicator (RSSI)</strong></h4>
Con questa tecnica si sfrutta la potenza ricevuta dalle antenne del segnale BLE per determinare la distanza tra il tag, che ha emesso il segnale, e le antenne stesse. A partire dalla posizione delle antenne, è possibile calcolare la posizione approssimativa del dispositivo utilizzando algoritmi di trilaterazione. Maggiore è la densità delle antenne, migliore è la localizzazione che difficilmente può superare i 3 metri. servono almeno 3 antenne per poter stimare la posizione del tag. In assenza di 3 antenne, la posizione del tag viene approssimata a quella dell’antenna stessa che ha ricevuto il segnale con la potenza maggiore.
<h4><strong>2. Angle of Arrival (AoA)</strong></h4>
Con questa tecnica si sfrutta l’angolo di arrivo del segnale trasmesso dai tag sulle antenne riceventi. Riuscendo a rilevare sulle 3 dimensioni l’angolo di provenienza del segnale, questa tecnica permette di identificare con una elevata precisione la posizione del dispositivo che lo ha emesso. Tuttavia le antenne richiedono un hardware particolare (oltre che il necessario firmware), ovvero un array di antenne che permetta di rilevare non solo la potenza, ma anche la direzione di arrivo del segnale, 1 sola antenna è sufficiente per localizzare un tag e maggiore è l’altezza di installazione e maggiore è la copertura Sfruttando l’angolo di arrivo del segnale, questa tecnica offre una maggiore robustezza alle riflessioni che si traduce in una localizzazione molto più precisa che può raggiungere il mezzo metro in ambienti anche complessi di utilizzo.

<h1>Presentazione</h1>
Presentazione realizzata da Alessandro Donida Labati, Pandini Filippo, Bergomi Fabio e Linardi Cristian	<br>
La nostra presentazione approfondisce il funzionamento dei negozi Amazon Go. 

Descrive:
  - come funziona
  - le tecnologie che sono utilizzate
  - il tipo di Bluetooth utilizzato e a cosa serve



<h3>Siti utilizzati</h3>

https://www.ibm.com/it-it/topics/computer-vision <br>
https://tech.everyeye.it/articoli/speciale-amazon-go-spesa-del-futuro-tra-ia-machine-learning-31772.html  <br>
https://www.thismarketerslife.it/marketing/just-walk-out-tecnhology-gli-scaffali-intelligenti-di-amazon-go/   <br>
https://chatgpt.com/c/67d52d54-1da4-800f-b4b6-0077861756d6  <br>
