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
* [Inline styles](#learning-inline-styles)
* [Server rendering](#learning-server-rendering)
* [Immutable.js](#learning-immutablejs)
* [Relay, Falcor, etc](#learning-relay-falcor-etc)

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

podes já ter ouvido alguma talk sobre as classes ES6 serem uma melhor maneira de criar componentes React. Isto não é verdade. A maioria das pessoas (incluindo no Facebook), usam `React.createClass()`.
