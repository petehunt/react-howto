# react-howto

Stawiając pierwsze kroki w React (lub po prostu będąc nowym w temacie front-end'u), bardzo łatwo pogubić się w tym całym ekosystemie. Jest to spowodowane kilkoma rzeczami:

* Grupą docelową React byli entuzjaści technologii i eksperci,
* Facebook udostępnia to z czego sam korzysta, nie skupiają się nad stworzeniem uniwersalnego narzędzia dla wszystkich (w tym mniejszych) projektów,
* W sieci możecie znaleźć pełno mylących artykułów, które tylko z nazwy mają coś wspólnego z przewodnikiem po React.

Pisząc ten dokument, zakładam że miałeś okazję zbudować stronę opartą o HTML, CSS i JavaScript.

## Dlaczego powinnieneś posłuchać akurat mnie?

Możecie znaleźć całą masę porad dotyczących React, które często się wykluczają; dlaczego więc powinieneś posłuchać akurat mnie?

Byłem jednym z członków zespołu w Facebook'u, który stworzył i opublicznił React. Nie pracuję już w Facebook'u, ale zajmuję się teraz małym startup'em, dzięki któremu zdobyłem inną perspektywę.

## Jak zacząć w ekosystemie React?

Każde oprogramowanie jest zbudowane z przeróżnych technologii, więc najpierw pownienieś dobrze zrozumieć z czego właściwie jest zbudowana Twoja aplikacja. Z początku cały ekosystem React przytłacza, ponieważ zawsze jest on tłumaczony w złej kolejności.

Poniżej znajdziesz prawidłową kolejność, której powinieneś przestrzegać **bez omijania żadnego punktu czy uczenia się jednocześnie kilku rzeczy na raz**:

* [React](#nauka-samego-react)
* [`npm`](#nauka-npm)
* [JavaScript “bundlers”](#nauka-bundlerow-javascript)
* [ES6](#learning-es6)
* [Routing](#learning-routing)
* [Flux](#learning-flux)

**Nie musisz zapoznawać się ze wszystkimi materiałami, żeby zbudować swoje pierwsze aplikacje w React.** Przejdź do kolejnego kroku tylko jeśli napotkasz na problem, który może być rozwiązany jedynie przez inną technologię.

Dodatkow często spotkasz się z innymi tematami w społeczności React, które są w trakcie rozwoju i są określane terminem "bleeding edge". Tematy te są oczywiście bardzo interesujące, ale zazwyczaj trudne do zrozumienia, są znacznie mniej popularne niż te wymienione powyżej i **nie są wymagane w większości przypadków**.
* [Inline styles](#learning-inline-styles)
* [Server rendering](#learning-server-rendering)
* [Immutable.js](#learning-immutablejs)
* [Relay, Falcor, itd.](#learning-relay-falcor-etc)

## Nauka samego React

Bardzo często spotkasz przekonanie że aby zacząć naukę React musisz spędzić sporo czasu, żeby skonfigurować całe środowisko i zainstalować masę narzędzi. W oficjalnej dokumentacji znajdziesz [kod HTML "kopiuj-wklej"](https://facebook.github.io/react/docs/getting-started.html#quick-start-without-npm), który wystarczy zachować jako plik `.html`. **Nie potrzebujesz do tego żadnych narzędzi, więc nie instaluj żadnych dodatkowych rzeczy dopóki nie poczujesz się komfortowo z podstawami React.**

Nadal uważam, że najłatwiej nauczyć się React z [oficjalnego samouczka](https://facebook.github.io/react/docs/tutorial.html).

## Nauka `npm`

`npm` jest systemem paczek dla środowiska Node.js za pomocą którego front-end developerzy dzielą się JavaScript'owym kodem. Zawiera on system zwany `CommonJS` i pozwala Ci zainstalować narzędzia napisane w JavaScript za pomocą linii poleceń. Przeczytaj [ten artykuł](http://0fps.net/2013/01/22/commonjs-why-and-how/) aby dowiedzieć się dlaczego `CommonJS` jest potrzebny, lub [CommonJS Wiki](http://wiki.commonjs.org/wiki/Introduction) aby dowiedzieć się więcej o API `CommonJS`.

Komponenty, biblioteki i narzędzia których używa się często w ekosystemie React są zazwyczaj dostępne jako moduły `CommonJS` i instaluje się je za pomocą `npm`.

## Nauka bundler'ów JavaScript

Ze względu na techniczne przeszkody, moduły `CommonJS` (czyli wszystko co znajdziesz w `npm`) nie mogą być użyte natywnie w przeglądarce. Potrzebujesz tzw. "bundler'a", aby "związać" ("połączyć") te moduły w pliki `.js`, które możesz dołączyć do swojej strony za pomocą tagu `<script>`.

Przykłady takich bundler'ów dla JavaScript to `webpack` i `browserify`. Każdy z nich to dobry wybór, ale osobiścię wolę `webpack`, ponieważ oferuje znacznie więcej możliwości, które sprawiają że budowa dużych aplikacji jest znacznie łatwiejsza. Ponieważ jego dokumentacja może być myląca, używam [gotowy template](https://github.com/petehunt/react-webpack-template) i napisałem [poradnik dla webpack'a](https://github.com/petehunt/webpack-howto) dla bardziej zaawansowanych przypadków.

React oferuje też [oficjalne narzędzie odpalane w wierszu poleceń, nazwane "Stwórz aplikację React" ("Create React App")](https://github.com/facebookincubator/create-react-app). Pozwala ono na utworzenie projektu w React, przy wsparciu `webpack`'a, bez koniecznej dodatkowej konfiguracji. Narzędzie może Cię trochę ograniczać, ale na pewno warto od niego zacząć, zwłaszcza że przyszłe aktualizacje na pewno rozszerzą zakres jego funkcji. Oferuje również możliwość skopiowania wszystkich plików konfiguracyjnych i zależności w projekcie, więc tak naprawdę nie tracisz nad nimi kontroli.

Jedna rzecz, o której warto pamiętać: `CommonJS` używa funkcji `require()` do importowania modułów, dlatego dużo osób myli go z projektem nazwanym `require.js`. Z kilku technicznych powodów, zalecam unikanie `require.js`. Nie jest on zbyt popularny w ekosystemie React.

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