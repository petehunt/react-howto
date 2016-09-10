# react-howto

Sí eres nuevo en React (o con el desarrollo front-end en general) puedes encontrarte con que este ecosistema sea confuso. Existen unas cuantas razones para ello.

* Históricamente React se ha enfocado en early-adopters y expertos.
* Facebook sólo libera lo que realmente usa, por lo que no se centra en herramientas para proyectos "más pequeños que Facebook"
* Hay muchos artículos de marketing enmascarados como guías de React

A lo largo de este documento, asumiré que tienes preparada una página con HTML, CSS y JavaScript.

## ¿Por qué escucharme a mí?

Hay un montón de consejos confusos sobre React ahí fuera, entonces ¿por qué escucharme a mí?

Fui miembro del equipo inicial de Facebook que construyó y liberó React. Ya no estoy en Facebook, ahora estoy en una pequeña StartUp, por lo que tengo también una perspectiva "no-Facebook".

## Cómo iniciar con React y su ecosistema

Todo software se construye con un stack tecnológico, y es necesario entender lo suficiente de ese stack como para construir una aplicación. La razón por la que el ecosistema de herramientas de React parece abrumador es porque siempre ha sido explicado en el orden incorrecto.

Debes aprenderlo en este orden, **sin saltarte ningún paso o hacerlo concurrentemente**:

* [React en sí](#aprendiendo-react-en-sí)
* [`npm`](#aprendiendo-npm)
* [JavaScript “bundlers”](#aprendiendo-javascript-bundlers)
* [ES6](#aprendiendo-es6)
* [Enrutamiento](#aprendiendo-enrutamiento)
* [Flux](#aprendiendo-flux)

**No necesitas aprender todas ellas para ser productivo con React.** Sólo dirígete al siguiente paso si tienes algún problema que necesita ser resuelto.

Adicionalmente, hay unos cuantos temas que a menudo son categorizados en la comunidad de React como "bleeding edge"<sup>[1](#f1)</sup>. Los temas de abajo son interesantes, pero difíciles de entender, de lejos menos populares que los de arriba y **no son requeridos por la mayoría de las aplicaciones**.
* [Estilos inline](#aprendiendo-estilos-inline)
* [Renderizado en el servidor](#aprendiendo-renderizado-en-el-servidor)
* [Immutable.js](#aprendiendo-immutablejs)
* [Relay, Falcor, etc.](#aprendiendo-relay-falcor-etc)

## Aprendiendo React en sí

Es un error común pensar que se necesita perder mucho tiempo preparando un entorno para iniciar el aprendizaje de React. En la documentación oficial la encontrarás en una [plantilla HTML de copia y pega](https://facebook.github.io/react/docs/getting-started.html#quick-start-without-npm) que puedes guardar en un fichero `.html` y empezar inmediatamente. **No se necesita ninguna herramienta para este paso, y no empieces a aprender sobre herramientas extras hasta que no te sientas cómodo con lo básico de React.**

Todavía pienso que la forma más fácil de aprender React es [el tutorial oficial](https://facebook.github.io/react/docs/tutorial.html).

## Aprendiendo `npm`

`npm` es el gestor de paquetes de Node.js y la forma más popular en la que diseñadores y desarrolladores de front-end comparten código JavaScript. Incluye un módulo de sistema llamado `CommonJS`, que te permite instalar herramientas de línea de comando escritas en JavaScript. Lee [este artículo](http://0fps.net/2013/01/22/commonjs-why-and-how/) para entender porque `CommonJS` es necesario en los navegadores, o la [CommonJS Spec Wiki](http://wiki.commonjs.org/wiki/Introduction) para más información en la API de `CommonJS`.

La mayoría de componentes reusables, librerías y herramientas en el ecosistema de React están disponibles como módulos `CommonJS` y se instalan con `npm`.

## Aprendiendo JavaScript bundlers

Hay muchas razones razones técnicas por la que los módulos `CommonJS` (p.ej. cualquiera en `npm`) no pueden ser usados nativamente en el navegador. Necesitas un  JavaScript “bundler” para "convertir" estos módulos en ficheros `.js` que puedas incluir en tus páginas web con un tag `<script>`.

Ejemplos de JavaScript bundlers incluye `webpack` y `browserify`. Ambos son buenas opciones, pero prefiero `webpack` ya que tiene muchas características que hacen que el desarrollo de aplicaciones grandes se más sencillo. Ya que su documentación puede ser confusa, les traigo una [plantilla plug-and-play para empezar](https://github.com/petehunt/react-webpack-template) y una [guía how-to para webpack](https://github.com/petehunt/webpack-howto) para usos mas complejos.

Una cosa a tener en cuenta: `CommonJS` utiliza la función `require()` para importar modules, por lo que mucha gente se confunde y piensa que tiene algo que ver con un proyecto llamado `require.js`. Por unas cuantas razones técnicas, te sugiero que evites utilizar `require.js`. Además, no es muy popular en el ecosistema de React.

## Aprendiendo ES6

Aparte de JSX (el cual has aprendido en el tutorial de React), Es posible que aparezca alguna sintaxis "divertida" en ejemplos de React. Esto se llama ES6, y es la última versión de JavaScript así que seguramente no lo hayas aprendido aún. Al ser tan nuevo, no está soportado en los navegadores aún, pero tu bundler puede traducirlo por ti con la configuración adecuada.

Si lo que desea es hacer las cosas con React, **puedes omitir el aprendizaje ES6**, o tratar de aprenderlo en el camino.

## Aprendiendo enrutamiento

Las “single-page applications” (o aplicaciones de página única) son las que están de moda estos días. Se trata de páginas que se cargan una vez, y cuando el usuario hace click en un enlace o botón, el JavaScript que está corriendo en la página actualiza la barra de direcciones, pero la página web no es recargada. La gestión de la barra de direcciones es hecha por algo llamado **router**.

El router más popular en el ecosistema de React es [react-router](https://github.com/rackt/react-router). Si estás haciendo una aplicación de página única, úsalo a no ser que tengas una buena razón para no hacerlo.

**No uses un router si no estás construyendo una aplicación de página única**. De cualquier manera la mayoría de proyectos comienzan como pequeños componentes dentro de una aplicación más grande.

## Aprendiendo Flux

Probablemente habrás oído hablar de Flux. Hay un *montón* de información errónea sobre Flux ahí fuera.

Muchas personas se sientan a construir una aplicación y quiere definir su modelo de datos, y piensan que necesitan Flux para hacerlo. **Esta es la manera incorrecta de adoptar Flux. Flux debería ser añadido sólo una vez que se han hecho ya algunos componentes.**

Los componentes de React están organizado en una jerarquía. La mayoría de las veces, tu modelo de datos también sigue una jerarquía. Es estas situaciones Flux no te aporta demasiado. A veces, sin embargo, tu modelo de datos no es jerárquico. Cuando tus componentes de React empiezan a recibir `props` que parecen extrañas,  o tienes un pequeño número de componentes que empiezan a ser muy complejos, entonces puede que quieras considerar usar Flux.

**Sabrás cuando necesitas Flux. Si no estás seguro de si lo necesitas, es que no lo necesitas.**

Si has decidido usar Flux, la librería más popular y bien documentada es [Redux](http://redux.js.org/). Hay *muchas* alternativas, y estarás tentado a revisar muchas de ellas, pero mi consejo es que te quedes sólo con la más popular.

## Aprendiendo estilos Inline

Antes de React, mucha gente reutilizaba hojas de estilos CSS con complicados estilos construidos con preprocesadores como SASS. React hace que escribir componentes reutilizables sea sencillo, tus hojas de estilo pueden ser menos complicadas. Muchos usuarios de la comunidad (incluido yo) están pensando deshacerse del todo de las hojas de estilo.

Puede parecer una idea bastante loca pero hay muchas razones. Hace las media queries más complicadas, y es posible que existan limitaciones en cuanto a rendimiento usando esta técnica. **Cuando empieces con React, sólo pone el estilo a las cosas de la forma que normalmente lo harías.**

Una vez entiendes cómo funciona React, puedes considerar técnicas alternativas. Una de las más populares es [BEM](https://en.bem.info/). Te recomiendo reducir gradualmente tus pre-procesadores CSS, ya que React te ofrece una manera más potente de reutilizar los estilos (reutilizacion de componentes) y tu bundler de JavaScript puede generar hojas de estilos más eficientes para ti (Yo di [una charla sobre esto en  OSCON](https://www.youtube.com/watch?v=VkTCL6Nqm6Y)). Dicho esto, React, como cualquier otra librería de JavaScript, funcionará bien con un preprocesador CSS.

## Aprendiendo renderizado en el servidor

El renderizado en el servidor (o server rendering) es a menudo llamado JavaScript "universal" o "isomórfico". Esto significa que puedes tomar tus componentes de React y renderizarlos como HTML estático en el servidor. Esto mejora el rendimiento de la carga inicial ya que el usuario no necesita esperar a que el JS sea descargado para ver la interfaz inicial, y React puede reutilizar el HTML renderizado en el servidor así que no necesita generarlo en el lado del cliente.

Necesitas hacer el renderizado en el servidor si te das cuentas que renderizado inicial es demasiado lento y además quieres mejorar tu ranking en buscadores (Search Engine Ranking). Aunque, es cierto que Google ahora indexa el contenido renderizado en el cliente, desde Enero de 2016 cada vez que se ha medido se ha visto que afecta negativamente al ranking, seguramente por la penalización de rendimiento del renderizado en el cliente.

El renderizado en el servidor todavía requiere de muchas herramientas para hacerlo bien. Ya que React soporta transparentemente que los componentes sean escritos sin el renderizado en el servidor, puedes construir una aplicación primero y preocuparte del renderizado en el servidor después. **No necesitarás re-escribir todos tus componentes para que funcione.**

## Aprendiendo Immutable.js

[Immutable.js](https://facebook.github.io/immutable-js/) aporta una colección de estructuras de datos que ayudan a resolver ciertos problemas de rendimiento cuando se construyen aplicaciones con React. Es una gran librería, y seguramente la usarás más adelante en muchas de tus aplicaciones, pero es completamente innecesaria hasta que empieces a apreciar problemas de rendimiento.

## Aprendiendo Relay, Falcor, etc.

Estas son tecnologías que te ayudan a reducir el número de peticiones AJAX. Son todavía innovadoras, así que si no tienes problemas con demasiadas peticiones AJAX, no necesitas Relay o Falcor.

----------
<a name="f1">1</a>: Tecnologías beeding-edge https://es.wikipedia.org/wiki/Bleeding_edge_technology

