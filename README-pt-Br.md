# react-howto

Se React é novo para você (ou frontend em geral) você pode achar o ambiente um pouco confuso. Aqui estão algumas razões para isso.

* React vem sendo historicamente procurado por recém chegados e especialistas.
* O Facebook deixa open-source somente o que realmente utiliza, então ele não foca em desenvolver ferramentas para projetos menores que o Facebook em si.
* Há muito marketing ruim disfarçado de guia de React

Ao decorrer deste documento, irei assumir que você já criou uma página web com HTML, CSS e JavaScript.

## Por que você deveria me ouvir?

Há toneladas de conselhos conflitantes sobre o React por aí. Por que me ouvir?

Eu fui um dos membros do time original do Facebook que construiu e disponibilizou o React como open-source. Eu não estou mais no Facebook e agora estou em uma pequena startup, logo eu tenho uma perspectiva diferente do Facebook.

## Como lidar com o ecossistema React?

Todo software é construido em uma stack de tecnologias, e você precisa entender o suficiente dessa stack para construir seu app. A razão que o ecossistema de ferramentas do React parece esmagadora é porque sempre é explicada na ordem errada.

Você deveria aprender, nessa ordem, **sem pular etapas ou estudar ao mesmo tempo**: 

* [React em sí](#learning-react-itself)
* [`npm`](#learning-npm)
* [JavaScript “bundlers”](#learning-javascript-bundlers)
* [ES6](#learning-es6)
* [Routing](#learning-routing)
* [Flux](#learning-flux)

**Você não precisa aprender tudo isso para ser produtivo com React**
Apenas vá para o próximo passo se você tiver algum problema que precisa ser resolvido.

Adicionalmente, têm alguns tópicos que são frequentemente mencionados na comunidade do React que são muitas vezes "supérfluos". Os tópicos abaixo são interessantes, mas eles são difíceis de entender, e são, de longe, menos populares que os tópicos acima e **não são necessários para a maioria das aplicações**.
* [Inline styles](#learning-inline-styles)
* [Server rendering](#learning-server-rendering)
* [Immutable.js](#learning-immutablejs)
* [Relay, Falcor, etc](#learning-relay-falcor-etc)

## Aprendendo React em sí

É um equívoco comum você precisar desperdiçar muito tempo na configuração de ferramentas para começar a aprender React. Na documentação oficial você encontrará um [exemplo de template HTML](https://facebook.github.io/react/docs/getting-started.html#quick-start-without-npm) que você pode salvar em um arquivo `.html` e começar logo em seguida. **Nenhuma configuração de ferramenta é necessária para esse passo, e não comece a estudar mais ferramentas até você estar confortável com o básico do React.**

Eu ainda acho que a forma mais fácil para aprender React é o [tutorial oficial](https://facebook.github.io/react/docs/tutorial.html).


## Aprendendo `npm`

`npm` é o gerenciador de pacote Node.js(**N**ode.js **P**ackage **M**anager) e é a forma mais popular que engenheiros, designers e desenvolvedores front-end compartilhar código JavaScript. Isso inclui um sistema modular chamado `CommonJS` e permite você instalar ferramentas na linha de comando escritas em JavaScript. Leia [esse post](http://0fps.net/2013/01/22/commonjs-why-and-how/) para entender por que `CommonJS` é necessário para navegadores (browsers), ou o [CommonJS Spec Wiki](http://wiki.commonjs.org/wiki/Introduction) para mais informações da API do `CommonJS`.

A maioria dos componentes reutilizáveis, bibliotecas e ferramentas do ecossistema do React estão disponíveis como módulos `CommonJS` e são instalados com o `npm`.

## Aprendendo JavaScript bundlers (empacotadores)

Por uma série de boas razões técnicas, módulos `CommonJS` (ex: tudo do `npm`) não pode ser usado nativamente no navegador. Você precisa de um "empacotador" JavaScript para "empacotar" esses módulos dentro de arquivos `.js` que você pode incluir na sua página web com a tag `<script>`

Exemplos de empacotadores JavaScript são `webpack` e `browserify`. Ambos são boas escolhas, mas eu prefiro `webpack`, pois possue funcionalidades que fazem o desenvolvimento muito mais fácil. Mesmo a documentação sendo confusa, eu tenho um [template para começar](https://github.com/petehunt/react-webpack-template) e também escrevi um [guia webpack](https://github.com/petehunt/webpack-howto) para casos mais complexos.

Uma coisa para se manter em mente: `CommonJS` usa a função `require()` para importar módulos, então muitas pessoas ficam confusas e pensam que tem algo haver com o projeto chamado `require.js`. Por uma série de boas razões técnicas, eu gostaria de sugerir que você evitasse `require.js`. Ele também não é muito popular no ecossistema React.


## Aprendendo ES6

Além do JSX (o qual você aprendeu no tutorial do React), você pode achar alguns exemplos engraçados no React. Isso é conhecido como ES6, que é a última versão do JavaScript que talvez você ainda não tenha aprendido. Já que é tão novo, não é suportado nos browsers ainda, mas o seu empacotador (bundler) pode traduzir pra você com a configuração adequada.

Se você apenas quiser fazer as coisas acontecerem em React, **você pode pular o aprendizado do ES6**, ou tentar seguir por esse caminho.

Talvez você tenha ouvido que classes ES6 melhores para criar componentes React. Isso não é verdade. A maioria das pessoas (incluindo o Facebook) estão usando `React.createClass()`.

## Aprendendo routing (fazer rotas)

“Single-page applications”, ou SPA (Aplicações de uma única página) são os comuns nos dias de hoje. São páginas web que carregam apenas uma vez, e quando o usuário clica em um link ou em um botão, o JavaScript compila a página e atualizando a barra de endereço, mas a página web não é recarregada. O gerenciamento da barra de endereço é feito por algo chamado **router**.

O router mais popular no ecosistema do React é [react-router](https://github.com/rackt/react-router). Se você está construindo uma single-page application, esse a não ser que você tenha uma boa razão para não fazer.

**Não utilize o router se você não estiver construindo uma single-page application**. A maioria dos projetos começam com componentes pequenos dentro de uma grande aplicação.

## Aprendendo Flux

Você provavelmente já ouviu falar sobre o Flux. Existe uma *tonelada* de informações erradas sobre Flux por aí.

Muita gente começa a construir um app e gostaria de definir seu próprio modelo de dados. Pensam que precisam usar Flux para fazer isso. **Essa é uma forma errada de adotar o Flux. O Flux só deveria ser adicionado quando muitos componentes já foram construídos.**

Os componentes React são organizados em hierarquia. Na maioria das vezes, seu modelo de dados também segue uma hierarquia. Nessa situação o Flux não te ajuda muito. As vezes não há hierarquia no seu modelo de dados. Quando seus componentes React começam a receber `props` (propriedades) que parecem estranhas, ou você possue um pequeno número de componentes começando a ficar muito complexo, talvez você queira dar uma olhada no Flux.

**Você saberá quando precisará do Flux. Se você não tem certeza que precisa, realmente não precisa.**

Se decidiu usar Flux, a biblioteca mais popular e melhor documentada é o [Redux](http://redux.js.org/). Há *muitas* outras alternativas por aí, e você ficará tentado a avalizar a maioria delas, meu conselho é ficar apenas na mais popular.

## Aprendendo inline styles

Antes do React, muita gente reutiliza estilos de CSS usando pré-processadores como SASS. React torna a reuitilização de componentes de forma mais simples, seu CSS será menos complicado. A maioria da comunidade (me incluindo) estão experimentando se livrar do CSS totalmente.

Essa é uma idéia bastante louca por bom número de razões. Faz com que media queries fiquem mais difíceis, e é possível que tenha uma limitação ao utilizar essa técnica. **Ao iniciar com React, apenas estilize as coisas como você geralmente faria.**

Uma vez que você já tem idéia de como React funciona, pode procurar por técnicas alternativas. Uma bem popular é o [BEM](https://en.bem.info/). Eu recomendo você descartar seu pré-processador de CSS, já que React disponibiliza uma forma mais poderosa de reutilizar CSS (reutilizando componentes), e o seu empacotador JavaScript pode gerar CSS mais eficientes pra você (te dou um [exemplo sobre isso no OSCON](https://www.youtube.com/watch?v=VkTCL6Nqm6Y)). Dito isso, React, como toda biblioteca JavaScript, funcionará bem com um pré-processador de CSS.

Alternativamente, você também pode usar [módulos CSS](http://glenmaddern.com/articles/css-modules), especialmente [react-css-modules](https://github.com/gajus/react-css-modules). Com módulos CSS você ainda escreverá CSS (ou SASS/LESS/Stylus), mas você pode gereciar e criar seus arquivos CSS como você faria inline styles no React. Também não precisará se preocupar em gerenciar nome de classes com metodologias como BEM, pois isso será feito automaticamente pelo sistema de módulos.


## Aprendendo server rendering (renderização de servidor)

Renderização no servidor é geralmente chamada de JavaScript "universal" ou "isomórfico". Quer dizer que você pode pegar seus componentes React e renderizá-los em um HTML estático no servidor. Melhorando a performance inicial, pois o usuário não precisa esperar pelo JS para fazer o download e visualizar a interface inicial. O React reutilizará o HTML renderizado no servidor, logo não é necessário gerar no lado do cliente.

Você só precisa renderizar no servidor achar que a renderização inicial está muito lenta ou se você quiser melhorar o SEO (otimização para motores de busca). Embora seja verdade que o Google agora indexa conteúdo processado no cliente, a partir de janeiro de 2016, cada vez que for medido o SEO será afetado negativamente a posição da página, devido à penalidade de desempenho da renderização do lado do cliente.

Renderização no lado do servidor ainda requer uma grande quantidade de ferramentas para se fazer corretamente. Já que é evidente que componentes React são escritos sem foco na renderização no servidor. Primeiramente construa seu app e depois se preocuope com a renderização no servidor. Você não precisa reescrever todos os seus componentes para suportar isso.

## Aprendendo Immutable.js

[Immutable.js](https://facebook.github.io/immutable-js/) disponibiliza uma série de estruturas de dados que podem ajudar a resolver certos problemas de performance. É uma excelente biblioteca, e você provavelmente irá usar muito seus apps mais avançados, mas é completamente desnecessário até que você tenha necessidade de uma aplicação performática.

## Aprendendo Relay, Falcor etc

São tecnologias que ajudam você a reduzir o número de requisições AJAX. São tecnologias avançadas e se não tiver problemas com muitas requisições, não há necessidade de Relay ou Falcor.