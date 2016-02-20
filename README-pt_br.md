# react-howto

Se você é novo no React (ou no frontend em geral) você pode achar o ecossistema confuso. Existem algumas razões para isso.

* React tem sido historicamente orientado para iniciantes e especialistas
* Facebook apenas abre o código fonte daquilo que ele realmente utiliza, então ele não se concentra em ferramentas para projetos menores que o Facebook.
* Há muito marketing ruim que aparecem como guias para o React.

Ao longo deste documento, eu irei assumir que você já construiu alguma página Web com HTML, CSS e JavaScript.

## Por que você deve me escutar?

Há uma tonelada de conselhos conflitantes sobre o React por aí; por que me ouvir?

Eu fui um dos membros originais da equipe do Facebook que construiu e abriu o código fonte do React. Eu não estou mais no Facebook e sim em uma pequena startup, então eu também tenho uma perspectiva de fora do Facebook.

## Como lidar com o ecossistema do React

Todo software é construído sobre uma pilha de tecnologias, e você precisa entender o suficiente dessa pilha para construir sua aplicação. A razão pela qual o ecossistema de ferramentas do React parece te esmagar é porque ele é sempre explicado na ordem errada.

Você deve aprender, nessa ordem, **sem pular para o próximo ou aprender simultaneamente**:

* [React em si](#learning-react-itself)
* [`npm`](#learning-npm)
* [JavaScript “bundlers”](#learning-javascript-bundlers)
* [ES6](#learning-es6)
* [Rotas](#learning-routing)
* [Flux](#learning-flux)

**Você não precisa aprender todos para ser produtivo com o React.** Somente pule para o próximo passo caso você esteja com algum problema que necessite ser resolvido.

Além disso, existem alguns tópicos mencionados frequentemente na comunidade do React que são "pioneiros". Os tópicos a seguir são interessantes, mas são difíceis de entender, são muito menos populares do que os tópicos acima e **não são necessários para a maioria dos aplicativos**.
* [Estilos Inline](#learning-inline-styles)
* [Renderizando no servidor](#learning-server-rendering)
* [Immutable.js](#learning-immutablejs)
* [Relay, Falcor, etc](#learning-relay-falcor-etc)

## Aprendendo o React em si

É um equívoco comum que diz que você precisa perder bastante tempo configurando as ferramentas para começar a aprender React. Na documentação oficial você encontrará [um template de copiar/colar](https://facebook.github.io/react/docs/getting-started.html#quick-start-without-npm) que você pode salvar em um arquivo `.html` e começar imediatamente. **Nesse momento nenhuma configuração é necessária, e você não precisa começar a estudar configurações adicionais até que você esteja confortável com o básico do React.**

Eu ainda acho que o jeito mais fácil de aprender React é através do [tutorial oficial](https://facebook.github.io/react/docs/tutorial.html).

## Aprendendo `npm`

`npm` é o gerenciador de pacotes do Node.JS e é a maneira mais popular para engenheiros front-end e designers compartilharem seus códigos JavaScript. Ele inclui um módulo chamado `CommonJS` e permite que você instale ferramentas escritas em JavaScript através da linha de comando. Leia [esse post](http://0fps.net/2013/01/22/commonjs-why-and-how/) para uma idéia de como o `CommonJS` é necessário para os navegadores, ou o [CommonJS Spec Wiki](http://wiki.commonjs.org/wiki/Introduction) para mais sobre o API do `CommonJS`.

A maioria dos componentes reutilizáveis, bibliotecas e ferramentas no ecossistema do React estão disponíveis como `módulos CommonJS` e são instalados com o `npm`.

## Aprendendo os JavaScript bundlers

Por algum bom número de razões técnicas os módulos `CommonJS` (ex. tudo no `npm`) não podem ser usados nativamente no navegador. Você precisa de um “bundler” JavaScript para “converter” esses módulos em arquivos `.js` que possam ser incluídos na sua página com uma tag `<script>`.

Exemplos de bundlers JavaScript incluem `webpack` e `browserify`. Ambos são boas escolhas, mas eu prefiro o `webpack` uma vez que ele possui diversas ferramentas que fazem o desenvolvimento de aplicativos maiores mais fáceis. Visto que sua documentação pode ser confusa, eu criei [um template plug-and-play para começar](https://github.com/petehunt/react-webpack-template) e escrevi um [guia 'how-to' para o webpack](https://github.com/petehunt/webpack-howto) para casos de uso mais complexos.

Tenha em mente uma coisa: `CommonJS` usa a função `require()` para importar os módulos, então, várias pessoas ficam confusas e acham que isso tem algo a ver com um projeto chamado `require.js`. Por um número de razões técnicas, eu sugiro que você evite o `require.js`. E também não é muito popular no ecossistema do React.

## Aprendendo ES6

Fora do JSX (que você aprendendo no tutorial do React), você deve ter visto algumas sintaxes engraçadas nos exemplos do React. Isso é chamado de ES6, e é a última versão do JavaScript então talvez você não tenha aprendido ainda. Já que é tão novo, não é suportado nos navegadores ainda, mas seu bundler pode traduzi-lo com as configurações corretas.

Se você apenas quer aprender React, **você pode pular a parte do ES6**, ou ir aprendendo no caminho.

Você pode ver algumas conversas sobre as classes ES6 serem o caminho preferido para criar componentes para o React. Não é verdade. A maioria das pessoas (incluindo Facebook) estão usando `React.createClass()`.

## Aprendendo as rotas

“Single-page applications” ou aplicativos de uma só página estão na moda nos dias de hoje. São paginas que carregam uma vez, e quando o usuário clica num link ou botão, o JavaScript que está sendo executado na página atualiza a barra de endereço, mas a página não é atualizada. A administração da barra de endereço é feita por algo chamado de **roteador**.

O roteador mais popular no ecossistema React é o [react-router](https://github.com/rackt/react-router). Se você está construindo uma SPA (aplicativo de uma página), use-o, a não ser que você tenha um bom motivo para não usar.

**Não use o roteador se você não está criando aplicativos de uma página**. A maioria dos projetos começa como pequenos componentes dentro de aplicativos maiores de qualquer maneira.

## Aprendendo Flux

Você provavelmente já ouviu falar do Flux. Há uma *tonelada* de informações erradas sobre ele por aí.

Muitas pessoas se sentam parar desenvolver aplicativos e querem definir os seus modelos de dados, e pensam que devem usar o Flux para fazê-lo. **Essa é uma maneira errada de adotar o Flux. Flux deve ser apenas adicionado quando vários componentes já tiverem sido construídos.**

Os componentes do React são alinhados hierarquicamente. A maior parte do tempo, seu modelo de dados seguem essa hierarquia. Nessas situações o Flux não acrescenta muito. Algumas vezes, no entanto, seu modelo de dados não é hierarquico. Quando seus componentes do React começarem a receber `props` que parecem estranhos, ou você tem um número pequeno de componentes começando a ficar complexos, então você deve partir para o Flux.

**Você saberá a hora de precisar do Flux. Se você não tem certeza se precisa, não precisa.**

Se você decidiu usar o Flux, a biblioteca mais popular e bem documentada é o [Redux](http://redux.js.org/). Existem *milhares* de alternativas por aí, e você ficará tentado em testar todas elas, mas meu conselho é que você fique com o mais popular.

## Aprendendo estilos inline

Antes do React, várias pessoas reusaram estilos CSS com 'style sheets' complicados construido por pre-processadores como o SASS. Já o React torna a escrita de componentes reusáveis fácil, e seus stylesheets podem ser menos complicados. Várias pessoas na comunidade (incluindo eu) estamos experimentando nos livrar de stylesheets em um único arquivo.

Concordo que isso seja uma idéia doida por um número de razões. Isso torna as requisições de mídia mais difíceis, e é possível que existam limitações de performance usando essa técnica. **Quando estivar começando com o React, estilize suas coisas do jeito que você normalmente faz.**

Assim que você sentir que sabe como o React funciona, você pode procurar por técnicas alternativas. Um popular é o [BEM](https://en.bem.info/). eu recomendo que você vá atualizando seu preprocessador de CSS gradualmente, já que o React te oferece uma maneira mais poderosa de reutilizar os estilos (por reutilizar os componentes) e seu bundler JavaScript pode gerar stylesheets mais eficientes para você (Eu [conversei sobre isso na OSCON](https://www.youtube.com/watch?v=VkTCL6Nqm6Y)). Com isso dito, React, como qualquer outra biblioteca JavaScript, irá funcionar normalmente com um preprocessador CSS.

Alternativamente, você pode usar o [Módulo CSS](http://glenmaddern.com/articles/css-modules), e mais especificamente [react-css-modules](https://github.com/gajus/react-css-modules). Com Módulos CSS você ainda irá escrever CSS (ou SASS/LESS/Stylus), mas você pode administrar e compor seus arquivos CSS files como você faz com seus estilos inline no React. E você não precisa se preocupar em administrar os nomes das classes usando metodologias como o BEM, já que isso será feito pra você por de trás dos panos pelo módulo do sistema.

## Aprendendo renderização do servidor

Renderização do servidor é muitas vezes chamado de JS "universal" ou "isomórfico". Isso significa que você pode pegar seus componentes React e renderizá-los em HTML estáticos no servidor. Isso melhora o carregamento inicial pois o usuário não necessita de esperar o JS terminar de ser baixado para visualizar a interface inicial, e o React pode reusar o HTML renderizado no servidor, então não é necessário que seja gerado no lado do cliente.

Você precisará de renderização no servidor se notar que a renderização inicial está muito lenta ou se você deseja melhorar seu ranking nos mecanismos de busca. Embora seja verdade que o Google agora indexa conteúdo renderizado no cliente, desde Janeiro de 2016, cada vez que foi mensurado, tem sido notado que afetam negativamente o ranking, potencialmente devido a penalidade de desempenho da renderização feita no lado do cliente.

Renderização no servidor ainda necessita várias configurações para funcionar corretamente. Já que ele suporta transparentemente os componentes do React escritos sem a renderização no servidor em mente, você deve desenvolver seu aplicativo primeiro e se preocupar com a renderização no servidor depois. Você não precisará reescrever todos seus componentes para suportá-lo.

## Aprendendo Immutable.js

[Immutable.js](https://facebook.github.io/immutable-js/) fornece um conjunto de ferramenta de dados que pode ajudá-lo a resolver certos problemas de desempenho quando construindo aplicativos React. É uma excelente biblioteca, e você provavelmente irá usá-lo bastante em seus aplicativos daqui pra frente, mas é completamente desnecessário até que você tenha uma apreciação por implicações de desempenho.

## Aprendendo Relay, Falcor etc

São tecnologias que te ajudam a reduzir o número de requisições AJAX. Ainda são tecnologias de ponta, então, se você não tem problema com muitas requisições AJAX, você não precisa do Relay ou Falcor.
