# 🎓 Rubrica Pro MERN — Programma del corso

**Tecnologie e strumenti:** HTML, CSS, JavaScript, React, Vite, React Router, Node.js, npm, Express, MongoDB, Mongoose, MongoDB Atlas, Railway, Netlify, Git, GitHub ed ESLint.

## Presentazione

Questo corso accompagna dalla creazione di una semplice applicazione React alla realizzazione e pubblicazione di una rubrica telefonica MERN. La rubrica permette di visualizzare, aggiungere, modificare ed eliminare contatti salvati in un database MongoDB. Il percorso comprende anche il collegamento a MongoDB, la pubblicazione online e il collaudo della demo.

Il corso è gratuito e in italiano. Le lezioni, il codice sorgente e le dispense saranno pubblicati progressivamente sul canale YouTube DevAppSpace e nella repository ufficiale del corso.

- [Canale YouTube DevAppSpace](https://www.youtube.com/@DevAppSpace)
- [Demo dell’applicazione finale](https://lamiera70-corso-rubrica-mern.netlify.app/contatti)

## Modulo 1 — React e struttura frontend

**Lezioni 01–06**

| Lezione | Argomento | Risultato pratico |
|---|---|---|
| 01 | Introduzione al corso, organizzazione del progetto e creazione della prima app React con Vite | Prima applicazione React funzionante |
| 02 | React, Vite, npm, HMR, build e preview | Ambiente frontend e comandi essenziali |
| 03 | Componenti React, JSX, import/export | Componenti riutilizzabili |
| 04 | Navbar, Flexbox e CSS | Struttura grafica e navigazione |
| 05 | React Router, Routes, Route e pagine | Navigazione tra pagine |
| 06 | NavLink, pagina 404 e rotta jolly | Collegamenti attivi e gestione delle rotte inesistenti |

**Risultato del modulo:** una prima applicazione React navigabile.

## Modulo 2 — Rubrica React con dati locali

**Lezioni 07–10**

| Lezione | Argomento | Risultato pratico |
|---|---|---|
| 07 | Array di oggetti, tabella React e `map()` | Visualizzazione dei contatti |
| 08 | `useState`, aggiornamento dello stato e immutabilità | Stato dinamico della rubrica |
| 09 | Modulo di inserimento e input controllati | Raccolta dei dati dal form |
| 10 | Eliminazione contatti con `filter()` | Aggiornamento della tabella senza mutare lo stato |

**Risultato del modulo:** rubrica funzionante nel browser con dati temporanei.

## Modulo 3 — Prime API Express

**Lezioni 11–14**

| Lezione | Argomento | Risultato pratico |
|---|---|---|
| 11 | Node.js, Express, CommonJS e primo server | Avvio del backend |
| 12 | Rotte GET, JSON e array backend | Prima API di lettura |
| 13 | `req.params`, `find()`, `Number()`, HTTP 404 e `return` | Ricerca per identificativo e risposte HTTP |
| 14 | `req.query`, `filter()`, ricerca per nome e `toLowerCase()` | Parametri query e filtri backend |

**Risultato del modulo:** prime API Express per leggere i contatti.

## Modulo 4 — Collegamento React–Express e CRUD

**Lezioni 15–23**

| Lezione | Argomento | Risultato pratico |
|---|---|---|
| 15 | Prima `fetch` GET, `useEffect`, CORS, `.then()` e `.catch()` | Contatti Express mostrati in React |
| 16 | HTTP POST, `express.json()`, `req.body`, UUID e status HTTP | Creazione di un contatto tramite API |
| 17 | `fetch` POST dal modulo React | Inserimento dal frontend |
| 18 | Validazione dei dati POST e gestione degli errori | Messaggi di errore e conferma |
| 19 | HTTP PUT e aggiornamento dell'array Express | API di modifica |
| 20 | Pulsante Modifica e modulo React | Preparazione dei dati da modificare |
| 21 | `fetch` PUT e aggiornamento della tabella | Modifica completa dal frontend |
| 22 | HTTP DELETE e `fetch` DELETE | Eliminazione dal frontend |
| 23 | Revisione CRUD, caricamento ed errori | Rubrica React–Express completa |

**Risultato del modulo:** operazioni CRUD complete con dati temporanei nel backend.

## Modulo 5 — MongoDB e Mongoose

**Lezioni 24–32**

| Lezione | Argomento | Risultato pratico |
|---|---|---|
| 24 | Introduzione a MongoDB, documenti e collezioni | Comprensione del database documentale |
| 25 | MongoDB locale, Compass e primo database | Database `corso_rubrica_mern` |
| 26 | Installazione Mongoose e collegamento con `.env` | Connessione database dal server |
| 27 | Schema e modello Contatto | Definizione della struttura dati |
| 28 | GET con Mongoose `find()` | Contatti MongoDB mostrati in React |
| 29 | POST con Mongoose `create()` | Inserimento persistente |
| 30 | PUT con Mongoose e ObjectId | Modifica persistente |
| 31 | DELETE con Mongoose | Eliminazione persistente |
| 32 | Validazioni Mongoose e gestione errori | CRUD consolidato |

**Risultato del modulo:** rubrica con dati permanenti in MongoDB.

## Modulo 6 — Cloud, deploy e collaudo della demo

**Lezioni 33–36**

| Lezione | Argomento | Risultato pratico |
|---|---|---|
| 33 | MongoDB Atlas e database cloud | Database online collegato a Express |
| 34 | Deploy del backend Express su Railway | API pubbliche e CORS configurato |
| 35 | Deploy del frontend React su Netlify | Rubrica online collegata al backend |
| 36 | Collaudo della demo; GET/POST/PUT/DELETE, F5, persistenza e messaggi | CRUD verificato e routing Netlify corretto con `_redirects` |

**Risultato del modulo:** demo MERN online funzionante e collaudata.

## Conclusione del corso

**Totale:** 36 lezioni suddivise in 6 moduli. La rubrica realizzata è una **demo didattica pubblica**, senza login e autorizzazione: per le prove utilizzare esclusivamente dati fittizi.
