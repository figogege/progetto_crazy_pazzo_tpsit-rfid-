# progetto_crazy_pazzo_tpsit-rfid
Progetto TPSIT di D'Amore, Gunebakmaz e Zadro. Progetto per lo sviluppo di un sistema che sfrutta la tecnologia rfid e un database.

Il propgetto consiste nello sviluppo di un sistema per un' azienda che fornisce servizi dislocati per le citta, come la condivisione di biciclette, monopattini, scooter, powerbanks etc; per poter usufruire dei servizi è necessario pagare un abbonamento, tutti gli abbonati sono inseriti in un database.
Il progetto sfrutta anche un sistema rfid per poter accedere ai servizi. L'abbonato dovrà avvicinare una tessera NFC con l'rfid fornita dall'azienda a seguito dell'abbonamento al totem della stazione di cui vuole un servizio, la carta contiene tutti i dati dell'utente e i soldi caricati in precedenza nel saldo, si andrà cosi a verificare se l'utente ha tutti i requisiti in regola per poter accedere. Una volta avvicinata la carta, l'utente può scegliere di quale servizio usufruire direttamente dal totem della stazione, che provvede ad assegnare il dispositivo giusto.
Al momento dello sblocco, la tessera dell'utente condivide tutti i dati, che vengono memorizzati nel database assieme a tutti gli altri dati di inizio. 
All'inizio dell'utilizzo i dati presi sono: Dati utente, data, ora, luogo inizio. 
I dati passano dalla stazione al server tramite Internet con protocollo TCP per garantire l'affidabilità del tradsferimento di informazioni, che trattanto con il denaro degli utenti è necessario.
Durante l'utilizzo viene tenuta traccia degli spostamenti dell'utente mentre utilizza il dispositivo in sharing basandosi sulle stazioni a cui passa vicino, per avere sempre un riferimento geografico in caso di malfunzionamenti, guasti, incidenti, furti e altri problemi. Queeste informazioni vengono trasmesse sul database man mano che si incontra una stazione con protocollo UDP, meno affidabile ma più veloce in caso di necessità.
Alla fine dell'utilizzo l'utente si fermerà in una stazione riposizionando il dispositivo in uno slot libero e passando si nuovo la tessera sul totem per porre fine al noleggio. A questo punto vengono trasmessi sul database tramite Internet con protocollo TCP i dati di fine utilizzo: tempo di utilizzo, luogo di fine, autodiagnosi del dispositivo noleggiato.
Posto che il noleggio è stato terminato, il server procede a calcolare l'importo dovuto in base ai piani tariffari dell'azienda, quindi viene scalato l'importo dal saldo della tessera dell'utente.
Possibile sviluppi fututri:
- Inserire diversi piani di abbonamento che definiscono per quante ore un utente può accedere al servizio.
- Creare delle tabelle con le informazioni degli abbonati per poter fornire alle aziende le  statisctiche riguardo a chi utilizza maggiormente i servizi (es sesso, età, luogo in cui viene utilizzato il servizio, per quanto tempo si usa, cosa viene richiesto maggiormente).
- Rilevamenti di incidenti e infarzioni del codice della strada se si noleggiano mezzi di trasporto, tramite sensori di velocità o di urti.
SIMULAZIONE
Per simulare il progetto nel mondo reale utilizzeremo un led su Arduino, che si accende di un colore se il servizio viene sbloccato e di un altro se non viene autorizzato. Per la tecnologia NFC su Arduino verranno aggiunti moduli come PN532 o RC522.
