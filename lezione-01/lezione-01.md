# Rubrica Pro MERN — DevAppSpace
## Lezione 01 — Introduzione e creazione del progetto

**Tecnologie e strumenti:** React, Vite, JavaScript, JSX, CSS, Node.js, npm ed ESLint  

---

## Obiettivi della lezione

- Comprendere la differenza tra frontend e backend.
- Organizzare il frontend nella cartella `client`; il backend sarà introdotto nella Lezione 11.
- Creare un'applicazione React utilizzando Vite.
- Installare le dipendenze con npm.
- Avviare il server di sviluppo.
- Comprendere il funzionamento di `index.html`, `main.jsx` e `App.jsx`.
- Creare e personalizzare un componente React.
- Separare il codice JSX dai fogli di stile CSS.

---

## Struttura del progetto

```text
lezione-01/
│
├── client/
│   ├── node_modules/
│   ├── public/
│   ├── src/
│   │   ├── assets/
│   │   ├── App.jsx
│   │   ├── App.css
│   │   ├── index.css
│   │   └── main.jsx
│   ├── index.html
│   ├── package.json
│   ├── package-lock.json
│   ├── eslint.config.js
│   └── vite.config.js
│
└── lezione-01.md

```

**Nota:** questa è la struttura locale della lezione. La cartella `node_modules/` viene generata da npm e non va pubblicata su GitHub. Il backend sarà aggiunto nella Lezione 11. La repository ufficiale del corso raccoglie le cartelle delle lezioni man mano che vengono pubblicate.

---

## Concetti fondamentali

### 1. Frontend

È la parte dell'applicazione visibile all'utente.

Utilizzeremo React per costruire l'interfaccia, gestire i contatti e navigare tra le pagine.

### 2. Backend

È la parte che riceve le richieste HTTP, elabora i dati e interagisce con il database.

Utilizzeremo Node.js, Express, MongoDB e Mongoose.

### 3. Come comunicano frontend e backend

```text
REACT (client)
      |
      | Richiesta HTTP
      v
EXPRESS (server)
      |
      | Operazioni sui dati
      v
MONGODB
      |
      | Risultato
      v
EXPRESS
      |
      | Risposta JSON
      v
REACT
```

Questo collegamento verrà realizzato nelle prossime lezioni.

---

## Comandi utilizzati

### Creazione progetto React

```powershell
npm create vite@latest client -- --template react
```

- `npm`: gestore dei pacchetti di Node.js.
- `create`: avvia lo strumento per creare un progetto.
- `vite@latest`: utilizza la versione più recente dello strumento di creazione del progetto Vite. Le versioni installate possono differire da quelle della lezione.
- `client`: nome della cartella di destinazione.
- `--`: separa gli argomenti di npm da quelli di Vite.
- `--template react`: seleziona React con JavaScript.

### Installazione delle dipendenze

```powershell
cd client
npm install
```

`cd client` entra nella cartella del frontend.

`npm install` installa le dipendenze dichiarate nel file `package.json`. Il file `package-lock.json` registra le versioni risolte delle dipendenze e va conservato.

Se hai scaricato il progetto della lezione da GitHub, non devi ricrearlo: entra nella cartella `client` ed esegui `npm install`.

### Avvio dell'applicazione

```powershell
npm run dev
```

Avvia il server di sviluppo di Vite.

Indirizzo normalmente utilizzato:

`http://localhost:5173/`

Per interrompere il server utilizziamo `Ctrl + C` nel terminale.

---

## File fondamentali di React

| File | Funzione |
|---|---|
| `index.html` | Pagina HTML iniziale |
| `main.jsx` | Crea la radice React e renderizza App |
| `App.jsx` | Componente principale dell'applicazione |
| `App.css` | Stili associati al componente App |
| `index.css` | Stili globali |
| `package.json` | Dipendenze e script npm |
| `vite.config.js` | Configurazione di Vite |
| `eslint.config.js` | Configurazione dei controlli ESLint |
| `package-lock.json` | Versioni risolte delle dipendenze |

### Collegamento tra i file

```text
index.html
    |
    v
main.jsx
    |
    v
App.jsx
    |
    v
Interfaccia visualizzata nel browser
```

---

## Codice realizzato

### client/src/App.jsx

```jsx
import "./App.css";

function App() {
  return (
    <div className="app">
      <h1>Rubrica Pro</h1>
      <p>La mia prima applicazione MERN</p>
    </div>
  );
}

export default App;
```

**Spiegazione:**

- `import "./App.css"` importa il foglio di stile.
- `function App()` definisce un componente React.
- `return` restituisce gli elementi JSX da visualizzare.
- `className` assegna una classe CSS.
- `export default App` permette di importare il componente in altri file.

### client/src/App.css

```css
.app {
  max-width: 1200px;
  margin: 0 auto;
  padding: 30px 20px;
  text-align: center;
}

.app h1 {
  color: #155eab;
  margin-bottom: 10px;
}

.app p {
  font-size: 18px;
  color: #555;
}
```

### client/src/index.css

```css
* {
  box-sizing: border-box;
}

body {
  margin: 0;
  font-family: Arial, sans-serif;
  background-color: #f4f6f9;
  color: #222;
}
```

### client/src/main.jsx

```jsx
import { StrictMode } from 'react'
import { createRoot } from 'react-dom/client'
import './index.css'
import App from './App.jsx'

createRoot(document.getElementById('root')).render(
  <StrictMode>
    <App />
  </StrictMode>,
)
```

`createRoot()` crea la radice React associata all'elemento HTML con `id="root"`.

`.render()` visualizza il componente `App` all'interno della radice.

`StrictMode` abilita controlli aggiuntivi durante lo sviluppo.

---

## Concetti CSS imparati

- `box-sizing: border-box`: include padding e bordi nelle dimensioni impostate.
- `max-width`: stabilisce la larghezza massima.
- `margin: 0 auto`: permette di centrare orizzontalmente un blocco con spazio disponibile.
- `padding`: definisce gli spazi interni.
- `text-align: center`: centra il testo.
- `background-color`: imposta il colore di sfondo.
- `color`: definisce il colore del testo.

**Nota:** i CSS tradizionali non sono isolati automaticamente per componente.

---

## Controllo del codice con ESLint

ESLint analizza il codice e segnala possibili problemi. Il progetto della lezione contiene già la configurazione in `client/eslint.config.js`.

Dalla cartella `client` possiamo eseguire:

```powershell
npm run lint
```

La configurazione mantiene i controlli consigliati per JavaScript e React Hooks. Le variabili inutilizzate e le dipendenze mancanti degli Hooks vengono segnalate come avvisi; `console.log()` è consentito.

Nel `package.json` della lezione è presente anche l'override di `minimatch`, utilizzato per la gestione delle dipendenze indirette di ESLint:

```json
"overrides": {
  "minimatch": "^11.0.1"
}
```

Non è necessario modificare queste impostazioni per seguire la lezione: utilizziamo i file già predisposti nel progetto. I comandi `npm run build` e `npm run preview` saranno approfonditi nella Lezione 02.

---

## Risultato della lezione

Nel browser visualizziamo il titolo **Rubrica Pro** e il testo **La mia prima applicazione MERN**, con gli stili CSS personalizzati.

Nella prossima lezione approfondiremo React, Vite, npm, HMR, build e preview.

## Materiale del corso

- [Repository ufficiale DevAppSpace](https://github.com/lamiera70/devappspace-rubrica-mern)
- [Programma completo del corso](../indice-corso.md)
- [Canale YouTube DevAppSpace](https://www.youtube.com/@DevAppSpace)
- [Demo dell'applicazione finale](https://lamiera70-corso-rubrica-mern.netlify.app/contatti)

La demo è pubblica e priva di autenticazione: utilizzare esclusivamente dati fittizi.
