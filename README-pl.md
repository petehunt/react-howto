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
* [ES6](#nauka-es6)
* [Routing](#nauka-routing)
* [Flux](#nauka-flux)

**Nie musisz zapoznawać się ze wszystkimi materiałami, żeby zbudować swoje pierwsze aplikacje w React.** Przejdź do kolejnego kroku tylko jeśli napotkasz na problem, który może być rozwiązany jedynie przez inną technologię.

Dodatkow często spotkasz się z innymi tematami w społeczności React, które są w trakcie rozwoju i są określane terminem "bleeding edge". Tematy te są oczywiście bardzo interesujące, ale zazwyczaj trudne do zrozumienia, są znacznie mniej popularne niż te wymienione powyżej i **nie są wymagane w większości przypadków**.
* [Style Inline](#nauka-stylow-inline)
* [Renderowanie po stronie serwera](#nauka-renderowania-po-stronie-serwera)
* [Immutable.js](#learning-immutablejs)
* [Relay, Falcor, itd.](#nauka-relay-falcor-itp)

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

## Nauka ES6

W przykładach kodu napisanego w React, oprócz na JSX, zwróciłeś pewnie uwagę na niektóre nietypowe składnie. Jest to najnowsza wersja JavaScript, o której mogłeś jeszcze nie usłyszeć, zwana ES6. Ponieważ jest to relatywnie nowa technologia, nie jest wspierana przez przeglądarki, ale wspomniane wcześniej bundlery pomogą nam w przetłumaczeniu tego kodu na wcześniejsze standardy JavaScript, dobrze wspierane przez przeglądarki.

Jeśli chcesz się skupić na razie wyłącznie na React, **możesz pominąć naukę ES6**, lub spróbować jej w trakcie, w każdym momencie nauki.

Prawdopodobnie spotkałeś się już z kilkoma wpisami w Internecie, które przekonują do używania klas ES6, jako zalecanej metody tworzenia komponentów w React. To nieprawda. Większość (wliczając również Facebook) używa `React.createClass()`.

## Nauka routingu

Aplikacje webowe zwane "Single-page applications" są obecnie bardzo modne. To takie aplikacje, które ładują się tylko raz, a gdy użytkownik kliknie link lub przycisk, JavaScript aktualizuje pasek adresu, ale strona nie jest odświeżana. Zarządzanie paskiem adresu realizowane jest właśnie przez **router**.

Najpopularniejszym routerem używanym w ekosystemie React jest [react-router](https://github.com/rackt/react-router). Jeśli zamierzasz zbudować "single-page application", użyj go, chyba że masz naprawdę dobry powód żeby wybrać inne rozwiązanie.

**Nie używaj routera, jeśli nie zamierzasz zbudować single-page application**. Większość projektów zaczyna jako mniejsze komponenty, które użyte są w większych aplikacjach.

## Nauka Flux

Na pewno słyszałeś już o Flux. Niestety *cała masa* informacji o Flux, którą możesz przeczytać w Internecie, jest mylna.

Większość ludzi, gdy tylko zaczyna tworzyć aplikację i chcą zdefiniować model danych, są przekonani że muszą użyć do tego Flux. **To nieprawidłowy sposób użycia Flux. Flux powinien być dodany dopiero gdy w projekcie stworzysz już wiele komponentów.**

Komponenty React są ułożone hierachicznie. W większości przypadków, Twój model danych też przestrzega jakiejś hierarchii. W takich przypadkach, Flux nie jest potrzebny. Czasami jednak Twój model danych nie przestrzega specyficznej hierarchii. Jeśli Twoje komponenty React otrzymują parametry (`props`), które wydają się być z nim niezwiązane, lub masz małą ilość komponentów które zaczynają być coraz bardziej skomplikowane, wtedy pewnie powinieneś zacząć używać Flux.

**Sam będziesz dobrze wiedział kiedy potrzebujesz użyć Flux. Jeśli nie jesteś pewien, najprawdopodobniej go wcale nie potrzebujesz.**

Jeśli podjąłeś już decyzję użycia Flux, najpopularniejszą i świetnie udokumentowaną implementacją Flux jest [Redux](http://redux.js.org/). Jest *pełno* alternatyw, będziesz koniecznie chciał wypróbować wiele z nich, ale zalecam Ci skorzystanie z tej najbardziej popularnej biblioteki.

## Nauka stylów inline

Przed erą React, dużo ludzi korzystało ze stylów CSS, budując skomplikowane arkusze stylów, budowane przez preprocesory jak SASS. Odkąd React sprawia, że pisanie komponentów wielokrotnego użytku stało się proste, Twoje arkusze stylów mogą być znacznie mniej skomplikowane. Dużo osób w społeczności React (wliczając również mnie) eksperymentuje, aby w ogóle zrezygnować z używania arkuszy stylów.

Jest to dość szalony pomysł z kilku powodów. Sprawia, że media queries stają się trudniejsze w użyciu, oraz możliwe że są pewne limity wydajnościowe gdy używamy tej metody. **Jeśli dopiero zaczynasz z React, używaj stylów tak jak byś to robił w innych przypadkach.**

Kiedy poczujesz się już pewnie w React, możesz wypróbować innych, alternatywnych technik. Jednym z popularnych jest [BEM](https://en.bem.info/). Polecam Ci zaprzestanie używania preprocesorów CSS, ponieważ React oferuje znacznie bardziej skuteczny sposób ponownego użycia stylów (poprzez ponowne użycie komponentów) a Twój bundler JavaScript potrafi wygenerować znacznie bardziej wydajne arkusze stylów (Mówiłem o tym na [OSCON](https://www.youtube.com/watch?v=VkTCL6Nqm6Y)). React, tak jak inne biblioteki JavaScript, będzi działał dobrze z preprocesorem CSS.

Alternatywnie, możesz też użyć tzw. ["CSS Modules"](http://glenmaddern.com/articles/css-modules), a dokładniej mówiąc [react-css-modules](https://github.com/gajus/react-css-modules). Nadal będziesz używał CSS (lub SASS/LESS/Stylus) pisząc w "CSS Modules", ale możesz zorganizować i komponować swoje pliki CSS w ten sam sposób jak byś to robił ze stylami inline. Wtedy nie musisz się też przejmować używaniem właściwych nazw klasy korzystając z metodologi BEMA, ponieważ będą one zarządzane poprzez moduły.

## Nauka renderowania po stronie serwera

Renderowanie po stronie serwera jest często nazywane "uniwesalnym" lub "izomorficznym" JS. Oznacza to, że możesz wyświetlać swoje komponenty React jako statyczny HTML na serwerze. To poprawia wydajność na samym początku ładowania strony, bo użytkownik nie musi czekać na załadowanie JS, aby wyświetlić interfejs strony. React potrafi wykorzystać HTML wygenerowany na serwerze, tak, aby nie było potrzeby tworzyć go ponownie po stronie klienta.

Potrzebujesz renderowania na serwerze, jeśli zauważysz, że czas na wyświetlenie Twojej strony na początku jest zbyt długi oraz jeśli chcesz poprawić swoją pozycję w wyszukiwarkach. Pomimo tego, że Google potrafi już indeksować HTML wygenerowany przez klienta – w styczniu 2016 zbadano, że to nadal negatywnie wpływa na pozycję strony (prawdopodobnie w związku z gorszą wydajnością stron generowanych po stronie klienta).

Renderowanie na serwerze ciągle wymaga wiele narzędzi do poprawnego działania. W związku z tym, że zapewnia ono wsparcie komponentów React napisanych w tradycyjnym stylu, nadal lepiej napisać aplikację w pierwszej kolejności, a dopiero później martwić się o renderowanie na serwerze. Nie będzie potrzeby przepisywać wszystkich komponentów, aby renderować aplikację na serwerze.

## Nauka Immutable.js

[Immutable.js](https://facebook.github.io/immutable-js/) zapewnia zbiór struktur danych, które pomagają w rozwiązaniu pewnych problemów z wydajnością podczas budowania aplikacji w React'cie. To świetna biblioteka i prawdopodobnie będziesz dużo z niej korzystać w swoich aplikacjach w przyszłości – jednak jest kompletnie niepotrzebna dopóki nie zrozumiesz kwestii związanych z wydajnością Twojej aplikacji.

## Nauka Relay, Falcor itp.

Te narzędzia pomogą ograniczyć ilość zapytań AJAX. Są nadal bardzo świeże, więc jeśli nie masz problemu ze zbyt dużą ilością zapytań, nie potrzebujesz Relay ani Falcor.