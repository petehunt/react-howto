# react-howto

Se React é novo para você (ou frontend no geral) você pode achar o ambiente um pouco confuso. Aqui está algumas razões para isso.

* React vem sendo historicamente alvo de recém chegados e especialistas.
* O Facebook deixa open-source somente o que realmente utiliza, então não foca em desenvolver ferramentas para projetos menores que o Facebook em si.
* Há muitos marketing mascarados ruins como guias do React.

Ao decorrer deste documento, Eu irei assumir que você já criou uma página web com HTML, CSS e JavaScript.

## Por que você deveria me ouvir?

Há toneladas de conselhos conflitantes sobre o React por aí. Por que me ouvir?

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

Adicionalmente, têm alguns tópicos que são frequentemente mencionados na comunidade do React que são "Era sangrenta". Os tópicos abaixo são interessantes, mas eles são difíceis de entender, e são, de longe, menos populares que os tópicos acima e **não são requeridos para a maioria dos apps**.
* [Inline styles](#learning-inline-styles)
* [Server rendering](#learning-server-rendering)
* [Immutable.js](#learning-immutablejs)
* [Relay, Falcor, etc](#learning-relay-falcor-etc)

## Aprendendo React em sí

É um equívoco comum você precisar desperdiçar muito tempo na configuração de ferramentas para começar a aprender React. Na documentação oficial você encontrará um [copiar-colar template HTML](https://facebook.github.io/react/docs/getting-started.html#quick-start-without-npm) que você pode salvar em um arquivo `.html` e começar logo em seguida. **Nenhuma configuração de ferramenta é necessária para esse passo, e não comece a estudar mais ferramentas até você estar confortável com o básico do React.**

Eu ainda acho que a forma mais fácil para aprender React é o [tutorial oficial](https://facebook.github.io/react/docs/tutorial.html).


## Aprendendo `npm`

`npm` é o gerenciador de pacote Node.js(**N**ode.js **P**ackage **M**anager) e é a forma mais popular que engenheiros, designers e desenvolvedores front-end compartilhar código JavaScript. Isso inclui um sistema modular chamado `CommonJS` e permite você instalar ferramentas na linha de comando escritas em JavaScript. Leia [esse post](http://0fps.net/2013/01/22/commonjs-why-and-how/) para entender por que `CommonJS` é necessário para navegadores (browsers), ou o [CommonJS Spec Wiki](http://wiki.commonjs.org/wiki/Introduction) para mais informações da API do `CommonJS`.

A Maioria dos componentes reutilizáveis, bibliotecas e ferramentas do ecossistema do React estão dispiníveis como módulos `CommonJS` e são instalados com `npm`.

## Aprendendo JavaScript bundlers (empacotadores)

Para um bom número de boas razões técnicas, módulos `CommonJS` (ex: tudo no `npm`) não pode ser usado nativamente no browser. Você precisa de um "empacotador" JavaScript para "empacotar" esses módulos dentro de arquivos `.js` que você pode incluir na sua página web com a tag `<script>`

Exemplos de empacotadores JavaScript são `webpack` e `browserify`. Ambos são boas escolhas, mas eu prefiro `webpack` pois possue funcionalidades que fazem o desenvolvimento muito mais fácil. Mesmo a documentação sendo confusa, eu tenho um [plug-and-play template para começar](https://github.com/petehunt/react-webpack-template) e eu escrevi um guia webpack [como-fazer](https://github.com/petehunt/webpack-howto) para casos mais complexos.

Uma coisa para manter em mente: `CommonJS`usa a função `require()` para importar módulos, então muitas pessoas ficam confusas e pensam que tem algo haver com o projeto chamado `require.js`. Para um bom número de razões tecnicas, eu gostaria de sugerir que você evitasse `require.js`. Ele também não é muito popular no ecossistema do React.


## Aprendendo ES6

Além do JSX (o qual você aprendeu no tutorial do React), você pode achar alguns exemplos engraçados no React. Isso é conhecido como ES6, que é a última versão do JavaScript que talvez você ainda não tenha aprendido. Já que é tão novo, não é suportado nos browsers ainda, mas o seu empacotador (bundler) pode traduzir pra você com a configuração adequada.

Se você quer apenas fazer as coisas acontecerem no React, **você pode pular o aprendizado de ES6**, ou tentar entender no caminho.

Talvez você tenha ouvido que classes ES6 são preferidas para criar componentes React. Isso não é verdade. A maioria das pessoas (incluindo o Facebook) estão usando `React.createClass()`.

## Aprendendo routing (fazer rotas)

“Single-page applications” (Aplicações de uma única página) são os objetivos nos dias de hoje. São páginas web que carregam apenas uma vez, e quando o usuário clica em um link ou em um botão, o JavaScript compila a página e atualiza a barra de endereço, mas a página web não é atualizada. O gerenciamento da barra de endereço é feito por algo chamado **router** (roteador).

O roteador mais popular no ecosistema do React é [react-router](https://github.com/rackt/react-router). Se você está construindo uma single-page application, utilize isso a não ser que você tenha uma boa razão para não fazer.

**Não utilize o roteador se você não estiver construindo uma single-page application**. A maioria dos projetos começam com componentes pequenos dentro de uma grande aplicação de qualquer forma.

## Aprendendo Flux

Você provavelmente já ouviu falar sobre "head" do Flux. Tem uma *tonelada* de mal entendidos sobre Flux por aí.

Muita gente começa a construir um app e gostaria de definir seu próprio modelo de dados, e pensam que precisam usar Flux para fazer isso. **Assim é uma forma errada de adotar o Flux. O Flux só deveria ser adicionado quando muitos componentes já foram cosntruídos.**

Os componentes React são arranjados em hierarquia. A maioria das vezes, seu modelo de dados também segue uma hierarquia. Nessa situação o Flux te adiciona muita coisa. As vezes não há hierarquia no seu modelo de dados. Quando seus componentes React começam a receber `props` (propriedades) que parecem estranhas, ou você possue um pequeno número de componentes começando a ficar muito complexo, talvez você queira dar uma olhada no Flux.

**Você saberá quando precisará do Flux. Se você não está certo se precisa disso, você realmente não precisa disso.**

Se você decidiu usar Flux, a biblioteca mais popular e melhor documentada é [Redux](http://redux.js.org/). Há *muitas* outras alternativas por aí, e você ficará tentado a avalizar a maioria deles, mas meu conselho é para você ficar apenas no mais popular.

## Aprendendo inline styles 

Antes do React, muita gente reutiliza estilos de CSS com complicados processadores de style sheets (folhas de estilo) como SASS. Como React faz escritas de componentes reutilizáveis facilmente, sua folha de estilo pode ser menos complicada. A maioria da comunidade (me incluindo) estão esperimentando se livrar de folhas de estilos altogether (tudo em uma só).

Essa é uma idéia bastante louca por bom número de razões. Faz com que media queries fiquem mais difíceis, e é possível que tenha uma limitação ao usar essa técnica. **Quando começando com React, apenas coloque estilho nas coisas como você geralmente faria.**

Uma vez que você já tem idéia de como React funciona, você pode olhar por técnicas alternativas. Uma bem popular é  [BEM](https://en.bem.info/). Eu recomendo você descartar seu pré-processador de CSS, já que React disponibiliza uma forma mais poderosa de reusar styles (reutilizando componentes), e o seu empacotador JavaScript pode gerar folhas de estilo mais eficientes pra você (Eu te dou [um exemplo sobre isso no OSCON](https://www.youtube.com/watch?v=VkTCL6Nqm6Y)). Dito isso, React, como toda biblioteca JavaScript, funcionará bem com um pré-processador CSS.

Alternativamente, você também pode usar [Módulos CSS](http://glenmaddern.com/articles/css-modules), mais especificamente [react-css-modules](https://github.com/gajus/react-css-modules). Com módulos CSS você ainda escreverá CSS (ou SASS/LESS/Stylus), mas você pode gereciar e fazer seus arquivos CSS como você faria inline styles no React. E você não precisará se preocupar em gerenciar o nom de de classes usando metodologias como BEM, pois isso será cuidado sob os panos quando utilizado o sistema de módulos.


## Aprendendo server rendering (renderização de servidor)

Renderização de servidor é geralmente chamado de "universal" ou "isomorphic" JS. Isso quer dizer que você pode pegar seus componentes React e renderizá-los em um HTML estático no servidor. Isso melhora a performance inicial porque o usuário não precisa esperar pelo JS para fazer o download para visualizar a interface inicial, e o React pode reutilizar o HTML renderizado no servidor, logo não é necessário gerar isso no lado do cliente. 

Você apenas precisa renderizar no servidor se você perceber que a renderização inicial está muito lenta ou se você voque quer melhorar o sistema de ranking de busca. Enquando for verdade que o Google agora indexa conteúdo renderizado no cliente, a partir de janeiro de 2016 todo tempo é mensurado e o ranking sofre um efeito negativamente, potencialemnte por causa da penalidade na renderização do lado do cliente.

Renderização no lado do servidor ainda requer uma grande quantidade de ferramentas para fazer corretamente. Já que transparentemente suporta componentes React escritos sem foco na renderização no lado do servidor, você deveria primeiramente construir seu app e se preocupar com a renderização do lado do servidor mais tarde. Você não precisa reescrever todos os seus componentes para suportar isso.

## Aprendendo Immutable.js

[Immutable.js](https://facebook.github.io/immutable-js/) disponibiliza uma série de estrutura de dados que podem ajudar a resolver certos problemas de performance na construção de apps em React. É uma excelente biblioteca, e você provavelmente irá usar muito no avanço dos seus apps, mas é completamente desnecessário até que você tenha uma apreciação em implementações performáticas.

## Aprendendo Relay, Falcor etc

São tecnologias que ajudam você a reduzir o número de requisições AJAX. São tecnologias de ponta, então se você não tiver problemas com muitas requisições AJAX, não há necessidade de Relay ou Falcor.
