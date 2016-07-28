# Como usar React

Se você é novo com React (ou frontend em geral) você pode achar o ecossistema um tanto quanto confuso. Existem algumas razões para isso.

* React tem um historico de ser orientada para early-adopters e especialistas
* Facebook usa projetos de codigo aberto, que eles realmente vão utilizar, eles não se concetram em outras ferramentas para projetos menores que o proprio Facebook
* Há um monte de marketing ruim que aparece como guias para o React

Ao longo deste documento, eu vou assumir que você construiu uma página Web com HTML, CSS e JavaScript.

## Por que você deve me ouvir?

Há uma tonelada de conselhos conflitantes sobre React lá fora; porque me ouvir? 

Eu fui um dos membros originais da equipe do Facebook que construíram e tornaram React um codigo aberto. Eu já não estou mais no Facebook e estou agora em uma pequena empresa (Startup), então eu também tenho uma perspectiva de fora do Facebook.

## Como lidar com o ecossistema React

Todo o software é construído sobre varias tecnologias, e você precisa entender o suficiente de cada tecnologia para construir sua aplicação. A razão pela qual o ecossistema React asusta é porque sempre é explicado na ordem errada. 

Você deve aprender, nesta ordem, **sem pular à frente ou aprender simultaneamente**:

* [React em si](#aprendendo-react-em-si)
* [`npm`](#aprendendo-npm)
* [JavaScript "bundlers"](#aprendendo-bundlers-javascript)
* [ES6](#aprendendo-es6)
* [Routing](#aprendendo-rotas)
* [Flux](#aprendendo-flux)

**Você não precisa aprender tudo isso para ser produtivo com React**. Apenas passe para a próxima etapa se você tem um problema que precisa ser resolvido. Além disso, existem alguns tópicos que são frequentemente mencionados na comunidade React que são "bleeding edge". 
Os tópicos a seguir são interessantes, mas eles são difíceis de entender, são muito menos populares do que os tópicos acima e **não são necessários para a maioria dos aplicativos**.
* [Inline styles](#aprendendo-inline-styles)
* [Server rendering](#aprendendo-renderização-de-servidor)
* [Immutable.js](#aprendendo-immutablejs)
* [Relay, Falcor, etc](#aprendendo-relay-falcor-etc)

## Aprendendo React em si

É um equívoco muito comum, achar que você precisa perder muito tempo na criação de ferramentas para começar a aprender React. Na documentação oficial 
você encontrará uma [modelo de template HTML](https://facebook.github.io/react/docs/getting-started.html#quick-start-without-npm) 
que você pode salvar em um arquivo `.html` e começar imediatamente. **Nenhuma ferramenta é necessária para esta etapa, e não começe a aprender outra ferramenta até que você esteja confortável com o basico de React.** 

Eu ainda acho que a maneira mais fácil de aprender React é [o tutorial oficial](https://facebook.github.io/react/docs/tutorial.html).

## Aprendendo `npm`

`npm` é o gerenciador de pacotes do Node.js e é o modo mais comum que engenheiros e designers frontedn compartilham o código JavaScript. Inclui um sistema de módulo chamado `CommonJS` e lhe permite instalar as ferramentas de linha de comando escritos em JavaScript. Leia [este post](http://0fps.net/2013/01/22/commonjs-why-and-how/) para entender mais sobre por que `CommonJS` é necessário para navegadores, como o [commonjs Spec Wiki](http : //wiki.commonjs.org/wiki/Introduction) para mais informações sobre o `CommonJS` API.

A maioria dos componentes reutilizáveis, bibliotecas e ferramentas no ecossistema React estão disponíveis como `módulos CommonJS` e são instalados com `npm`.

## Aprendendo Bundlers JavaScript

Por uma série de boas razões técnicas `módulos CommonJS` (tudo isto em `npm`) não podem ser usados nativamente no navegador. Você precisa de um "bundler" JavaScript para "empacotar" estes módulos em arquivos `.js` que você pode incluir na sua página web com uma tag `<script>`. 

Exemplos de bundlers JavaScript incluem `webpack` e browserify`. Ambos são boas escolhas, mas eu prefiro `webpack` uma vez que ele tem um monte de recursos que tornam o desenvolvimento de grandes aplicações mais fáceis. Sua documentação pode ser confusa, mas eu tenho um [modelo de plug-and-play para começar](https://github.com/petehunt/react-webpack-template) e eu escrevi um [guia de como usar Webpack](https://github.com/petehunt/webpack-howto) para casos de uso mais complexos. 

Uma coisa para manter em mente: `CommonJS` usa a função` require()` para importar módulos, várias pessoas se confundem e pensam que ele tem algo a ver com um projeto chamado `require.js`. Por uma série de razões técnicas, gostaria de sugerir que você evite `require.js`. E também por não ser muito popular no ecossistema React.

## Aprendendo ES6

Fora de JSX (que você aprendeu no tutorial React), você pode ver algumas sintaxe's engraçadas nos exemplos de React. Isso é chamado de ES6, e é a última versão do JavaScript caso você não ter aprendido isso ainda. Ele é tão novo, que não é suportado em navegadores atuais ainda, mas o seu bundler pode traduzi-lo para você com a configuração adequada.

Se você só quer fazer as coisas com React, **você pode ignorar a aprendizagem ES6**, ou tentar aprender ao longo do caminho. 

Você pode ver alguma conversa sobre classes ES6, dizendo que é a forma preferida para criar componentes React. Isto não é verdade. A maioria das pessoas (incluindo Facebook) estão usando `React.createClass()`.

## Aprendendo Rotas

“Single-page applications” são a raiva de todos os dias. Elas são páginas da web que carregam uma vez, e quando o usuário clica em um link ou um botão, a execução de JavaScript na página atualiza a barra de endereços, mas a página web não é atualizada. A gestão da barra de endereços é feita por algo chamado de **roteador** .

O roteador mais popular no ecossistema React é o [react-router](https://github.com/rackt/react-router). Se você está construindo uma aplicação de uma única página, você deve usá-lo, a não ser que você tenha uma boa razão para não utilizar.

**Não use um roteador, caso você não esteja construindo uma aplicação de single-page**. A maioria dos projetos começam com componentes menores dentro de uma aplicação maior de qualquer maneira.

## Aprendendo Flux

Você provavelmente já ouviu falar de Flux. Há uma **tonelada** de desinformação sobre Flux lá fora.

Um monte de gente senta para criar um aplicativo e quer definir seu modelo de dados, e eles acham que precisam usar Flux para isso. **Este é o caminho errado para adotar Flux. Flux só deve ser adicionado uma vez que muitos componentes já foram construídos.**

Componentes React são dispostos numa hierarquia. Na maioria das vezes, o seu modelo de dados também segue uma hierarquia. Nestas situações Flux não compra muito. Às vezes, porém, o seu modelo de dados não é hierárquico. Quando seu componente React começar a receber `props` que são estranhos, ou você tem um pequeno número de componentes começando a ficar muito complexo, então você pode querer utilizar para Flux.

**Você saberá quando precisara de Flux. Se você ainda não tem certeza que precisa dele, você não precisa dele.**

Se você decidiu usar Flux, a mais popular e bem documentada biblioteca Flux é [Redux] (http://redux.js.org/). Há **um monte** de alternativas lá fora, e você vai ser obrigado a avaliar muitos deles, mas meu conselho é utilizar os mais populares.

## Aprendendo inline styles

Antes de React, um monte de gente reutiliza estilos CSS com folhas de estilo complicadas construídas por pre processadores como SASS. React faz você escrever componentes fácilmente reutilizáveis, e suas folhas de estilo podem ser menos complicados. Muitos na comunidade (inclusive eu) estão experimentando com livrar-se de folhas de estilo completamente. 

Esta é uma ideia bastante louca por uma série de razões. Faz media queries se tornarem mais difíceis, e é possível que existam limitações de desempenho usando esta técnica. **Ao iniciar com a React, os estilos são usados da maneira que você faria normalmente.**

Uma vez que você tem uma idéia de como React funciona, você pode olhar para técnicas alternativas. Um popular é [BEM] (https://en.bem.info/). Eu recomendo eliminar seu pré-processador CSS, uma vez que React dá-lhe uma forma mais poderosa para reutilizar estilos (através da reutilização de componentes) e seu bundler JavaScript pode gerar folhas de estilo mais eficientes para você (eu dei [a falar sobre isso em OSCON] (https: / /www.youtube.com/watch?v=VkTCL6Nqm6Y)). Com isso dito, React, como qualquer outra biblioteca JavaScript, vai funcionar muito bem com um pré-processador CSS.

Uma alternativa é você usar [Módulos CSS] (http://glenmaddern.com/articles/css-modules), mais especificamente [react-css-modules] (https://github.com/gajus/react-css-modules). Com módulos CSS você ainda vai escrever CSS (ou SASS /LESS/Stylus), mas você pode gerenciar e compor seus arquivos CSS como você faria com estilos inline em React. E você não precisa se preocupar com o gerenciamento de seus nomes de classe utilizando metodologias como BEM, já que isso vai ser tratado para você, sob o capô pelo sistema do módulo.

## Aprendendo renderização de servidor

Renderização de servidor é muitas vezes chamado de "universal" ou "isomórfico" JS. Isso significa que você pode tirar seus componentes React e torná-los HTML estático no servidor. Isso melhora o desempenho de arranque inicial, porque o usuário não precisa esperar para baixar os arquivos JS a fim de ver a interface do usuário inicial, e React pode voltar a usar o HTML renderizado no servidor para que ele não precisa gerá-lo do lado do cliente.

Você precisa que o servidor renderize se você notar que sua renderização inicial é muito lenta ou se você quiser melhorar o seu ranking nos motores de busca. Embora seja verdade que o Google agora indexa conteúdo renderizados no cliente, a partir de janeiro 2016 cada vez que ele foi medido tem sido demonstrado que afetam negativamente a classificação, principalmente devido ao desempenho negativo de renderização do lado do cliente.

Renderização de servidor ainda requer uma grande quantidade de ferramentas para funcionar direito. Desde que componentes Reacts suportem transparencia, escritos sem renderização de servidor, você deve construir seu primeiro aplicativo e se preocupar com renderização de servidor mais tarde. Você não vai precisar de reescrever todos os seus componentes para utiliza-lo.

## Aprendendo Immutable.js

[Immutable.js](https://facebook.github.io/immutable-js/) fornece um conjunto de estruturas de dados que podem ajudar a resolver certos problemas de desempenho quanto a construção aplicativos React. É uma grande biblioteca, e você provavelmente vai usá-lo muito em seus aplicativos daqui pra frente, mas é completamente desnecessário até que você tenha uma apreciação das implicações de desempenho.

## Aprendendo Relay, Falcor etc

São tecnologias que ajudam a reduzir o número de solicitações de AJAX. Eles ainda são tecnologias de ponta, por isso, se você não tem um problema com muitas solicitações, você não precisa de Relay ou Falcor.
