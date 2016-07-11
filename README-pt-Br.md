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

Exemplos de empacotadores JavaScript são `webpack` e `browserify`. Ambos são boas escolhar, mas eu prefiro `webpack` pois possue funcionalidades que fazem o desenvolvimento muito mais fácil. Mesmo a documentação sendo confusa, eu tenho um [plug-and-play template para começar](https://github.com/petehunt/react-webpack-template) e eu escrevi um guia webpack [como-fazer](https://github.com/petehunt/webpack-howto) para casos mais complexos.

Uma coisa para manter em mente: `CommonJS`usa a função `require()` para importar módulos, então muitas pessoas ficam confusas e pensam que tem algo haver com o projeto chamado `require.js`. Para um número de razões tecnicas, eu gostaria de sugerir que você evitasse `require.js`. Ele também não é muito popular no ecossistema do React.


## Aprendendo ES6

Além do JSX (o qual você aprendeu no tutorial do React), você pode achar alguns exemplos engraçados no React. Isso é conhecido como ES6, que é a última versão do JavaScript que talvez você ainda não tenha aprendido. Já que é tão novo, não é suportado nos browsers ainda, mas o seu empacotador (bundler) pode traduzir pra você com a configuração adequada.

Se você quer apenas fazer as coisas acontecerem no React, **você pode pular o aprendizado de ES6**, ou tentar entender no caminho.

Talvez você tenha ouvido que classes ES6 são preferidas para criar componentes React. Isso não é verdade. A maioria das pessoas (incluindo o Facebook) estão usando `React.createClass()`.

## Aprendendo routing (fazer rotas)

“Single-page applications” (Aplicações de uma única página) são os objetivos nos dias de hoje. São páginas web que carregam apenas uma vez, e quando o usuário clica em um link ou em um botão, O JavaScript compilando na página atualiza a barra de endereço, mas a página web não é atualizada. O gerenciamento da barra de endereço é feito por algo chamado **router** (roteador).

O roteador mais popular no ecosistema do React é [react-router](https://github.com/rackt/react-router). Se você está construindo uma single-page application, utilize isso a não ser que você tenha uma boa razão para não fazer.

**Não utilize o roteador se você não estiver construindo uma single-page application**. A maioria dos projetos começam com componentes pequenos dentro de uma grande aplicação de qualquer forma.

## Aprendendo Flux

Você provavelmente já ouviu falar sobre "head" do Flux. Tem uma *tonelada* de mal entendidos sobre Flux por aí.

Muita gente começa a cosntruir um app e gostaria de definir seu próprio modelo de dados, e pensam que precisam usar Flux para fazer isso. **Assim é uma forma errada de adotar o Flux. O Flux só deveria ser adicionado quando muitos componentes já foram cosntruídos.**

Os componentes React são arranjados em hierarquia. A maioria das vezes, seu modelo de dados também segue uma hierarquia. Nessa situação o Flux te adiciona muita coisa. As vezes não há hierarquia no seu modelo de dados. Quando seus componentes React começam a receber `props` (propriedades) que parecem estranhos, ou você possue um pequeno número de componentes começando a ficar muito complexo, talvez você queira dar uma olhada no Flux.

**Você saberá quando precisará do Flux. Se você não está certo se precis disso, você realmente não precisa disso.**

Se você decidiu usar Flux, a biblioteca mais popular e melhor documentada é [Redux](http://redux.js.org/). Há *muitas* outras alternativas por aí, e você ficará tentado para avalizar a maioria deles, mas meu conselho é para você ficar apenas no mais popular.

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

[Immutable.js](https://facebook.github.io/immutable-js/) disponibiliza uma série de estrutura de dados que podem ajudar a resolver certos problemas de performance na construção de apps em React. É uma excelente biblioteca, e você provavelmente irá usar muito no avanço dos seus apps, mas é completamente desnecessário até que você tenha uma apreciação em implementações performáticas.

## Aprendendo Relay, Falcor etc

São tecnologias que ajudam você a reduzir o número de requisições AJAX. São tecnologias de ponta, então se você não tiver problemas com muitas requisições AJAX, não há necessidade de Relay ou Falcor.
