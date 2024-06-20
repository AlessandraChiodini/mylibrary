
# MyLibrary

Questo progetto consiste nella creazione di un'applicazione web per la gestione di un archivio di libri, utilizzando un backend simulato con JSON Server e un frontend in Vanilla JavaScript. L'applicazione permette agli utenti di eseguire operazioni CRUD (Create, Read, Update, Delete) sui libri. Inoltre, sono state implementate funzionalità di filtro e ordinamento per migliorare l'esperienza utente.


# Tecnologie utilizzate

-   **HTML5**: Struttura base della pagina web.
-   **Tailwind CSS**: Libreria CSS per una stilizzazione rapida e reattiva.
-   **Vanilla JavaScript**: Logica per la gestione delle operazioni CRUD e manipolazione del DOM.
-   **JSON Server**: Simulazione di un backend per gestire le richieste HTTP.
-   **Vite**: Strumento per la creazione e gestione del progetto, che offre un ambiente di sviluppo rapido e moderno

## Struttura

-   **HTML5**
    
    -   Struttura base con elementi di form, bottoni e contenitori per i dati.
    -   Uso di classi Tailwind per una rapida stilizzazione e un layout reattivo.
    
-   **Tailwind CSS**
    
    -   Stilizzazione di elementi come bottoni, form, e griglie utilizzando classi predefinite.
    -   Personalizzazione dei colori e layout per ottenere un design pulito e moderno.
  
-   **Vanilla JavaScript**
    
    -   Gestione delle operazioni CRUD:
        -   **Create**: Aggiunta di nuovi libri tramite un form.
        -   **Read**: Visualizzazione dei libri presenti nel database.
        -   **Update**: Modifica dello stato "letto/non letto" dei libri.
        -   **Delete**: Eliminazione di libri dall'archivio.
    -   Filtri per visualizzare solo libri letti, non letti, o tutti i libri.
    -   Ordinamento dei libri per titolo o data di pubblicazione.
-   **JSON Server**
    
    -   Simulazione di un backend per gestire le richieste HTTP (GET, POST, PUT, DELETE).
    -   Memorizzazione dei dati in un file JSON.
-   **Vite**
    
    -   Configurazione e gestione del progetto tramite `npm create vite@latest`.


## Implementazione

**HTML5:**

### Spiegazione dettagliata:

1.  **Tag `<meta>`**: Specifica l'encoding del documento e la visualizzazione responsive per dispositivi.
    
2.  **Tag `<title>`**: Definisce il titolo della pagina visualizzato nella barra del browser.
    
3.  **Link a Tailwind CSS**: Collega il file CSS di Tailwind per applicare stili predefiniti alla pagina.
    
4.  **Tag `<body>`**: Il corpo principale dell'HTML, con una classe `bg-gray-100` per impostare lo sfondo grigio chiaro e `font-sans` per utilizzare un tipo di carattere senza grazie.
    
5.  **Div principale `.container`**: Contenitore principale della pagina, con margine esterno automatico (`mx-auto`) e spaziatura interna (`p-4`).
    
6.  **Intestazione `<header>`**: Parte superiore della pagina con logo o titolo centrato, utilizzando `flex` per allineare gli elementi tra loro (`justify-between` e `items-center`) e un margine inferiore (`mb-8`).
    
7.  **Form per aggiungere libri `<form>`**: Un form con uno sfondo bianco (`bg-white`), bordi arrotondati (`rounded-lg`) e ombra (`shadow-md`). Contiene campi per titolo, autore, data e un pulsante "Aggiungi Libro".
    
8.  **Lista dei libri `<div id="cont_lista">`**: Una griglia responsiva che mostra i libri in una colonna su dispositivi mobili e fino a 3 colonne su desktop, con uno spazio tra le colonne (`gap-4`).
    
9.  **Contatori dei libri `<div class="contatori">`**: Una sezione per mostrare il numero di libri letti e non letti, allineati centralmente (`flex justify-center`) con uno spazio tra i contatori (`space-x-8`).
    
10.  **Bottoni per filtrare i libri `<div class="bottoni_filtri">`**: Una serie di bottoni per filtrare i libri per stato di lettura (tutti, letti, non letti), con uno spazio tra i bottoni (`space-x-4`).
    
11.  **Bottoni per ordinare i libri `<div class="bottoni-ordina">`**: Bottoni per ordinare i libri per titolo o data di pubblicazione, con uno spazio tra i bottoni (`space-x-4`).
    
12.  **Script JavaScript**: Inclusione del file `main.js` per aggiungere la logica interattiva e il comportamento dinamico alla pagina.
    

Questo codice HTML crea un'interfaccia web per gestire una libreria di libri, utilizzando Tailwind CSS per la stilizzazione e JavaScript per la logica di interazione con l'utente e il backend simulato.

**Vanilla JavaScript:**

1.  **Selezione degli elementi HTML**: Vengono selezionati gli elementi della pagina HTML tramite i loro ID utilizzando `document.getElementById`. Questi elementi saranno utilizzati per interagire con il DOM (Document Object Model).
    
2.  **Valori dei campi di input**: I valori dei campi di input per titolo, autore, anno e genere vengono ottenuti immediatamente all'avvio dello script. Tuttavia, questo non cattura i valori degli input quando cambiano. Potresti voler spostare questa parte nel contesto di una funzione che viene chiamata quando è necessario ottenere i valori dei campi di input aggiornati.
    
3.  **`caricaLibri()`**: Questa funzione effettua una richiesta HTTP GET tramite `fetch` per ottenere i dati dei libri dal server all'indirizzo `http://localhost:3001/libri`. Una volta ricevuti i dati, svuota il contenuto dell'elemento `cont_lista` e chiama la funzione `stampaLibri` per ogni libro ottenuto.
    
4.  **`stampaLibri(libro)`**: Questa funzione crea dinamicamente un elemento `<div>` per ogni libro ricevuto. All'interno di ciascun `<div>`, crea elementi `<h2>`, `<h3>`, un checkbox e un bottone "Rimuovi" per visualizzare e gestire le informazioni del libro. Ogni elemento viene popolato con i dati appropriati dal libro e aggiunto alla lista `cont_lista`.
    
5.  **Gestione del checkbox**: Viene creato un checkbox per segnare se un libro è stato letto o no. Aggiunge un event listener per il click su questo checkbox, che invia una richiesta PATCH al server per aggiornare lo stato di lettura del libro (`libro.letto`). Quando il checkbox viene cliccato, inverte lo stato di lettura e aggiorna visivamente il checkbox di conseguenza.
    
6.  **Gestione del bottone "Rimuovi"**: Crea un bottone "Rimuovi" per ciascun libro nella lista. Aggiunge un event listener per il click su questo bottone, che invia una richiesta DELETE al server per rimuovere il libro dalla lista. Una volta confermata la rimozione dal server, l'elemento `<div>` corrispondente viene rimosso dalla lista visuale.
    
7.  **Gestione dell'evento "click" su "Mostra Tutti i Libri"**: Aggiunge un event listener al bottone "Mostra Tutti i Libri" (`tutti_libri`). Quando il bottone viene cliccato, chiama la funzione `caricaLibri` per caricare e visualizzare tutti i libri presenti sul server.
   
8.  **Gestire l'invio di un modulo per aggiungere un nuovo libro alla libreria**: quando il modulo viene inviato, l'evento submit viene intercettato e il comportamento predefinito viene prevenuto (`e.preventDefault()).
- Creare un oggetto nuovoLibro: raccoglie i dati dal modulo (titolo, autore, anno) e crea un oggetto nuovoLibro con questi valori, impostando letto a false.
- Inviare i dati al server: utilizza fetch per inviare una richiesta POST al server con l'oggetto nuovoLibro convertito in JSON.
- Gestire la risposta del server: Se la richiesta ha successo, la risposta viene convertita in JSON e la funzione stampaLibri viene chiamata per visualizzare il nuovo libro. I campi del modulo vengono resettati.
- Gestire gli errori: se c'è un errore durante la richiesta, viene stampato nella console.
In breve, questo codice aggiunge un nuovo libro alla libreria e aggiorna l'interfaccia utente con i dati del nuovo libro, gestendo eventuali errori nel processo.

9. **Le due funzioni libriLetti e libriNonLetti filtrano e mostrano rispettivamente i libri letti e non letti da un database**: fetch("http://localhost:3001/libri"): Esegue una richiesta GET al server per ottenere tutti i libri.
`.then((response) => response.json()):` Converte la risposta del server in formato JSON.
.`then((libri) => {...}):` Esegue il blocco di codice con i dati dei libri.
`cont_lista.innerHTML = "":` Svuota l'elemento HTML che contiene la lista dei libri.
`const libriLettiFiltrati = libri.filter((libro) => libro.letto):` Filtra i libri per ottenere solo quelli letti.
`libriLettiFiltrati.forEach(stampaLibri):` Visualizza i libri letti filtrati chiamando la funzione stampaLibri.
`console.log(libriLettiFiltrati.length):` Mostra il numero di libri letti nella console.
`.catch((errore) => {...}):` Gestisce eventuali errori nella richiesta e li mostra nella console. Funzione `libriNonLetti:fetch("http://localhost:3001/libri"):` Esegue una richiesta GET al server per ottenere tutti i libri.
`.then((response) => response.json()):` Converte la risposta del server in formato JSON.
`.then((libri) => {...}):` Esegue il blocco di codice con i dati dei libri.
`cont_lista.innerHTML = "":` Svuota l'elemento HTML che contiene la lista dei libri.
`const libriNonLettiFiltrati = libri.filter((libro) => !libro.letto):` Filtra i libri per ottenere solo quelli non letti.
`libriNonLettiFiltrati.forEach(stampaLibri):` Visualizza i libri non letti filtrati chiamando la funzione stampaLibri.
`console.log(libriNonLettiFiltrati.length):` Mostra il numero di libri non letti nella console.
`.catch((errore) => {...}):` Gestisce eventuali errori nella richiesta e li mostra nella console.

11. **Le funzioni, contaNonLetti e contaLetti, che contano rispettivamente i libri non letti e i libri letti e aggiornano i relativi contatori sulla pagina web**: `fetch("http://localhost:3001/libri"):` Esegue una richiesta GET al server per ottenere tutti i libri.
`.then((response) => response.json()):` Converte la risposta del server in formato JSON.
`.then((libri) => {...}):` Esegue il blocco di codice con i dati dei libri.
`const libriNonLettiCont = libri.filter((libro) => !libro.letto):` Filtra i libri per ottenere solo quelli non letti.
`contatori_non_letti.innerText = libriNonLettiCont.length:` Aggiorna il contatore dei libri non letti sulla pagina con il numero di libri non letti.
`.catch((errore) => {...}):` Gestisce eventuali errori nella richiesta e li mostra nella console.
Funzione contaLetti:
`fetch("http://localhost:3001/libri"):` Esegue una richiesta GET al server per ottenere tutti i libri.
`.then((response) => response.json()):` Converte la risposta del server in formato JSON.
`.then((libri) => {...}):` Esegue il blocco di codice con i dati dei libri.
`const libriLettiCont = libri.filter((libro) => libro.letto):` Filtra i libri per ottenere solo quelli letti.
`contatori_letti.innerText = libriLettiCont.length:` Aggiorna il contatore dei libri letti sulla pagina con il numero di libri letti.
`.catch((errore) => {...}):` Gestisce eventuali errori nella richiesta e li mostra nella console.

11. **La funzione ordinaTitolo ordina i libri in base al titolo in ordine alfabetico e li visualizza sulla pagina**

Pulizia del contenitore:

`cont_lista.innerHTML = "":` Svuota il contenitore HTML dove vengono visualizzati i libri.

    fetch("http://localhost:3001/libri"):

Esegue una richiesta GET al server per ottenere tutti i libri.

    .then((response) => response.json()):

Converte la risposta del server in formato JSON.

    .then((libri) => {...}):

Esegue il blocco di codice con i dati dei libri.

    const ordinaTi = libri.sort((a, b) => {...}):

Ordina i libri in base al titolo in ordine alfabetico.
`a.titolo.toLowerCase() < b.titolo.toLowerCase():` Confronta i titoli dei libri in ordine alfabetico ignorando maiuscole e minuscole.
Restituisce -1 se a.titolo è minore di b.titolo, 1 se è maggiore e 0 se sono uguali.

    ordinaTi.forEach(stampaLibri):

Visualizza ciascun libro ordinato sulla pagina chiamando la funzione stampaLibri per ogni libro.

    .catch((errore) => {...}):

Gestisce eventuali errori nella richiesta e li mostra nella console.

12. **Le funzioni che al caricamento della pagina aggiungono degli event listener per vari pulsanti della pagina per eseguire diverse azioni**
Funzioni chiamate al lancio della pagina:

contaNonLetti(): Conta i libri non letti e aggiorna il contatore sulla pagina.
contaLetti(): Conta i libri letti e aggiorna il contatore sulla pagina.
Event listener per i pulsanti:

    ordina_titolo.addEventListener("click", ordinaTitolo):

Ordina i libri per titolo quando si clicca il pulsante per l'ordinamento per titolo.

    ordina_data.addEventListener("click", ordinaAnno):

Ordina i libri per anno quando si clicca il pulsante per l'ordinamento per anno.

    tutti_libri.addEventListener("click", caricaLibri):

Mostra tutti i libri quando si clicca il pulsante per mostrare tutti i libri.

    libri_letti.addEventListener("click", libriLetti):

Mostra solo i libri letti quando si clicca il pulsante per mostrare i libri letti.

    libri_da_leggere.addEventListener("click", libriNonLetti):

Mostra solo i libri non letti quando si clicca il pulsante per mostrare i libri da leggere.

**JSON Server:**

-   Simulazione di un backend:
    -   Configurazione di `db.json` per memorizzare i dati dei libri.
    -   Utilizzo di due terminali: uno per `npm run dev` (Vite) e uno per `npm run json-server` (JSON Server).

### Conclusione

Il JavaScript per questo progetto gestisce tutte le interazioni dell'utente con il sistema, dal caricamento iniziale dei libri, all'aggiunta di nuovi, alla modifica e eliminazione, fino al filtraggio e ordinamento. L'integrazione con JSON Server permette di simulare un backend reale, offrendo un'esperienza di sviluppo completa e realistica.


## Ruoli

- Alessandra Chiodini - UX UI Designer (GitHub)
- Mariarita Oliva - Senior Web Developer (GitHub)
- Marina Manole - Database Administrator (GitHub)
- Monia Cirimele - Junior Web Developer (GitHub)
- Matteo Sabatini - IT Support Specialist (GitHub)

Questi ruoli sono quelli all'interno del gruppo di lavoro per il progetto MyLibrary... In realtà siamo tutti Front End Developer in erba e abbiamo cercato di dare il meglio in tutte le fasi del progetto mantenendo comunque 

## Commenti finali

Questo progetto dimostra come utilizzare tecnologie moderne e leggere per creare un'applicazione web funzionale e user-friendly. L'integrazione di JSON Server consente di simulare un backend reale, mentre l'uso di Tailwind CSS garantisce un design reattivo e pulito. Il risultato è un'applicazione completa che permette una gestione efficace di un archivio di libri, con funzionalità avanzate di filtro e ordinamento per migliorare l'esperienza dell'utente.
