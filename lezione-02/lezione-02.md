# Rubrica Pro MERN — DevAppSpace
## Lezione 02 — React, Vite e npm

**Tecnologie e strumenti:** React, Vite, JavaScript, JSX, CSS, Node.js, npm ed ESLint

---

## Obiettivi della lezione

- Comprendere le responsabilità di React, Vite e npm.
- Avviare e interrompere il server di sviluppo.
- Comprendere il file `package.json`, le dipendenze e gli script npm.
- Distinguere `node_modules/` da `package-lock.json`.
- Comprendere la configurazione ESLint adottata nel corso.
- Modificare il titolo dell'applicazione e osservare l'aggiornamento HMR.

Partiamo dal progetto della Lezione 01: non è necessario creare una nuova applicazione con Vite. La cartella della Lezione 02 contiene già il codice predisposto.

---

## Struttura del progetto

```text
lezione-02/
│
├── client/
│   ├── node_modules/
│   ├── public/
│   │   └── favicon.png
│   ├── src/
│   │   ├── assets/
│   │   ├── App.jsx
│   │   ├── App.css
│   │   ├── index.css
│   │   └── main.jsx
│   ├── .gitignore
│   ├── index.html
│   ├── package.json
│   ├── package-lock.json
│   ├── eslint.config.js
│   └── vite.config.js
│
└── lezione-02.md
```

**Nota:** lo schema mostra i file principali. `node_modules/` viene generata durante l'installazione; `dist/` verrà generata con la build. Entrambe sono escluse dalla pubblicazione su GitHub. Il backend sarà introdotto nella Lezione 11.

---

## Concetti fondamentali

### 1. React

React è una libreria JavaScript per costruire interfacce utente attraverso componenti. Un componente è una parte dell'interfaccia che possiamo definire, combinare e riutilizzare.

Nel nostro progetto il componente principale è `App`. Nelle prossime lezioni suddivideremo l'interfaccia in componenti più piccoli.

### 2. Vite

Vite è uno strumento di sviluppo e build per applicazioni web. Nel nostro progetto avvia il server locale, elabora JSX e CSS, aggiorna rapidamente i moduli modificati e prepara i file per la pubblicazione.

### 3. npm e Node.js

Node.js permette di eseguire JavaScript al di fuori del browser. In questa fase lo utilizziamo per gli strumenti di sviluppo del frontend, non ancora per il backend della rubrica.

npm permette di installare e gestire pacchetti JavaScript ed eseguire gli script del progetto.

| Strumento | Responsabilità |
|---|---|
| React | Costruisce e aggiorna l'interfaccia |
| Vite | Gestisce sviluppo e build |
| npm | Installa pacchetti ed esegue script |
| ESLint | Analizza il codice e segnala problemi |

**Versione Node.js di riferimento:** 22.17.0. Per controllare il proprio ambiente:

```powershell
node -v
npm -v
```

Le versioni delle dipendenze possono richiedere specifiche versioni di Node.js. Utilizziamo quelle già predisposte e verificate nel corso, evitando aggiornamenti indiscriminati.

---

## Comandi utilizzati

Apriamo il terminale di VS Code nella cartella `lezione-02/client`. Se siamo nella radice della repository:

```powershell
cd lezione-02/client
```

### Installazione delle dipendenze

```powershell
npm install
```

Installa i pacchetti necessari al progetto. Non occorre ripetere l'installazione ogni volta che avviamo Vite: è necessaria, ad esempio, quando scarichiamo il progetto senza `node_modules/` o cambiamo le dipendenze.

### Avvio del server di sviluppo

```powershell
npm run dev
```

- `npm`: richiama il gestore dei pacchetti.
- `run`: esegue uno script definito in `package.json`.
- `dev`: nome dello script.

L'indirizzo normalmente utilizzato è `http://localhost:5173/`.

`localhost` indica il computer locale; `5173` è la porta del server di sviluppo. Se la porta è occupata, Vite può sceglierne un'altra: utilizziamo l'indirizzo mostrato nel terminale.

Per fermare il server utilizziamo `Ctrl + C`. Per riavviarlo eseguiamo nuovamente `npm run dev`.

### Controllo del codice

```powershell
npm run lint
```

Esegue ESLint sui file interessati dalla configurazione. Non avvia l'applicazione e non sostituisce le prove nel browser.

---

## Il file package.json

File: `client/package.json`.

È il file che descrive il progetto, i suoi script e le dipendenze. Questa è la configurazione adottata nella Lezione 01 e mantenuta nella Lezione 02:

```json
{
  "name": "client",
  "private": true,
  "version": "0.0.0",
  "type": "module",
  "scripts": {
    "dev": "vite",
    "build": "vite build",
    "lint": "eslint .",
    "preview": "vite preview"
  },
  "dependencies": {
    "react": "^19.3.1",
    "react-dom": "^19.3.1"
  },
  "devDependencies": {
    "@eslint/js": "^10.0.1",
    "@vitejs/plugin-react": "^6.1.2",
    "eslint": "^10.13.0",
    "eslint-plugin-react-hooks": "^7.1.1",
    "eslint-plugin-react-refresh": "^0.5.7",
    "globals": "^17.13.0",
    "vite": "^8.3.5"
  },
  "overrides": {
    "minimatch": "^11.0.1"
  }
}
```

### Proprietà principali

| Proprietà | Funzione |
|---|---|
| `name` | Nome del pacchetto locale |
| `private: true` | Impedisce la pubblicazione accidentale del pacchetto su npm |
| `version` | Versione del progetto |
| `type: "module"` | Indica a Node.js di trattare i file `.js` del pacchetto come moduli ES |
| `scripts` | Comandi eseguibili con npm |
| `dependencies` | Dipendenze dell'applicazione |
| `devDependencies` | Dipendenze usate per sviluppo, analisi e build |
| `overrides` | Vincoli sulla risoluzione delle dipendenze |

Il formato è JSON (JavaScript Object Notation): le chiavi e le stringhe usano doppi apici, i valori sono separati da virgole e non sono ammessi commenti o virgole finali.

### Script npm

| Comando | Script eseguito | Funzione |
|---|---|---|
| `npm run dev` | `vite` | Avvia lo sviluppo locale |
| `npm run build` | `vite build` | Genera la versione di produzione |
| `npm run lint` | `eslint .` | Analizza il codice |
| `npm run preview` | `vite preview` | Serve localmente la build già generata |

Gli script utilizzano gli eseguibili delle dipendenze locali: non occorre installare Vite o ESLint globalmente.

### Dependencies

```json
"dependencies": {
  "react": "^19.3.1",
  "react-dom": "^19.3.1"
}
```

- `react`: fornisce le funzionalità della libreria, ad esempio componenti e Hooks.
- `react-dom`: collega React al DOM del browser; contiene anche `createRoot`.

Nelle prossime lezioni aggiungeremo altre dipendenze solo quando serviranno, ad esempio React Router per la navigazione.

### DevDependencies

| Pacchetto | Funzione |
|---|---|
| `vite` | Server di sviluppo e build |
| `@vitejs/plugin-react` | Integrazione React con Vite, compreso Fast Refresh |
| `eslint` | Motore di analisi statica |
| `@eslint/js` | Configurazioni consigliate per JavaScript |
| `eslint-plugin-react-hooks` | Controlli sulle regole di React e degli Hooks |
| `eslint-plugin-react-refresh` | Controlli relativi alla compatibilità dei moduli con Fast Refresh |
| `globals` | Elenchi di variabili globali, ad esempio quelle del browser |

Questi strumenti sono necessari nella fase di sviluppo o compilazione. Il browser riceve i file prodotti dalla build, non l'intera cartella `node_modules/`. Anche un servizio che genera la build deve poter installare gli strumenti di sviluppo necessari.

### Versioni e simbolo ^

Consideriamo la versione `^19.3.1` di React. Il simbolo `^` consente, in questo caso, aggiornamenti compatibili dalla versione 19.3.1 fino a prima della 20.0.0, secondo le regole del versionamento semantico.

Il numero dichiarato in `package.json` non è necessariamente la versione effettivamente installata: per quella consultiamo `package-lock.json` oppure `npm ls react`.

### Override di minimatch

```json
"overrides": {
  "minimatch": "^11.0.1"
}
```

`minimatch` è un pacchetto utilizzato per confrontare percorsi e nomi con pattern glob, ad esempio `**/*.js`. Nel nostro progetto è una dipendenza indiretta degli strumenti di analisi del codice.

La sezione `overrides` permette a npm di imporre un vincolo anche alle dipendenze transitive. Qui chiediamo che le occorrenze di `minimatch` siano risolte nell'intervallo indicato, dalla 11.0.1 fino a prima della 12.0.0.

**Motivazione nel corso:** mantenere la configurazione delle dipendenze già concordata e verificata nella Lezione 01. L'override non è necessario in ogni progetto Vite e non è una garanzia generale di sicurezza: può modificare le versioni attese da altri pacchetti. Per questo lo conserviamo insieme al lockfile e controlliamo installazione e lint.

Per vedere quali pacchetti dipendono da `minimatch` e le versioni risolte:

```powershell
npm ls minimatch
```

Non rimuoviamo o cambiamo l'override senza una verifica specifica delle dipendenze e della compatibilità.

---

## node_modules e package-lock.json

### node_modules/

Contiene i pacchetti installati da npm, sia quelli dichiarati direttamente sia quelli richiesti da altri pacchetti (dipendenze transitive).

Non modifichiamo manualmente i file contenuti in questa cartella e non la pubblichiamo su GitHub.

### package-lock.json

È generato e aggiornato da npm. Registra le versioni risolte, l'albero delle dipendenze e altre informazioni necessarie a riprodurre l'installazione.

| Elemento | Contenuto | GitHub |
|---|---|---|
| `package.json` | Dipendenze richieste e intervalli di versione | Sì |
| `package-lock.json` | Versioni risolte e struttura delle dipendenze | Sì |
| `node_modules/` | Pacchetti installati localmente | No |
| `dist/` | File generati dalla build | No, nel nostro corso |

`npm install` utilizza il lockfile quando è compatibile con `package.json` e può aggiornarlo quando necessario. Come approfondimento, `npm ci` esegue un'installazione pulita a partire dal lockfile, richiede che sia coerente con `package.json` e non lo aggiorna.

Nel corso utilizziamo `npm install` per le installazioni e gli aggiornamenti concordati, conservando il lockfile risultante.

### Verifica delle dipendenze

```powershell
npm audit
```

Controlla le vulnerabilità note segnalate dal registro npm per le dipendenze del progetto. L'installazione normalmente include già un controllo di audit. Zero vulnerabilità rilevate non significa che il progetto sia privo di qualunque rischio.

Non utilizziamo `npm audit fix` automaticamente: prima analizziamo le segnalazioni e le eventuali conseguenze degli aggiornamenti.

---

## Configurazione ESLint

ESLint è uno strumento di analisi statica: controlla il sorgente senza dover eseguire l'applicazione. Aiuta a individuare errori e schemi di codice problematici, ma non garantisce da solo che il programma funzioni.

File: `client/eslint.config.js`.

```javascript
import js from "@eslint/js";
import globals from "globals";
import reactHooks from "eslint-plugin-react-hooks";
import reactRefresh from "eslint-plugin-react-refresh";
import { defineConfig, globalIgnores } from "eslint/config";

export default defineConfig([
  globalIgnores(["dist"]),
  {
    files: ["**/*.{js,jsx}"],
    extends: [
      js.configs.recommended,
      reactHooks.configs.flat.recommended,
      reactRefresh.configs.vite,
    ],
    languageOptions: {
      globals: globals.browser,
      parserOptions: {
        ecmaFeatures: { jsx: true },
      },
    },
    rules: {
      "no-unused-vars": "warn",
      "react-hooks/exhaustive-deps": "warn",
      "no-console": "off",
    },
  },
]);
```

### 1. Import e configurazione

- `js`: configurazioni JavaScript consigliate del pacchetto `@eslint/js`.
- `globals`: elenco delle variabili globali disponibili nei diversi ambienti.
- `reactHooks`: configurazioni e regole relative a React e agli Hooks.
- `reactRefresh`: controlli sulla compatibilità con Fast Refresh.
- `defineConfig`: funzione per definire la configurazione ESLint.
- `globalIgnores`: funzione per escludere file o cartelle dall'analisi.

Utilizziamo il formato moderno di configurazione ESLint, chiamato *flat config*.

### 2. File analizzati ed esclusi

```javascript
globalIgnores(["dist"])
```

Esclude la cartella della build, perché contiene codice generato. ESLint ignora già `node_modules/` per impostazione predefinita.

```javascript
files: ["**/*.{js,jsx}"]
```

Applica questa configurazione ai file JavaScript e JSX, anche nelle sottocartelle.

### 3. Preset consigliati

```javascript
extends: [
  js.configs.recommended,
  reactHooks.configs.flat.recommended,
  reactRefresh.configs.vite,
]
```

Un preset è un insieme di regole già predisposto.

| Preset | Funzione |
|---|---|
| `js.configs.recommended` | Attiva controlli JavaScript consigliati, tra cui variabili non definite |
| `reactHooks.configs.flat.recommended` | Attiva controlli consigliati su Hooks e regole di React |
| `reactRefresh.configs.vite` | Adatta i controlli sugli export dei componenti all'integrazione Vite |

Conserviamo i preset: non disattiviamo indiscriminatamente i controlli React. Gli Hooks saranno studiati nelle lezioni successive.

### 4. Impostazioni del linguaggio

```javascript
languageOptions: {
  globals: globals.browser,
  parserOptions: {
    ecmaFeatures: { jsx: true },
  },
},
```

- `globals.browser`: comunica a ESLint che nomi come `window` e `document` sono disponibili nell'ambiente browser.
- `jsx: true`: consente al parser di analizzare la sintassi JSX.

Non occorre dichiarare esplicitamente `ecmaVersion: "latest"` e `sourceType: "module"` per questi file: la flat config utilizza già tali impostazioni predefinite per i file JavaScript pertinenti. Questa semplificazione non disattiva i controlli.

### 5. Regole personalizzate

```javascript
rules: {
  "no-unused-vars": "warn",
  "react-hooks/exhaustive-deps": "warn",
  "no-console": "off",
},
```

Le regole locali possono modificare la severità stabilita dai preset. ESLint distingue `error` (errore), `warn` (avviso) e `off` (regola disattivata).

**no-unused-vars: warn**

Segnala variabili dichiarate ma non utilizzate come avvisi. Esempio didattico:

```javascript
const nomeRubrica = "Rubrica Pro MERN";
```

Se questa variabile non viene utilizzata, ESLint può segnalarla. È preferibile rimuovere il codice inutilizzato; l'avviso non blocca normalmente il comando lint.

**react-hooks/exhaustive-deps: warn**

Segnala dipendenze mancanti o problematiche negli Hooks che prevedono un elenco di dipendenze, ad esempio `useEffect`. Manteniamo la segnalazione per imparare a gestire correttamente gli Hooks nelle lezioni successive. Un avviso non è un motivo per ignorare un possibile errore di comportamento.

**no-console: off**

Consente di utilizzare `console.log()` a fini didattici e di debug:

```javascript
console.log("Applicazione avviata");
```

La regola è disattivata esplicitamente; non significa che i log siano necessari o che si possano stampare dati riservati. Nelle applicazioni reali i log vanno gestiti con attenzione.

Non abbiamo disattivato le altre regole React, compresa `react-hooks/set-state-in-effect` quando inclusa nel preset.

### 6. Differenze rispetto al progetto iniziale

I template Vite cambiano nel tempo. Confrontiamo quindi la nostra configurazione con i file originali del corso, senza presumere che ogni versione di Vite abbia lo stesso template.

| Aspetto | Configurazione adottata | Motivazione |
|---|---|---|
| `@types/react` e `@types/react-dom` | Non dichiarati direttamente | Progetto JavaScript senza necessità di tali dipendenze dirette; possono comunque aiutare l'editor con tipi e suggerimenti |
| Preset JavaScript, Hooks e Refresh | Conservati | Mantenere i controlli consigliati |
| `ecmaVersion` e `sourceType` | Non dichiarati esplicitamente | Utilizzare i default della flat config |
| `no-unused-vars` | `warn` | Conservare la segnalazione senza trasformarla in errore |
| `react-hooks/exhaustive-deps` | `warn` esplicito | Rendere chiara la severità scelta, anche se il preset può già prevederla |
| `no-console` | `off` esplicito | Consentire i log didattici |
| `minimatch` | Override globale `^11.0.1` | Conservare la risoluzione concordata e verificata |

Nella versione originale della Lezione 02 l'override era limitato a ESLint e fissava `minimatch` a `11.0.3`. La configurazione adottata ha invece un ambito più ampio e un intervallo di versione: il lockfile è quindi importante per mantenere le versioni risolte.

**Nota:** il progetto contiene già questi file. Non è necessario modificarli per seguire la lezione. Le personalizzazioni sono scelte del corso, non requisiti generali di React o Vite.

---

## File fondamentali di React e Vite

| File | Funzione |
|---|---|
| `index.html` | Documento HTML iniziale |
| `main.jsx` | Crea la radice React e renderizza App |
| `App.jsx` | Componente principale |
| `App.css` | Stili associati ad App |
| `index.css` | Stili globali |
| `vite.config.js` | Configurazione di Vite |

### client/index.html

Le righe fondamentali sono:

```html
<div id="root"></div>
<script type="module" src="/src/main.jsx"></script>
```

Il primo elemento è il contenitore gestito da React. Il secondo carica il modulo che avvia l'applicazione. Durante lo sviluppo Vite elabora JSX affinché il browser possa eseguirlo come JavaScript.

Nella sezione `head` utilizziamo la favicon PNG del corso:

```html
<link rel="icon" type="image/png" href="/favicon.png" />
```

Il file è `client/public/favicon.png`: la nuova immagine mostra le lettere rosse MS. Vite serve le risorse di `public/` dalla radice e le copia nella build. Il nome del file rimane invariato anche se sostituiamo l'immagine.

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

`document.getElementById('root')` individua il contenitore HTML; `createRoot()` crea la radice React e `.render()` visualizza il componente `App`. `StrictMode` attiva controlli aggiuntivi durante lo sviluppo.

### client/vite.config.js

```javascript
import react from '@vitejs/plugin-react'
import { defineConfig } from 'vite'

// https://vite.dev/config/
export default defineConfig({
  plugins: [react()],
})
```

`defineConfig()` definisce la configurazione di Vite. Il plugin `react()` integra React nel processo di sviluppo, consentendo anche Fast Refresh.

---

## Codice realizzato

### client/src/App.jsx

Rispetto alla Lezione 01 cambia soltanto il titolo visualizzato dal componente.

**Prima**

```jsx
<h1>Rubrica Pro</h1>
```

**Dopo**

```jsx
<h1>Rubrica Pro MERN</h1>
```

Il file completo della Lezione 02 è:

```jsx
import "./App.css";

function App() {
  return (
    <div className="app">
      <h1>Rubrica Pro MERN</h1>
      <p>La mia prima applicazione MERN</p>
    </div>
  );
}

export default App;
```

- `import "./App.css"` carica gli stili associati al componente.
- `function App()` definisce il componente.
- `return` restituisce il JSX da visualizzare.
- `className` assegna la classe CSS `app`.
- `export default App` rende disponibile il componente per l'importazione in `main.jsx`.

`App.css` e `index.css` rimangono invariati rispetto alla Lezione 01. Il primo contiene gli stili della classe `.app` e dei suoi elementi; il secondo definisce gli stili generali della pagina. I CSS tradizionali non sono isolati automaticamente per componente.

---

## HMR — Hot Module Replacement

HMR consente a Vite di aggiornare i moduli modificati durante lo sviluppo senza dover necessariamente ricaricare l'intera pagina.

Con il plugin React, Fast Refresh permette di aggiornare i componenti e, quando possibile, conservare il loro stato. Alcune modifiche richiedono comunque un ricaricamento completo.

### Prova pratica

1. Avviamo Vite con `npm run dev` e apriamo il browser.
2. Lasciamo attivo il server e modifichiamo temporaneamente il titolo in `client/src/App.jsx`:

```jsx
<h1>Rubrica Pro MERN - Test HMR</h1>
```

3. Salviamo con `Ctrl + S` e osserviamo il nuovo titolo nel browser, senza ricaricare manualmente la pagina.
4. Ripristiniamo il titolo definitivo:

```jsx
<h1>Rubrica Pro MERN</h1>
```

La modifica temporanea serve esclusivamente a dimostrare l'aggiornamento automatico e non fa parte del codice finale della lezione.

**Nota:** la nostra applicazione non contiene ancora stato React; questa prova mostra l'aggiornamento dell'interfaccia, non la conservazione dello stato, che studieremo più avanti.

---

## Cenno agli script di produzione

Nel `package.json` sono già presenti due script che useremo più avanti:

- `npm run build`: genera i file ottimizzati per la distribuzione, normalmente in `client/dist/`.
- `npm run preview`: serve localmente la build già generata, per controllarla prima della pubblicazione. Non è un server di produzione.

La dimostrazione pratica e l'approfondimento di questi comandi sono rimandati alla **Lezione 36**, dedicata alla verifica finale dell'applicazione pubblicata. Nella Lezione 02 lavoriamo soltanto con il server di sviluppo, npm ed ESLint.

---

## Risultato della lezione

Nel browser visualizziamo il titolo **Rubrica Pro MERN**, il testo **La mia prima applicazione MERN** e la nuova favicon PNG.

Nella revisione del progetto sono stati confermati:

- Installazione delle dipendenze con `npm install`: 141 pacchetti aggiunti e 0 vulnerabilità segnalate.
- Controllo con `npm run lint`: nessun errore o avviso.
- Avvio dell'applicazione nel browser e aggiornamento HMR.

La configurazione npm ed ESLint concordata nella Lezione 01 è mantenuta anche nella Lezione 02. Le prove di build e preview sono rimandate alla Lezione 36.

Nella prossima lezione approfondiremo i componenti React, JSX e import/export, organizzando l'interfaccia in componenti riutilizzabili.

## Materiale del corso

- [Repository ufficiale DevAppSpace](https://github.com/lamiera70/devappspace-rubrica-mern)
- [Programma completo del corso](../indice-corso.md)
- [Canale YouTube DevAppSpace](https://www.youtube.com/@DevAppSpace)
- [Demo dell'applicazione finale](https://lamiera70-corso-rubrica-mern.netlify.app/contatti)

La demo è pubblica e priva di autenticazione: utilizzare esclusivamente dati fittizi.

## Documentazione ufficiale

- [React — Your First Component](https://react.dev/learn/your-first-component)
- [React — eslint-plugin-react-hooks](https://react.dev/reference/eslint-plugin-react-hooks)
- [Vite — Getting Started](https://vite.dev/guide/)
- [Vite — Features e HMR](https://vite.dev/guide/features.html)
- [Vite — Building for Production](https://vite.dev/guide/build.html)
- [Vite — Deploying a Static Site e preview](https://vite.dev/guide/static-deploy.html)
- [npm — package.json](https://docs.npmjs.com/cli/v11/configuring-npm/package-json/)
- [npm — package-lock.json](https://docs.npmjs.com/cli/v11/configuring-npm/package-lock-json/)
- [npm — npm install](https://docs.npmjs.com/cli/v11/commands/npm-install/)
- [npm — npm ci](https://docs.npmjs.com/cli/v11/commands/npm-ci/)
- [ESLint — Configuration Files](https://eslint.org/docs/latest/use/configure/configuration-files)
- [ESLint — Language Options](https://eslint.org/docs/latest/use/configure/language-options)
- [ESLint — Configure Rules](https://eslint.org/docs/latest/use/configure/rules)
