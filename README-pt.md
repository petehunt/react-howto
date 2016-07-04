# react-howto

Se te estás a iniciar agora com React (ou frontend no geral) talvez aches o ecossistema confuso. E tens alguma razão.

* React foi criado, historicamente, para iniciantes mas também para profissionais
* O Facebook apenas coloca em open-source aquilo que eles usam, para que não se foquem em ferramentas para usar com projetos mais pequenos que o próprio Facebook
* Existe muita publicidade enganosa mascarada de Guias para React

Ao longo deste documento, vou assumir que já construiste uma página usando HTML, CSS e JavaScript.

## Porque é que me deves ouvir?

Existe uma tonelada de conselhos conflituosos sobre React por aí; porque me ouvir?

Eu fiz parte da equipa original do Facebook que criou React como open-source. Já não estou no Facebook. Agora estou numa pequena startup por isso acrescento ainda uma prespetiva de alguém de fora do facebook.

## Como lidar com o ecossistema de Rect

Todo o software é criado usando uma stack de Tecnologia e por isso, precisas de conhecer o suficiente dessa stack para desenvolveres a tua aplicação. A razão pela qual o ecossistema de React é tão confuso deve-se ao facto de ser explicado pela ordem errada.

Tu deves aprender por esta ordem, **sem passar nada a frente nem aprender as coisas paralelamente**:
* [o próprio React](#aprendendo-react)
* [`npm`](#aprendendo-npm)
* [JavaScript “bundlers”](#aprendendo-javascript-bundlers)
* [ES6](#aprendendo-es6)
* [Routing](#aprendendo-routing)
* [Flux](#aprendendo-flux)

**Não precisas de aprender tudo isto para seres produtivo com React.** Passa apenas para o próximo passo se tiveres algum problema que precisas que seja resolvido.

Adicionalmente, existem alguns tópicos mencionados pela comunidade de React que são "bleeding edge". Os tópicos a baixo são interessantes, mas são dificeis de entender e muito menos populares do que os de cima e **não são obrigatórios para a maioria das aplicações**.
* [Inline styles](#aprendendo-inline-styles)
* [Server rendering](#aprendendo-server-rendering)
* [Immutable.js](#aprendendo-immutablejs)
* [Relay, Falcor, etc](#aprendendo-relay-falcor-etc)

## Aprendendo React

É um equívoco comum que tu precisas de perder muito tempo a configurar o teu ambiente de ferramentas para começares a aprender Reagir. Na documentação oficial, encontrarás um [template HTML copy-paste] (https://facebook.github.io/react/docs/getting-started.html#quick-start-without-npm) que podes guardar num ficheiro com extensão '.html' e começar imediatamente. ** Nenhuma ferramenta é necessária para esta etapa, e não começes a aprender outra ferramental adicional até que te sintas confortável com o básico de React. **

Eu continuo a achar que a maneira mais fácil de aprender React é [a documentação oficial](https://facebook.github.io/react/docs/tutorial.html).

## Aprendendo `npm`

`npm` é um gerenciador de pacotes (packages manager) de Node.js e é a maneira mais popular com que os engenheiros e designers de Front-end partilham código Javascript. Incui um módulo chamado 'CommonJS' e deixa-te instalar ferramentas de linha de comandos escritas em Javascript. Lê [este post](http://0fps.net/2013/01/22/commonjs-why-and-how/) para saberes mais sobre o porquê de 'CommonJS' é necessário para os browsers, ou [CommonJS Spec Wiki](http://wiki.commonjs.org/wiki/Introduction) para saberes mais sobre a API de 'CommonJS'.

A maioria dos componentes reutilizáveis, librarias e ferramentas sobre o ecossistema React estão disponíveis como módulos 'CommonJS' e são instaçados com 'npm'.

## Aprendendo JavaScript bundlers

Para uma série de boas razões técnicas, os módulos de 'CommonJS' (ex. tudo em 'npm') não pode ser usado nativamente no browser. Tu precisas de um "bundler" de JavaScript para "juntar" esses módulos em ficheiros com extensão '.js' que podes incluir na tua página web com uma tag '<script>'.

Exemplos de Javascript bundlers incluem 'webpack' e 'browserify'. Ambos são boas opções, mas eu prefiro 'webpack' pois tem muitas mais caracteristicas que fazem com que o desenvolvimento de aplicações grandes seja mais fácil. Como a sua documentação pode ser um pouco confusa, Eu tenho um [template plug-and-play para começares](https://github.com/petehunt/react-webpack-template) com casos de uso mais complexos

Uma coisa para ter em mente: 'CommonJS' usa a função 'require()' para importar módulos, por isso muita gente fica confusa e pensa que tem alguma coisa haver com o projeto chamado 'require.js'. Por diferentes razões técnicas, eu sugiro que evites 'require.js'Também não é muito popular no ecossistema de React.

## Aprendendo ES6

Para além de JSX (que aprendeste no tutorial de React), podes encontrar alguma sintaxe engraçada nos exemplos de React. Chama-se ES6, e é a última versão de Javascript por isso, é provável que ainda não tenhas aprendido. Como é tão recente, ainda não é suportada nos browsers mas o teu bundler pode traduzir por ti configurando-o da melhor maneira.

Se o que realmente queres é apenas saber trabalhar com React, **podes saltar à frente esta secção de ES6**, ou tenta voltar atrás daqui a uns tempos.

Podes já ter ouvido alguma talk sobre as classes ES6 serem uma melhor maneira de criar componentes React. Isto não é verdade. A maioria das pessoas (incluindo no Facebook), usam `React.createClass()`.

## Aprendendo routing

Aplicações do tipo "Single Page" (uma única página) são a moda, hoje em dia. São páginas web que carregam uma vez e, quando o user clica num link ou botão, o Javascript atualiza a barra de endereço, mas a página web não é carregada novamente. A esta gestão da barra de endereços, chamamos **router**.

 O router mais comum do ecossistema de React é [react-router](https://github.com/rackt/react-router). Se estás a criar uma single page, usa-o, a não ser que tenhas um bom motivo para não o fazeres.

 **Não uses um router se não estás a criar uma aplicação single page**. Aliás, a maioria dos projetos começam com componentes pequenos dentro de uma aplicação grande.

## Aprendendo Flux

Provavelmente já ouviste falar de Flux. Existem *toneladas* de má inflormação sobre Flux, por aí fora.

Algumas pessoas sentam-se para criar uma app e querem definir o modelo de dados, e pensam que precisam de Flux para isso. **Essa é a maneira errada de adoptar Flux. Flux só deve ser adicionado quando muitos componentes estão já construidos**.

Componentes React estão arranjados de forma hierárquica. Na maioria das vezes, o teu modelo de dados segue hierarquia também. Nessas situações, Flux não te ajuda assim muito. No entanto, o teu modelo de dados pode não ser hierárquico. Quando os teus componentes React começam a receber `props` que pareçam estranhos, ou tu tens um pequeno numero de componentes a começar a tornarem-se muito complexos, talvez queiras dar uma vista de olhos em Flux.

**Tu vais ter a certeza quando precisares de usar Flux. Se não tens a certeza se precisas, então, não precisas.**

Se decidiste que queres usar Flux, então, a mais popular e bem documentada libraria Flux é [Redux](http://redux.js.org/). Existem *imensas* alternativas por aí fora, e tu vais ficar tentado a avaliar muitas delas, mas o meu concelho é que fiques pela mais popular.

## Aprendendo inline styles

Antes de React, muitas pessoas reutilizavam folhas de estilo CSS complicadas produzidas com pré processadores tipo SASS. Como React faz com que seja fácil escrever componentes reutilizáveis, a tua folha de estilos pode ser menos complicada. Muitas pessoas na comunidade (eu próprio incluido) estão a experimentar livrar-se completamnete das folhas de estilo.

Esta é uma ideia completamente maluca por diversas razões. Faz com que as media querys sejam mais dificeis, e é possivel que existam limitações a nivel de performance com esta técnica. **Quando começas com React, faz o que normalmente fazias com os estilos**.

Assim que saibas como React funciona, podes olhar a algumas tecnicas. Uma muito popular é [BEM](https://en.bem.info/). Eu recomendo eliminar progressivamente o teu pré processador CSS, pois React dá te formas mais poderosas de reutilizar estilos (reutilizando componentes) e o teu Bundler Javascript pode gerar folhas de estilo mais eficientes para ti. )Eu dei uma  [talk sobre isto na OSCON](https://www.youtube.com/watch?v=VkTCL6Nqm6Y)). Com isto dito, React, como qualquer outra libraria Javascript, funciona bem à mesma com pré processadores CSS.

Em alternativa, tu podes usar [Módulos CSS](http://glenmaddern.com/articles/css-modules), mais espoecificamente, [react-css-modules](https://github.com/gajus/react-css-modules). Com módulos CSS, tu podes escrever CSS (ou SASS/LESS/Stylus), mas tu podes geri-los e compor os teus ficheiros CSS como tu farias com estilos inline em React. E não precisas de te preocupar com a gestão dos nomes das classes usando metodologias BEM, pois isso é lidado por ti, pelo módulo de Sistema.

## Aprendendo Server rendering

Server Rendering é usualmente chamado de Javascript "universal" ou "isomórfico". Significa que pode pegar nos teus componentes React e transforma-los em HTML estático no servidor. Isto melhora a performance inicial pois o User não precisa de esperar pelo JS para fazer download para que consiga ver a interface inicial, e o React pode reutilizar o HTML do server-rendering para que não precise de gerar o client-side.

Precisas de Server Rendering se reparares que o render inicial é demasiado lento ou se tu queres melhorar o sistema de ranking de pesquisas (SEO). Enquanto que é verdade que a Google indexa, agora, conteúdo de client-rendered,desde Janeiro de 2016 que, de todas as vezes que foi medido, mostra que afecta o ranking de forma negativa, potencialmente devido à penalização na performance de client-side rendering.

Server rendering necessita ainda, de muitas ferramentas para ser feito da melhor maneira. Desde que ele suporta de forma transparente os componentes React escritos sem server rendering em mente, deves construir a tua app primeiro e só depois preocupar-te com server-rendering. Tu não precisas de re-escrever todos os componentes para suporta-lo.

## Aprendendo Immutable.js

[Immutable.js](https://facebook.github.io/immutable-js/) dá-nos uma série de estruturas de dados que podem ajudar a resolver alguns problemas de performance quando construimos Apps React. É uma óptima libraria, e tu provavelmente vais usa-la em bastantes apps daqui para a frente, mas é completamente desnecessária até que tenhas um bom conhecimento das implicações na performance.

## Aprendendo Relay, Falcor etc

São tecnologias que te podem ajudar a reduzir o número de pedidos AJAX. Estão, ainda, muito na vanguarda por isso, se não tens problemas com muitos AJAX requests, não precisas nem de Relay nem de Falcor.
