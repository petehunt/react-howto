# react-howto

Se sei nuovo di React (o del frontend in generale) potresti trovare il suo ecosistema disorientante. Ecco alcune ragioni di questo:

* React storicamente e' pensato per early-adopters ed esperti
* Facebook rilascia open source solamente le cose che utilizza, quindi il focus di React non e' su progetti piu' piccoli di Facebook
* C'e' un sacco di cattivo marketing mascherato da "Guide per React"

In questo documento, assumero'che tu abbia gia' fatto una pagina web con HTML, CSS e Javascript prima d'ora.

## Perche' dovresti darmi retta?

Ci sono migliaia di consigli su React in conflitto tra di loro in giro, perche' dovresti ascoltarmi?

Sono stato uno dei membri originari del Facebook team che ha costruito e rilasciato open source React. Non lavoro piu' a Facebook, al momento lavoro in una piccola start up, quindi ho anche una prospettiva estranea a Facebook.

## Come affrontare l'ecosistema di React

Tutto il software e' costruito su uno stack di tecnologie, e tu devi saperne abbastanza di quello stack da essere in grado di creare la tua app. I tools di React sembrano troppo complicati perche' sono sempre spiegati nell'ordine sbagliato.

Doveresti imparare, in questo orgine, **senza saltare niente o imparare contemporaneamente**: 

* [React stesso](#learning-react-itself)
* [`npm`](#learning-npm)
* [JavaScript “bundlers”](#learning-javascript-bundlers)
* [ES6](#learning-es6)
* [Routing](#learning-routing)
* [Flux](#learning-flux)

**Non ti serve imparare tutti questi tool per essere produttivo con React.** Passa al passo successivo solo se hai un problema da risolvere

Inoltre, ci sono alguni argomenti che sono spesso citati dalla comunita' React, e che sono "bleeding edge", all'avanguardia. Gli argomenti sotto sono interessanti, ma sono difficili da comprendere, sono molto meno popolari degli argomenti sopra e **non sono richiesti nella maggior parte delle applicazioni**
* [Inline styles](#learning-inline-styles)
* [Server rendering](#learning-server-rendering)
* [Immutable.js](#learning-immutablejs)
* [Relay, Falcor, etc](#learning-relay-falcor-etc)

## Imparare React Stesso

E' un errore comune che sia necessario configurare un sacco di strumenti per iniziare ad imparara React. Nella guida ufficiale troverai [un template HTML da copiare-incollare](https://facebook.github.io/react/docs/getting-started.html#quick-start-without-npm) puoi salvarlo come file  `.html` ed iniziare subio. **Non hai bisogno di configurare nessuno strumento particolare per fare questo, E non cominciare a studiare nessun altro tool finche' non padroneggi le basi di React.**


Penso ancora che il modo piu' facile di imparare React sia [Il Tutorial Ufficiale](https://facebook.github.io/react/docs/tutorial.html).

## Imparare `npm`
`npm` e' il  package manager di Node.js ed e' il modo piu' usato dai programmatori front-end e dai designer per condividire il codice Javascript. . Comprende un sistema di moduli chiamato `CommonJS` che ti consente di installare strumenti a linea di comando scritti in Javascript. Leggi [questo post](http://0fps.net/2013/01/22/commonjs-why-and-how/) per capire perche'  `CommonJS` e' necessario sul browser oppure la  [CommonJS Spec Wiki](http://wiki.commonjs.org/wiki/Introduction) per ulteriuri informazioni sulle  `CommonJS` API.

La maggior parte dei componenti riusabili, le librerie ed i tools nell'ecosistema React sono disponibili sotto forma di moduli `CommonJS` e sono installabili con `npm`.

## Imparare i javascript Bundlers

Per diverse ragioni tecniche i moduli `CommonJS` (i.e. qualunque cosa su `npm`) non possono essere usati nativamente nel browser. Devi usare un Javascript "bundler" per creare un "impacchettare" questi moduli in un file   `.js` che puo' essere incluso nella tua pagina web tramita un tag `<script>`

Esempi di JavaScript bundlers sono `webpack` e `browserify`. Entrambi sono buone scelte, ma io preferisco `webpack` in quanto ha molte piu' funzionalita' che rendono lo sviluppo di grandi applicazioni piu' semplice. Visto che la documentazione puo' risultare di complicata, Ho un  [plug-and-play template per iniziare](https://github.com/petehunt/react-webpack-template) ed ho scrito una  [guida how-to per webpack](https://github.com/petehunt/webpack-howto) per casi piu' complessi.

Una cosa da tenere a mente: `CommonJS` usa la funzione `require()` per importare moduli, per questo molta gente si confonde e pensa che abbia qualcosa a che fare con un progetto chiamato  `require.js`. Per diverse ragioni tecniche, ti suggerirei di evitare `require.js`. Inoltre non e' molto popolare all'interno dell'ecosistema React.


## Imparare ES6

Oltre a JSX (che hai imparato nel tutorial React) potresti vedere un po' di sintassi strana negli esempi di React. E' ES6, ed e' l'ultima versione di Javascript, quindi potresti non averla ancora imparata. Siccome e' molto nuova,  non e' ancora supportata dai browsers, ma il tuo bundler puo' tradurla per te se opportunamente configurato.

Se vuoi iniziare velocemente con React, **puoi evitare di imparare ES6**, o puoi provare ad utilizzarlo strada facendo.

Potresti vedere qualche discussione sul fatto che le classi ES6 sono il modo principlare per creare i componenti React. Questo e' falso. Molta gente (Facebook inclusa) sta utilizzando `React.createClass()`.

## Imparare il Routing

Le “Single-page applications” vanno di moda in questi giorni. Sono pagine web che vengono caricate in una volta, dopodiche' quando l'utente schiaccia un link od un bottone, Il Javascript si occupa di aggiornare la pagina e la barra degli indirizzi, senza refreshare la pagina. La gestione della barra degli indirizzi e' effattuata da qualcosa chiamato  **router**.

Il router piu' popolare nell'ecosistema di React e' il [react-router](https://github.com/rackt/react-router). Se stai facendo una single-page application, usalo a meno che tu non abbia una buona ragione per non farlo.

**Non usare il router se non stai facendo una single-page application**. Molti progetti iniziano come un piccolo componente all'interno di una applicazion piu' grande.

## Imparare Flux

Probabilmente ai sentito parlare di Flux. Ci sono  *tonnellate* di false informazioni riguardo Flux.

Molte persone iniziano a costruire una app e vogliono definire il loro Modello di dati, e pensano che sia necessario usare Flux per farlo. ** Questo e' il modo sbagliato di adottare Flux. Flux dovrebbe essere aggiunto solamente dopo che molti componenti sono stati create **

I Componenti React sono organizzati in una  gerarchia. Molte bolte, il tuo data model  segue una gerarchia a sua volta. In queste situazioni Flux non aiuta molto. A volte, invece, il tuo data model non e' gerarchico. Quando i tuoi componenti React iniziano a ricevere `props` che sembrano estranee, o hai un piccolo numero di componenti che iniziano a diventare molto complessi, allora potresti voler dare un'occhiata a Flux. 

**Quando Flux ti servira', lo saprai. Se non sei sicuro di averne bisogno, non ti serve.**

Se hai deciso di usare Flux, La piu' famosa e meglio documentata libreria Flux e' [Redux](http://redux.js.org/). Ci sono  *un sacco* di alternative, e sarati tentatoto di provarne molte. Il mio consiglio e' di affidarti a quella piu' popolare.

## Imparare gli  inline styles

nell'era pre-React, molte persone riutilizzavano gli stili CSS conc complicati fogli di stile costruita da preprocessori come SASS. Visto che react rende lo scrivere componenti riutilizzabili facile, i tuoi fogli di stile possono essere meno complicati. Molti all'interno della comuniti (io compreso) stanno sperimentando il completo abbandono dei fogli di stile.

Pre-React, a lot of people reused CSS styles with complicated style sheets built by preprocessors like SASS. Since React makes writing reusable components easy, your stylesheets can be less complicated. Many in the community (including myself) are experimenting with getting rid of stylesheets altogether.
E' un'idea abbastanza folle per diverse ragioni. Rende le media queries difficili, ed e' possibile imbattersi in qualche problema di perfomance utilizzando qusta tecnica. **Quando inizi con React, utilizza gli stili come faresti normalmente.**

Una volta che capisci come funziona React, puoi dare un occhio a tecniche alternative. Una molto popolare e' [BEM](https://en.bem.info/).
Io raccomando la graduale eliminazione dei preprocessori CSS, in quanto React ti offre una modo piu' potente di riutilizzare gli stili (tramite il riutilizzo dei componenti) ed il tuoi Javascript bundler puo' ottimizzare gli stylesheets per te' (feci [un seminario riguardo questo all'OSCON](https://www.youtube.com/watch?v=VkTCL6Nqm6Y)).
Detto Questo, React, come altre librerie Javascript, funzionera' bene insieme ad un preprocessore CSS.

In alternativa, puoi anche utilizzare i [CSS Modules](http://glenmaddern.com/articles/css-modules), nello specifico [react-css-modules](https://github.com/gajus/react-css-modules). Con i CSS Modules scrivi sempre CSS (o SASS/LESS/Stylus), ma puoi gestire e comporre i tuoi file CSS come se stessi usando gli inline styles di React. E non ti devi preoccupare di gestire i nomi delle tue classi utilizzando metodologie come BEM, in quanto saranno gestite automaticamente dal sistema di modularizazione.


## Imparare il server rendering

Il Server rendering e' spesso chiamato  "universal"(universale) o "isomorphic"(isomorfico) JS. Vuold dire che poi prendere i tuoi componenti React e renderizzarli come HTML statico sul server. Questo migliora la prestazione iniziale perche' l'utente non deve aspettare che il JS sia scaricato per vedere la UI iniziale, inoltre React puo' riutilizzare l'HTML renderizzato lato server che non deve essere quindi generato lato client

Hai bisongno sel server rendering se noti che il tuo rendering iniziale e' troppo lento o se vuoi migliorare il tuo ranking sui motori di ricerca. Se e' vero che Goodle adesso indicizza il contenuto generato dal client, al Gennaio 2016 ogni volta che e' stato misurato a mostrato di influenzare negativamente il ranking, potenzialmente per via delle penalita' nella performance intodotte la client side rendering.

Il server rendering richiede ancora molta configurazione per funzionare correttamente. Sicoome e' supportato in maniera trasparente dai componenti React scritti senza il server side rendieng in mente, dovresti prima fare la tua app e solo successivamente preoccuparti del server rendering. Non ti servira' riscrivere ogni tuo componente per supportarlo.


## Imparare Immutable.js

[Immutable.js](https://facebook.github.io/immutable-js/) fornisce un insieme di strutture dati che ti aiutano a risolvere certi problemi di prestazioni mentre sviluppi applicazioni React.
E' una grande libraria, e probablimente la userai molto andando avanti nelle tue apps, ma e' completamente non necessaria finche' non avrai problemi di performance.

## Imparare Relay, Falcor etc

Sono tecnologie che ti aiutano a ridurre il numero di richieste AJAX. Sono ancora molto sperimentali, quindi se non hai un problema di troppe chiamate AJAX, non ti serve usare Realy o Falcor.
