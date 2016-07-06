# react-howto

Se sei nuovo di React (o del frontend in generale) potresti trovare il suo ecosistema disorientante. Ecco alcune ragioni di questo:

* React storicamente e' pensato per early-adopters ed esperti
* Facebook rilascia open source solamente le cose che utilizza, quindi il focus di React non e' su progetti piu' piccoli di Facebook
* C'e' un sacco di cattivo markeging mascherato da "Guide per React"

In questo documento, assumero' daro' per scontato che su che tu abbia fatto una pagina web con HTML, CSS e Javascript prima d'ora.

## Perche' dovresti darmi retta?

Ci sono migliaia di consigli su React in conflitto tra di loro in giro, perche' dovresti ascoltarmi?

Sono stato uno dei membri originari del Facebook team che ha costruito e rilasciato open source React. Non lavoro piu' a Facebook, attualmente sono in una piccola start up, quindi ho anche una prospettiva estranea a Facebook.

## Come affrontare l'ecosistema di React

Tutto il software e' costruitu su uno stack di tecnologie, e tu devi essere in gradio di capire abbastanza di quello stack per costruire la tua app. I tools di React sembrano troppo complicati perche' sono sempre spiegati nell'ordine sbagliato.

Doveresti imparare, in questo orgine, **senza saltare niente o imparare contemporaneamente**: 

* [React stesso](#learning-react-itself)
* [`npm`](#learning-npm)
* [JavaScript “bundlers”](#learning-javascript-bundlers)
* [ES6](#learning-es6)
* [Routing](#learning-routing)
* [Flux](#learning-flux)

**Non ti serve imparare tutti questi tool per essere produttivo con React. **Passa al passo successivo solo se hai un problema da risolvere

Inoltre, ci sono alguni argomenti che sono spesso citati dalla comunita' React, e che sono "bleeding edge", all'avanguardia. Gli argomenti sotto sono interessanti, ma sono difficili da comprendere, sono molto meno popolari degli argomenti sopra e **non sono richiesti nella maggior parte delle applicazioni**
* [Inline styles](#learning-inline-styles)
* [Server rendering](#learning-server-rendering)
* [Immutable.js](#learning-immutablejs)
* [Relay, Falcor, etc](#learning-relay-falcor-etc)

## Imparare React Stesso

E' un errore comune che sia necessario configurare un sacco di strumenti per iniziare ad imparara React. Nella guida ufficiale troverai [un template HTML da copiare-incollare](https://facebook.github.io/react/docs/getting-started.html#quick-start-without-npm) puoi salvarlo come file  `.html` ed iniziare subio. **Non hai bisogno di configurare nessuno strumento particolare per fare questo, E non cominciare a studiare nessun altro tool finche' non padroneggi le basi di React.**


Penso ancora che il modo piu' facile di imparare React sia [Il Tutorial Ufficiale](https://facebook.github.io/react/docs/tutorial.html).

## Imparare `npm`
`npm` e' il  package manager di Node.js ed e' il modo piu' usato dai programmatori front-end e designer per condividire il codice Javascript. . Comprende un sistema di moduli chiamato `CommonJS` che ti consente di installare strumenti a linea di comando scritti in Javascript. Leggi [questo post](http://0fps.net/2013/01/22/commonjs-why-and-how/) per capire perche'  `CommonJS` e' necessario sul browser oppure la  [CommonJS Spec Wiki](http://wiki.commonjs.org/wiki/Introduction) per ulteriuri informazioni sulle  `CommonJS` API.

La maggior parte dei componenti riusabili, le librerie ed i tools nell'ecosistema React sono disponibili sotto forma di moduli `CommonJS` e sono installabili con `npm`.

## Imparare i javascript Bundlers

Per diverse ragioni tecniche i moduli `CommonJS` (i.e. qualunque cosa su `npm`) non puossono essere usati nativamente nel browser. Devi usare un Javascript "bundler" per creare un "impacchettare" questi moduli in un file   `.js` che puo' essere incluso nella tua pagina web tramita un tag `<script>`

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

## Learning Flux

You’ve probably heard of Flux. There’s a *ton* of misinformation about Flux out there.

A lot of people sit down to build an app and want to define their data model, and they think they need to use Flux to do it. **This is the wrong way to adopt Flux. Flux should only be added once many components have already been built.**

React components are arranged in a hierarchy. Most of the time, your data model also follows a hierarchy. In these situations Flux doesn’t buy you much. Sometimes, however, your data model is not hierarchical. When your React components start to receive `props` that feel extraneous, or you have a small number of components starting to get very complex, then you might want to look into Flux.

**You’ll know when you need Flux. If you aren’t sure if you need it, you don’t need it.**

If you have decided to use Flux, the most popular and well-documented Flux library is [Redux](http://redux.js.org/). There are *a lot* of alternatives out there, and you’ll be tempted to evaluate lots of them, but my advice is to just stick with the most popular one.

## Learning inline styles

Pre-React, a lot of people reused CSS styles with complicated style sheets built by preprocessors like SASS. Since React makes writing reusable components easy, your stylesheets can be less complicated. Many in the community (including myself) are experimenting with getting rid of stylesheets altogether.

This is a fairly crazy idea for a number of reasons. It makes media queries more difficult, and it's possible that there are  performance limitations using this technique. **When starting out with React, just style things the way you normally would.**

Once you've got a feel for how React works, you can look at alternate techniques. One popular one is [BEM](https://en.bem.info/). I recommend phasing out your CSS preprocessor, since React gives you a more powerful way to reuse styles (by reusing components) and your JavaScript bundler can generate more efficient stylesheets for you (I gave [a talk about this at OSCON](https://www.youtube.com/watch?v=VkTCL6Nqm6Y)). With that said, React, like any other JavaScript library, will work just fine with a CSS preprocessor.

Alternatively, you can also use [CSS Modules](http://glenmaddern.com/articles/css-modules), more specifically [react-css-modules](https://github.com/gajus/react-css-modules). With CSS Modules you'll still write CSS (or SASS/LESS/Stylus), but you can manage and compose your CSS files like you'd do with inline styles in React. And you don't need to worry about managing your class names using methodologies like BEM, as this will be handled for you under the hood by the module system.

## Learning server rendering

Server rendering is often called "universal" or "isomorphic" JS. It means that you can take your React components and render them to static HTML on the server. This improves initial startup performance because the user does not need to wait for JS to download in order to see the initial UI, and React can re-use the server-rendered HTML so it doesn't need to generate it client-side.

You need server rendering if you notice that your initial render is too slow or if you want to improve your search engine ranking. While it's true that Google now indexes client-rendered content, as of January 2016 every time it's been measured it's been shown to negatively affect ranking, potentially because of the performance penalty of client-side rendering.

Server rendering still requires a lot of tooling to get right. Since it transparently supports React components written without server rendering in mind, you should build your app first and worry about server rendering later. You won't need to rewrite all of your components to support it.

## Learning Immutable.js

[Immutable.js](https://facebook.github.io/immutable-js/) provides a set of data structures that can help to solve certain performance issues when building React apps. It's a great library, and you'll probably use it a lot in your apps moving forward, but it's completely unnecessary until you have an appreciation of the performance implications. 

## Learning Relay, Falcor etc

These are technologies that help you reduce the number of AJAX requests. They’re still very cutting-edge, so if you don’t have a problem with too many AJAX requests, you don’t need Relay or Falcor.
