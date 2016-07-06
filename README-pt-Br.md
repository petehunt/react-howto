# react-howto

Se React é novo para você (ou frontend no geral) você pode achar o ambiente um pouco confuso. Aqui está algumas razões para isso.

* React vem sendo historicamente alvo de recém chegados e especialistas.
* O Facebook deixa open-source somente o que realmente utiliza, então não foca em desenvolver ferramentas para projetos menores que o Facebook em si.
* Há muitos marketing mascarados ruins como guias do React.

Ao decorrer deste documento, Eu irei assumir que você já criou uma página web com HTML, CSS e JavaScript.

## Por que você deveria me ouvir?

Há toneladas de conselhos conflitantes sobre o React por aí; Por que me ouvir?

Eu fui um dos membros do time original do Facebook que construiu e disponibilizou o React como open-source. Eu não estou mais no Facebook e agora estou em uma pequena startup, logo eu tenho uma perspectiva diferente do Facebook.

## Como lidar com o ecossistema React?

Todo software é construido em uma stack de tecnologias, e você precisa entender o suficiente dessa stack para construir seu app. A razão que o ecossistema de ferramentas do React parece esmagadora é porque é sempre explicada na ordem errada. 

Você deveria aprender, nessa ordem, **sem pular etapas ou estudar ao mesmo tempo**: 

* [React em sí](#learning-react-itself)
* [`npm`](#learning-npm)
* [JavaScript “bundlers”](#learning-javascript-bundlers)
* [ES6](#learning-es6)
* [Routing](#learning-routing)
* [Flux](#learning-flux)

**Você não precisa aprender tudo isso para ser produtivo com React**
Apenas vá para o próximo passo se você tiver algum problema que precisa ser resolvido.

Adicionalmente, têm alguns tópicos que são frequentemente mencionados na comunidade do React que são "Era sangrenta". Os tópicos abaixo são interessantes, mas eles são difíceis de entender, são, de longe, menos populares que os tópicos acima e **não são requeridos para a maioria dos apps**.
* [Inline styles](#learning-inline-styles)
* [Server rendering](#learning-server-rendering)
* [Immutable.js](#learning-immutablejs)
* [Relay, Falcor, etc](#learning-relay-falcor-etc)

## Aprendendo React em sí

É um equívoco comum você precisar desperdiçar muito tempo na configuração de ferramentas para começar a aprender React. Na documentação oficial você encontrará um [copiar-colar template HTML](https://facebook.github.io/react/docs/getting-started.html#quick-start-without-npm) que você pode salvar em um arquivo `.html` e começar logo em seguida. **Nenhuma configuração de ferramenta é necessária para esse passo, e não comece a estudar mais ferramentas até você estar confortável com o básico do React.**

Eu ainda acho que a forma mais fácil para aprender React é o [tutorial oficial](https://facebook.github.io/react/docs/tutorial.html).


## Aprendendo `npm`

`npm` é o gerenciador de pacote Node.js(**N**ode.js **P**ackage **M**anager) e é a forma mais popular que engenheiros, designers e desenvolvedores front-end compartilhar código JavaScript. Isso inclui um sistema modular chamado `CommonJS` e permite você instalar ferramentas em linha de comando escritas em JavaScript. Leia [esse post](http://0fps.net/2013/01/22/commonjs-why-and-how/) para entender por que `CommonJS` é necessário para navegadores (browsers), ou o [CommonJS Spec Wiki](http://wiki.commonjs.org/wiki/Introduction) para mais informações da API do `CommonJS`.

A Maioria dos componentes reutilizáveis, bibliotecas e ferramentas do ecossistema do React estão dispiníveis como módulos `CommonJS` e são instalados com `npm`.

## Aprendendo JavaScript bundlers (empacotadores)

Para um número de boas razões técnicas, módulos `CommonJS` (ex: tudo no `npm`) não pode ser usado nativamente no browser. Você precisa de um "empacotador" JavaScript para "empacotar" esses módulos dentro de arquivos `.js` que você pode incluir na sua página web com a tag `<script>`


Examples of JavaScript bundlers include `webpack` and `browserify`. Both are good choices, but I prefer `webpack` since it has a lot of features that make development of large apps easier. Since its documentation can be confusing, I have a [plug-and-play template for getting started](https://github.com/petehunt/react-webpack-template) and I wrote a [how-to guide for webpack](https://github.com/petehunt/webpack-howto) for more complex use cases.

One thing to keep in mind: `CommonJS` uses the `require()` function to import modules, so a lot of people get confused and think that it has something to do with a project called `require.js`. For a number of technical reasons, I would suggest that you avoid `require.js`. It’s also not very popular in the React ecosystem.

## Aprendendo ES6

Outside of JSX (which you learned in the React tutorial), you may see some funny syntax in React examples. This is called ES6, and it’s the latest version of JavaScript so you may not have learned it yet. Since it’s so new, it’s not supported in browsers yet, but your bundler can translate it for you with the proper configuration.

If you just want to get things done with React, **you can skip learning ES6**, or try to pick it up along the way.

You may see some talk about ES6 classes being the preferred way to create React components. This is untrue. Most people (including Facebook) are using `React.createClass()`.

## Aprendendo routing (fazer rotas)

“Single-page applications” are all the rage these days. These are web pages that load once, and when the user clicks on a link or a button, JavaScript running on the page updates the address bar, but the web page is not refreshed. Management of the address bar is done by something called a **router**.

The most popular router in the React ecosystem is [react-router](https://github.com/rackt/react-router). If you’re building a single-page application, use it unless you have a good reason not to.

**Don’t use a router if you aren’t building a single-page application**. Most projects start out as smaller components inside of a larger application anyway.

## Aprendendo Flux

You’ve probably heard of Flux. There’s a *ton* of misinformation about Flux out there.

A lot of people sit down to build an app and want to define their data model, and they think they need to use Flux to do it. **This is the wrong way to adopt Flux. Flux should only be added once many components have already been built.**

React components are arranged in a hierarchy. Most of the time, your data model also follows a hierarchy. In these situations Flux doesn’t buy you much. Sometimes, however, your data model is not hierarchical. When your React components start to receive `props` that feel extraneous, or you have a small number of components starting to get very complex, then you might want to look into Flux.

**You’ll know when you need Flux. If you aren’t sure if you need it, you don’t need it.**

If you have decided to use Flux, the most popular and well-documented Flux library is [Redux](http://redux.js.org/). There are *a lot* of alternatives out there, and you’ll be tempted to evaluate lots of them, but my advice is to just stick with the most popular one.

## Aprendendo inline styles

Pre-React, a lot of people reused CSS styles with complicated style sheets built by preprocessors like SASS. Since React makes writing reusable components easy, your stylesheets can be less complicated. Many in the community (including myself) are experimenting with getting rid of stylesheets altogether.

This is a fairly crazy idea for a number of reasons. It makes media queries more difficult, and it's possible that there are  performance limitations using this technique. **When starting out with React, just style things the way you normally would.**

Once you've got a feel for how React works, you can look at alternate techniques. One popular one is [BEM](https://en.bem.info/). I recommend phasing out your CSS preprocessor, since React gives you a more powerful way to reuse styles (by reusing components) and your JavaScript bundler can generate more efficient stylesheets for you (I gave [a talk about this at OSCON](https://www.youtube.com/watch?v=VkTCL6Nqm6Y)). With that said, React, like any other JavaScript library, will work just fine with a CSS preprocessor.

Alternatively, you can also use [CSS Modules](http://glenmaddern.com/articles/css-modules), more specifically [react-css-modules](https://github.com/gajus/react-css-modules). With CSS Modules you'll still write CSS (or SASS/LESS/Stylus), but you can manage and compose your CSS files like you'd do with inline styles in React. And you don't need to worry about managing your class names using methodologies like BEM, as this will be handled for you under the hood by the module system.

## Aprendendo server rendering (renderização de servidor)

Server rendering is often called "universal" or "isomorphic" JS. It means that you can take your React components and render them to static HTML on the server. This improves initial startup performance because the user does not need to wait for JS to download in order to see the initial UI, and React can re-use the server-rendered HTML so it doesn't need to generate it client-side.

You need server rendering if you notice that your initial render is too slow or if you want to improve your search engine ranking. While it's true that Google now indexes client-rendered content, as of January 2016 every time it's been measured it's been shown to negatively affect ranking, potentially because of the performance penalty of client-side rendering.

Server rendering still requires a lot of tooling to get right. Since it transparently supports React components written without server rendering in mind, you should build your app first and worry about server rendering later. You won't need to rewrite all of your components to support it.

## Aprendendo Immutable.js

[Immutable.js](https://facebook.github.io/immutable-js/) provides a set of data structures that can help to solve certain performance issues when building React apps. It's a great library, and you'll probably use it a lot in your apps moving forward, but it's completely unnecessary until you have an appreciation of the performance implications. 

## Aprendendo Relay, Falcor etc

These are technologies that help you reduce the number of AJAX requests. They’re still very cutting-edge, so if you don’t have a problem with too many AJAX requests, you don’t need Relay or Falcor.