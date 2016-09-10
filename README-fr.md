# react-howto

Quand on découvre React (ou le frontend en général) on peut trouver l'écosystème troublant.
Il y a des raisons à ça.

* React était historiquement destiné aux adeptes précoces et aux experts
* Facebook n'ouvre au public que ce qu'il utilise et ne se concentre donc pas sur les outils nécessaires à des projets d'ampleur inférieure
* Beaucoup de guides sur React véhiculent une mauvaise image

Tout au long de ce document, je vais partir du principe que vous avez déjà réalisé une page web avec HTML, CSS et JavaScript.

## Pourquoi devriez-vous m'écouter ?

Il y a énormément de conseils contradictoires dans la nature ; pourquoi m'écouter ?

Je fais parti de l'équipe de Facebook qui a construit React et l'a ouvert au public. Je ne travaille plus pour Facebook mais pour une petite start-up donc j'ai également un point de vue externe.

## Comment aborder l'écosystème React

Tout programme repose sur un assemblage de technologies, et il vous faut comprendre assez de cet assemblage pour construire votre application. La raison pour laquelle aborder les outils de l'écosystème React semble insurmontable est qu'on ne les présente pas dans le bon ordre.

Vous devriez apprendre, dans cet ordre, **sans sauter d'étape et une à la fois** :

* [React en lui même](#apprendre-react-en-lui-même)
* [`npm`](#apprendre-npm)
* [Les concaténateurs de fichiers JavaScript](#apprendre-les-concaténateurs-javascript)
* [ES6](#apprendre-es6)
* [Routage](#apprendre-le-routage)
* [Flux](#apprendre-flux)

**Vous n'avez pas besoin de tout apprendre pour être productif avec React.** Ne sautez d'étape que si vous devez absolument résoudre un problème.

De plus, il y a quelques sujets dont on parle souvent dans la communauté React qui sont à utiliser prudemment, car moins stables. Ce sont des sujets intéressants mais plus compliqués à appréhender, moins répandus que les sujets précédents et **requis dans peu de cas**.

* [Les styles en ligne](#apprendre-les-styles-en-ligne)
* [Rendu côté serveur](#apprendre-le-rendu-côté-serveur)
* [Immutable.js](#apprendre-immutablejs)
* [Relay, Falcor, etc](#apprendre-relay-falcor-etc)

## Apprendre React en lui même

C'est une erreur commune de penser qu'il faut perdre du temps à mettre en place des outils pour commencer à apprendre React. Dans la documentation officielle vous trouverez un [template à copier-coller](https://facebook.github.io/react/docs/getting-started.html#quick-start-without-npm) et sauvegarder dans un fichier `.html` et pourrez démarrer tout de suite. **Aucun outil n'est nécessaire pour cette étape, n'apprenez pas à en mettre en place avant d'être à l'aise avec les bases de React.**

Je pense toujours que la manière la plus simple d'apprendre React est [le tutoriel officiel](https://facebook.github.io/react/docs/tutorial.html).

## Apprendre `npm`

`npm` est le gestionnaire de paquets de Node.js. C'est le moyen le plus répandu parmi les développeurs et concepteurs front-end de partager du code JavaScript. Il comprend un système de module appelé `CommonJS` et vous permet d'installer des outils utilisables en ligne de commande écrits en JavaScript. Lisez [cet article](http://0fps.net/2013/01/22/commonjs-why-and-how/) pour savoir pourquoi `CommonJS` est nécessaire pour les navigateurs, ou le [Wiki de la spécification CommonJS](http://wiki.commonjs.org/wiki/Introduction) pour découvrir l'API.

La plupart des composants réutilisables, bibliothèques et outils de l'écosystème React sont disponibles en tant que modules `CommonJS` et s'installent avec `npm`.

## Apprendre les concaténateurs JavaScript

En raison de limitations techniques pertinentes, les modules `CommonJS` (ceux qu'on trouve sur `npm`) ne peuvent pas être utilisés tels quels dans le navigateur. Il faut un concaténateur JavaScript pour empaqueter ces modules dans des fichiers `.js` qu'on pourra inclure grâce à une balise `<script>` dans une page web.

`webpack` et `browserify` sont des concaténateurs disponibles. Les deux sont satisfaisants, mais je préfère `webpack` car il propose des fonctionnalités qui facilitent le développement de grosses applications. Sa documentation pouvant être troublante, j'ai un [projet tout prêt pour commencer](https://github.com/petehunt/react-webpack-template) et j'ai écrit un [guide pour webpack](https://github.com/petehunt/webpack-howto) pour des cas plus complexes.

Ne pas confondre : `CommonJS` utilise la fonction `require()` pour importer des modules, et beaucoup de personnes pensent à tort que c'est lié au projet `require.js`. Pour des raisons techniques, je vous conseille de ne pas utiliser `require.js`. De plus il n'est pas très répandu dans l'écosystème React.

## Apprendre ES6

En dehors du JSX (que vous avez appris dans le tutoriel React), vous pouvez rencontrer une syntaxe inhabituelle dans certains exemples React. C'est de l'ES6, la dernière version de JavaScript que vous ne connaissez pas forcément. Comme c'est très récent, ce n'est pas encore supporté par les navigateurs, mais votre concaténateur peut le traduire pour vous avec la bonne configuration.

Si vous avez besoin d'avancer sur React, **vous n'êtes pas obligé d'apprendre ES6**, ou pouvez l'apprendre en chemin.

Il est possible que vous tombiez sur des exemples qui laissent supposer que les classes ES6 sont le moyen préconisé de créer des composants React. Ce n'est pas le cas, et la plupart des gens utilisent `React.createClass`, y compris Facebook.

## Apprendre le routage

Les applications "Single-page" sont à la mode en ce moment. Ce sont des pages web qui ne chargent qu'une fois, et quand l'utilisateur clique sur un lien ou un bouton, le JavaScript de la page met à jour la barre d'adresse, mais la page n'est pas rafraîchie. La gestion de la barre d'adresse est prise en charge par un **routeur**.


Le routeur le plus populaire dans l'écosystème React est [react-routeur](https://github.com/rackc/react-routeur). Si vous construisez une application single-page, utilisez-le, sauf si vous avez de bonnes raisons de ne pas le faire.

**N'utilisez pas de routeur si vous ne construisez pas une application single-page.** La plupart des projets commencent de toute façon en tant que petits composants dans une plus grande application.

## Apprendre Flux

Vous avez probablement entendu parler de flux. Il y a des *tas* de mauvaises informations concernant Flux qui circulent.

Beaucoup de gens qui veulent développer une application cherchent à définir leur modèle de données et pensent avoir besoin de flux pour ça. **Ce n'est pas la bonne manière d'intégrer Flux. Flux ne devrait être ajouté que lorsque beaucoup de composants ont déjà été construits.**

Les composants React sont organisés en hiérarchie. La plupart du temps votre modèle de données suit également une hiérarchie. Dans cette situation Flux ne vous apporte pas grand chose. Quelques fois cela dit, votre modèle de données n'est pas hiérarchique. Quand vos composants commencent à recevoir des `props` qui ne semblent pas lui être destinées, ou qu'un petit nombre de composants commencent à être très complexes, vous pouvez vous pencher sur Flux.

**Vous saurez quand vous aurez besoin de Flux. Si vous n'êtes pas sûr d'en avoir besoin, vous n'en avez pas besoin.**

Si vous avez décidé d'utiliser Flux, la plus répandue et mieux documentée des bibliothèques Flux est [Redux](http://redux.js.org). Il y a *énormément* d'alternatives disponibles, et vous pouvez être tenté de toutes les évaluer, mais je vous conseille vraiment d'opter pour la plus populaire.

## Apprendre les styles en ligne

Avant React, beaucoup de gens réutilisaient les styles CSS avec des feuilles de style compliquées construites avec des préprocesseurs comme SASS. Comme React rend la réutilisation des composants facile, vos feuilles de style peuvent être moins compliquées. Beaucoup de gens dans la communauté (moi y compris) essayent même de se débarasser des feuilles de style entièrement.

C'est un peu fou pour un bon nombre de raisons. Ça rend les mediaqueries plus complexes et il est possible qu'il existe des limitations relatives aux performances en utilisant cette technique. **En commençant React, utilisez le style comme vous le feriez normalement.**

Une fois que vous êtes à l'aise avec React, vous pouvez tester des méthodes alternatives. [BEM](https://en.bem.info/) en est une assez répandue. Je vous conseille d'éliminer votre préprocesseur CSS, car React vous donne un meilleur moyen de réutiliser les styles (en réutilisant les composants) et votre concaténateur peut générer des feuilles de style plus efficaces pour vous ([j'en ai parlé à OSCON](https://www.youtube.com/watch?v=VkTCL6NqmM6Y)). Malgré tout React fonctionne très bien avec un préprocesseur CSS.

Une autre option est d'utiliser [CSS modules](http://glenmaddern.com/articles/css-modules), plus particulièrement [react-css-modules](https://github.com/gajus/react-css-modules). Avec les modules CSS vous allez toujours écrire du CSS (ou SASS, LESS, Stylus), mais vous allez pouvoir organiser et composer vos fichiers CSS comme vous l'auriez fait avec les styles en ligne avec React. En utilisant des méthodes comme BEM, vous n'aurez même plus à vous soucier de vos noms de classes, le système de module va s'en charger pour vous.

## Apprendre le rendu côté serveur

Le rendu côté serveur est souvent appelé JavaScript "universel" ou "isomorphique". Ça veut dire que vous pouvez générer du HTML statique sur un serveur à partir de vos composants. Ça améliore le temps de chargement de la page car l'utilisateur n'a pas à attendre que le JS soit chargé pour voir l'interface, et React va réutiliser ce HTML plutôt que d'en générer un autre.

Vous avez besoin du rendu côté serveur dans le cas où votre rendu initial est trop lent ou si vous voulez améliorer votre référencement. Il est vrai que Google référence maintenant le contenu rendu côté client, mais le temps que le JS met à s'exécuter est pénalisant pour le référencement.

Le rendu côté serveur nécessite beaucoup d'outils pour être fait correctement. Dans la mesure où la majeure partie de vos composants pourront être rendus côté serveur sans même que vous ne les conceviez pour, vous devriez construire votre application d'abord, pour ensuite vous pencher sur le rendu côté serveur. Vous n'aurez pas besoin de réécrire tous vos composants pour le mettre en place.

## Apprendre Immutable.js

[Immutable.js](https://facebook.github.io/immutable-js/) propose un jeu de structures de données qui peuvent aider à résoudre des problèmes de performance sur des applications React. C'est une bonne bibliothèque et vous risquez de l'utiliser à mesure que vos applications grandissent, mais ce n'est pas utile si vous n'avez pas les performances en tête.

## Apprendre Relay, Falcor etc

Ce sont des technologies qui vous aident à réduire le nombre de requêtes AJAX. Elles sont encore très récentes, donc si vous n'avez pas de problème de requêtes, vous n'avez pas besoin de Relay ou Falcor.
