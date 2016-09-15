# react-howto

Stawiając pierwsze kroki w React'cie (lub po prostu będąc nowym w temacie front-end'u), bardzo łatwo pogubić się w tym całym ekosystemie. Jest to spowodowane kilkoma rzeczami:

* Grupą docelową React'a byli entuzjaści technologii i eksperci,
* Facebook udostępnia to z czego sam korzysta, nie skupiają się nad stworzeniem uniwersalnego narzędzia dla wszystkich (w tym mniejszych) projektów,
* W sieci możecie znaleźć pełno mylących artykułów, które tylko z nazwy mają coś wspólnego z przewodnikiem po React'cie.

Pisząc ten dokument, zakładam że miałeś okazję zbudować stronę opartą o HTML, CSS i JavaScript.

## Dlaczego powinnieneś posłuchać akurat mnie?

Możecie znaleźć całą masę porad dotyczących React'a, które często się wykluczają; dlaczego więc powinieneś posłuchać akurat mnie?

Byłem jednym z członków zespołu w Facebook'u, który stworzył i opublicznił React'a. Nie pracuję już w Facebook'u, ale zajmuję się teraz małym startup'em, dzięki któremu zdobyłem inną perspektywę.

## Jak zacząć w ekosystemie React?

Każde oprogramowanie jest zbudowane z przeróżnych technologii, więc najpierw pownienieś dobrze zrozumieć z czego właściwie jest zbudowana Twoja aplikacja. Z początku cały React'owy ekosystem przytłacza, ponieważ zawsze jest on tłumaczony w złej kolejności.

Poniżej znajdziesz prawidłową kolejność, której powinieneś przestrzegać **bez omijania żadnego punktu czy uczenia się jednocześnie kilku rzeczy na raz**:

* [React](#learning-react-itself)
* [`npm`](#learning-npm)
* [JavaScript “bundlers”](#learning-javascript-bundlers)
* [ES6](#learning-es6)
* [Routing](#learning-routing)
* [Flux](#learning-flux)

**Nie musisz zapoznawać się ze wszystkimi materiałami, żeby zbudować swoje pierwsze aplikacje w React'cie.** Przejdź do kolejnego kroku tylko jeśli napotkasz na problem, który może być rozwiązany jedynie przez inną technologię.

Dodatkow często spotkasz się z innymi tematami w społeczności React'owej, które są w trakcie rozwoju i są określane terminem "bleeding edge". Tematy te są oczywiście bardzo interesujące, ale zazwyczaj trudne do zrozumienia, są znacznie mniej popularne niż te wymienione powyżej i **nie są wymagane w większości przypadków**.
* [Inline styles](#learning-inline-styles)
* [Server rendering](#learning-server-rendering)
* [Immutable.js](#learning-immutablejs)
* [Relay, Falcor, itd.](#learning-relay-falcor-etc)

## Nauka samego React'a

Bardzo często spotkasz przekonanie że aby zacząć naukę React'a musisz spędzić sporo czasu, żeby skonfigurować całe środowisko i zainstalować masę narzędzi. W oficjalnej dokumentacji znajdziesz [kod HTML "kopiuj-wklej"](https://facebook.github.io/react/docs/getting-started.html#quick-start-without-npm), który wystarczy zachować jako plik `.html`. **Nie potrzebujesz do tego żadnych narzędzi, więc nie instaluj żadnych dodatkowych rzeczy dopóki nie poczujesz się komfortowo z podstawami React'a.**

Nadal uważam, że najłatwiej nauczyć się React'a z [oficjalnego samouczka](https://facebook.github.io/react/docs/tutorial.html).

## Learning `npm`

`npm` is the Node.js package manager and is the most popular way front-end engineers and designers share JavaScript code. It includes a module system called `CommonJS` and lets you install command-line tools written in JavaScript. Read [this post](http://0fps.net/2013/01/22/commonjs-why-and-how/) for background on why `CommonJS` is necessary for browsers, or the [CommonJS Spec Wiki](http://wiki.commonjs.org/wiki/Introduction) for more on the `CommonJS` API.

Most reusable components, libraries and tools in the React ecosystem are available as `CommonJS` modules and are installed with `npm`.

## Learning JavaScript bundlers

For a number of good technical reasons `CommonJS` modules (i.e. everything in `npm`) cannot be used natively in the browser. You need a JavaScript “bundler” to “bundle” these modules into `.js` files that you can include in your web page with a `<script>` tag.

Examples of JavaScript bundlers include `webpack` and `browserify`. Both are good choices, but I prefer `webpack` since it has a lot of features that make development of large apps easier. Since its documentation can be confusing, I have a [plug-and-play template for getting started](https://github.com/petehunt/react-webpack-template) and I wrote a [how-to guide for webpack](https://github.com/petehunt/webpack-howto) for more complex use cases.

React also now offers [an officially supported CLI tool called Create React App](https://github.com/facebookincubator/create-react-app). It lets you create React projects powered by `webpack` without any configuration. It has its limitations, but it can serve as a great starting point, and its updates will add more features over time. It also offers an "ejection" feature that copies all configs and dependencies into your project so you have full control over them.

One thing to keep in mind: `CommonJS` uses the `require()` function to import modules, so a lot of people get confused and think that it has something to do with a project called `require.js`. For a number of technical reasons, I would suggest that you avoid `require.js`. It’s also not very popular in the React ecosystem.

## Learning ES6

Outside of JSX (which you learned in the React tutorial), you may see some funny syntax in React examples. This is called ES6, and it’s the latest version of JavaScript so you may not have learned it yet. Since it’s so new, it’s not supported in browsers yet, but your bundler can translate it for you with the proper configuration.

If you just want to get things done with React, **you can skip learning ES6**, or try to pick it up along the way.

You may see some talk about ES6 classes being the preferred way to create React components. This is untrue. Most people (including Facebook) are using `React.createClass()`.

## Learning routing

“Single-page applications” are all the rage these days. These are web pages that load once, and when the user clicks on a link or a button, JavaScript running on the page updates the address bar, but the web page is not refreshed. Management of the address bar is done by something called a **router**.

The most popular router in the React ecosystem is [react-router](https://github.com/rackt/react-router). If you’re building a single-page application, use it unless you have a good reason not to.

**Don’t use a router if you aren’t building a single-page application**. Most projects start out as smaller components inside of a larger application anyway.

## Learning Flux

You’ve probably heard of Flux. There’s a *ton* of misinformation about Flux out there.

A lot of people sit down to build an app and want to define their data model, and they think they need to use Flux to do it. **This is the wrong way to adopt Flux. Flux should only be added once many components have already been built.**

React components are arranged in a hierarchy. Most of the time, your data model also follows a hierarchy. In these situations Flux doesn’t buy you much. Sometimes, however, your data model is not hierarchical. When your React components start to receive `props` that feel extraneous, or you have a small number of components starting to get very complex, then you might want to look into Flux.

**You’ll know when you need Flux. If you aren’t sure if you need it, you don’t need it.**

If you have decided to use Flux, the most popular and well-documented Flux library is [Redux](http://redux.js.org/). There are *a lot* of alternatives out there, and you’ll be tempted to evaluate lots of them, but my advice is to just stick with the most popular one.

## Learning inline styles

Pre-React, a lot of people reused CSS styles with complicated style sheets built by preprocessors like SASS. Since React makes writing reusable components easy, your stylesheets can be less complicated. Many in the community (including myself) are experimenting with getting rid of stylesheets altogether.

This is a fairly crazy idea for a number of reasons. It makes media queries more difficult, and it's possible that there are  performance limitations using this technique. **When starting out with React, just style things the way you normally would.**

Once you've got a feel for how React works, you can look at alternate techniques. One popular one is [BEM](https://en.bem.info/). I recommend phasing out your CSS preprocessor, since React gives you a more powerful way to reuse styles (by reusing components) and your JavaScript bundler can generate more efficient stylesheets for you (I gave [a talk about this at OSCON](https://www.youtube.com/watch?v=VkTCL6Nqm6Y)). With that said, React, like any other JavaScript library, will work just fine with a CSS preprocessor.

Alternatively, you can also use [CSS Modules](http://glenmaddern.com/articles/css-modules), more specifically [react-css-modules](https://github.com/gajus/react-css-modules). With CSS Modules you'll still write CSS (or SASS/LESS/Stylus), but you can manage and compose your CSS files like you'd do with inline styles in React. And you don't need to worry about managing your class names using methodologies like BEM, as this will be handled for you under the hood by the module system.

## Nauka renderowania po stronie serwera

Renderowanie po stronie serwera jest często nazywane "uniwesalnym" lub "izomorficznym" JS. Oznacza to, że możesz wyświetlać swoje komponenty React jako statyczny HTML na serwerze. To poprawia wydajność na samym początku ładowania strony, bo użytkownik nie musi czekać na załadowanie JS, aby wyświetlić interfejs strony. React potrafi wykorzystać HTML wygenerowany na serwerze, tak, aby nie było potrzeby tworzyć go ponownie po stronie klienta.

Potrzebujesz renderowania na serwerze, jeśli zauważysz, że czas na wyświetlenie Twojej strony na początku jest zbyt długi oraz jeśli chcesz poprawić swoją pozycję w wyszukiwarkach. Pomimo tego, że Google potrafi już indeksować HTML wygenerowany przez klienta – w styczniu 2016 zbadano, że to nadal negatywnie wpływa na pozycję strony (prawdopodobnie w związku z gorszą wydajnością stron generowanych po stronie klienta).

Renderowanie na serwerze ciągle wymaga wiele narzędzi do poprawnego działania. W związku z tym, że zapewnia ono wsparcie komponentów React napisanych w tradycyjnym stylu, nadal lepiej napisać aplikację w pierwszej kolejności, a dopiero później martwić się o renderowanie na serwerze. Nie będzie potrzeby przepisywać wszystkich komponentów, aby renderować aplikację na serwerze.

## Nauka Immutable.js

[Immutable.js](https://facebook.github.io/immutable-js/) zapewnia zbiór struktur danych, które pomagają w rozwiązaniu pewnych problemów z wydajnością podczas budowania aplikacji w React'cie. To świetna biblioteka i prawdopodobnie będziesz dużo z niej korzystać w swoich aplikacjach w przyszłości – jednak jest kompletnie niepotrzebna dopóki nie zrozumiesz kwestii związanych z wydajnością Twojej aplikacji.

## Nauka Relay, Falcor itp.

Te narzędzia pomogą ograniczyć ilość zapytań AJAX. Są nadal bardzo świeże, więc jeśli nie masz problemu ze zbyt dużą ilością zapytań, nie potrzebujesz Relay ani Falcor.