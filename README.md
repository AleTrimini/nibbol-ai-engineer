# AI Engineer Take-Home Challenge: RAG sugli Avengers

## Scenario: Operazione A.V.E.N.G.E.R.

Durante l'ultimo attacco alla Avengers Tower, un impulso elettromagnetico ha danneggiato il sistema che permette agli eroi di consultare l'archivio delle loro missioni. I documenti sono ancora integri, ma sono sparsi in decine di PDF e trovare rapidamente l'informazione giusta è diventato quasi impossibile.

Nick Fury ha quindi autorizzato l'**Operazione A.V.E.N.G.E.R.** — *Automated Vector Engine for Narrative Grounding, Evidence and Retrieval*.

Il tuo compito è costruire il nuovo assistente dell'archivio. Il sistema dovrà aiutare gli Avengers a interrogare i documenti in linguaggio naturale, collegare informazioni provenienti da missioni diverse e rispondere mostrando sempre le prove utilizzate.

La precisione è fondamentale: una risposta inventata sui punti deboli di un alleato potrebbe compromettere una missione. Se l'archivio non contiene la risposta, l'assistente deve ammetterlo chiaramente. Fury preferisce un onesto «informazione non disponibile» a un'allucinazione pronunciata con sicurezza.

Hai sette giorni prima che il sistema venga presentato agli Avengers. Tony Stark non ha imposto uno stack tecnologico — sorprendentemente — quindi puoi scegliere gli strumenti con cui lavori meglio. Quello che conta è che la soluzione funzioni, sia verificabile e possa essere spiegata alla squadra tecnica.

## Obiettivo

Progettare e implementare un sistema **Retrieval-Augmented Generation (RAG)** capace di rispondere a domande in linguaggio naturale utilizzando esclusivamente i documenti PDF forniti.

Il sistema dovrà recuperare le informazioni rilevanti, produrre risposte comprensibili e indicare chiaramente le fonti utilizzate. Il candidato può scegliere liberamente lo stack con cui si sente più a proprio agio: linguaggi, framework, modelli, database vettoriali e servizi esterni non sono imposti.

## Tempo a disposizione

La consegna è prevista entro **7 giorni di calendario** dalla ricezione del test.

Non è necessario lavorare per sette giorni pieni. La valutazione privilegia la qualità delle decisioni tecniche, la verificabilità del sistema e la chiarezza della consegna rispetto alla quantità di funzionalità.

## Dataset

Il corpus si trova della cartella docs e contiene:

- le trame dettagliate dei quattro film Avengers;
- schede dedicate a eroi, antieroi e villain;
- indici e documenti di supporto.

I PDF costituiscono la **sola fonte di verità** del sistema. Le risposte devono essere prodotte esclusivamente a partire dalle informazioni presenti nella documentazione fornita. Il sistema non deve completare le risposte utilizzando il web o la conoscenza generale del modello.

## Requisiti funzionali obbligatori

### 1. Ingestion e indicizzazione

Il sistema deve:

- leggere tutti i PDF presenti nelle due cartelle;
- estrarre il testo mantenendo almeno il riferimento al file sorgente e alla pagina;
- indicizzare il corpus con una strategia motivata dal candidato;

L'ingestion deve essere ripetibile tramite un comando o uno script documentato.

### 2. Interfaccia chat e domande in linguaggio naturale

Il progetto deve includere una **piccola interfaccia con una chat** attraverso la quale l'utente possa formulare domande libere e ricevere le risposte generate dal RAG.

L'interfaccia può essere realizzata con qualsiasi tecnologia e non è necessario dedicare particolare attenzione al design grafico. Deve però essere semplice da avviare e permettere ai valutatori di provare agevolmente nuove domande, per esempio:

- «Perché Tony Stark decide di creare Ultron?»
- «Quali sono i punti deboli di Hulk?»
- «Confronta i poteri di Thor e Captain Marvel.»
- «In quali film compare Wanda e come cambia il suo ruolo?»
- «Come fanno gli Avengers a recuperare le Gemme in Endgame?»
- «Chi sono i membri dell'Ordine Nero presenti nei documenti?»

Una CLI, un notebook o un'API possono essere presenti come strumenti aggiuntivi, ma non sostituiscono l'interfaccia chat richiesta.

### 3. Risposte fondate sulle fonti

Ogni risposta deve:

- essere basata esclusivamente sul contenuto recuperato dai PDF;
- distinguere chiaramente fatti presenti nel corpus da eventuali deduzioni;
- evitare di inventare informazioni non supportate;
- dichiarare quando il corpus non contiene elementi sufficienti per rispondere.


### 4. Recupero multi-documento

Il sistema deve gestire domande che richiedono informazioni provenienti da più file, come confronti tra personaggi, evoluzioni attraverso film differenti o riepiloghi trasversali.

### 5. Riproducibilità

Un valutatore deve poter avviare il progetto seguendo il `README` senza dover ricostruire passaggi mancanti. Devono essere documentati:

- prerequisiti;
- installazione;
- configurazione e variabili d'ambiente;
- comando di ingestion;
- comando di avvio;
- comando per eseguire test o valutazioni;
- servizi esterni

Non inserire chiavi API o credenziali nel repository. Non è necessario usare servizi a pagamento, il progetto può essere tranquillamente svolto con servizi gratuiti (o nei limiti gratuiti).

## Requisiti tecnici e libertà di scelta

Il candidato è libero di utilizzare lo stack, i servizi e gli strumenti con cui si sente più a proprio agio. Non esiste una combinazione tecnologica preferita e la scelta di tecnologie semplici non costituisce uno svantaggio.

È consentito utilizzare strumenti di AI durante qualsiasi fase dello sviluppo, inclusi assistenti di programmazione, generatori di codice e modelli linguistici. Ci interessa che il candidato:

- comprenda il codice consegnato;
- sappia commentarlo e spiegarne il funzionamento;
- sia in grado di motivare le principali scelte tecniche;
- riconosca limiti e compromessi della soluzione;
- sappia intervenire sul progetto durante un eventuale colloquio tecnico.


È possibile utilizzare servizi commerciali, modelli locali, API, librerie open source o una combinazione di questi strumenti. Le scelte devono essere motivate nel README.

## Valutazione richiesta al candidato

Preparare un piccolo set di valutazione contenente almeno:

- **5 domande fattuali** su un singolo documento;
- **3 domande multi-documento**;
- **2 domande senza risposta nel corpus**;
- **2 domande ambigue o formulate in modo impreciso**.

Per ogni esempio indicare:

- domanda;
- comportamento o risposta attesa;
- fonti attese, quando applicabili;
- risultato prodotto dal sistema;
- breve commento sull'esito.

La valutazione può essere automatica, manuale o ibrida. Non è richiesto costruire un framework di evaluation completo, ma ci aspettiamo un metodo ripetibile e ragionato.

## Deliverable

La consegna deve contenere:

- codice sorgente;
- `README.md` con istruzioni complete;
- file di dipendenze e configurazione di esempio;
- pipeline di ingestion ripetibile;
- piccola interfaccia chat per interrogare il sistema;
- test o script di valutazione;
- risultati della valutazione;
- breve sezione sulle decisioni architetturali;
- breve sezione su limiti, rischi e possibili miglioramenti.

## Modalità di consegna

La modalità preferita è un **repository GitHub**. In questo caso il candidato deve:

1. concedere l'accesso al repository a `devalessiat@gmail.com` come contributor o collaboratore;
2. verificare che il repository sia accessibile e contenga tutto il necessario per eseguire il progetto;
3. inviare una email di conferma della consegna a entrambi gli indirizzi:
   - `alessia.trimini@nibbol.com`;
   - `antonio.dabundo@nibbol.com`.

In alternativa, il progetto può essere inviato tramite email come archivio compresso o attraverso un collegamento per il download. Anche in questo caso, la comunicazione di consegna deve essere inviata a **entrambi** gli indirizzi indicati sopra.

L'email di consegna deve contenere almeno:

- nome e cognome del candidato;
- collegamento al repository o al pacchetto del progetto;
- eventuali istruzioni aggiuntive necessarie per l'avvio;

