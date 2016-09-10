# react-howto

Pokud jste se rozhodli začít s Reactem (nebo frontendem obecně), lehce se můžete v celém ekosystému nástrojů a technik ztratit. Co je příčinou?

* React byl od počátku cílen na experty a ty, kteří rádi zkoušejí nové technologie
* Facebook opensourcuje pouze věci, které sám používá a přirozeně je necílí na menší projekty
* Na internetu je spousta zavádějících React návodů

Tento návod předpokládá, že jste už někdy vytvořili stránku s HTML, CSS a JavaScriptem.

## Proč byste měli poslouchat mě?

Existuje spousta protichůdných rad ohledně Reactu. Proč byste měli dát zrovna na ty mé?

Jsem jeden z původních členů Facebook týmu, který React vytvořil a opensourcoval. Před časem jsem však Facebook opustil a začal pracovat v menším startupu. Mám tak k dispozici i pohled z druhé strany barikády.

## Jak se neztratit v React ekosystému

Každý software je postaven na několika vrstvách různých technologií. Abyste mohli vytvořit vaši aplikaci, musíte každé této vrstvě alespoň částečně rozumět. React ekosystém vypadá komplikovaně, protože je vždy představován ve špatném pořadí.

Měli byste se držet tohoto pořadí, **bez přeskakování nebo učení se více věcí naráz**:

* [Samotný React](#user-content-naučte-se-samotný-react)
* [`npm`](#user-content-naučte-se-npm)
* [JavaScript “bundlers”](#user-content-naučte-se-javascript-bundlery)
* [ES6](#user-content-naučte-se-es6)
* [Routing](#user-content-naučte-se-routing)
* [Flux](#user-content-naučte-se-flux)

**Nemusíte znát všechno, abyste byli s Reactem produktivní.** Přejděte k dalšímu kroku pouze tehdy, pokud máte zásadní problém, který s ním můžete vyřešit.

Můžete narazit i na několik dalších témat, která se v souvislosti s Reactem skloňují. Jde převážně o nejnovější "výstřelky". Jsou zajímavé, ale také poměrně složité k pochopení a daleko méně populární než ty, které jsem již zmínil výše. **K většině aplikací je nepotřebujete**.

* [Inline styly](#user-content-naučte-se-inline-styly)
* [Server rendering](#user-content-naučte-se-server-rendering)
* [Immutable.js](#user-content-naučte-se-immutablejs)
* [Relay, Falcor, atd](#user-content-naučte-se-relay-falcor-atd)

## Naučte se samotný React

Často se setkáte s tvrzením, že musíte strávit hodně času s nastavováním různých nástrojů, abyste se mohli naučit React. V oficiální dokumentaci naleznete [copy&paste HTML šablonu](https://facebook.github.io/react/docs/getting-started.html#quick-start-without-npm), kterou můžete uložit jako `.html` soubor a ihned si tak začít s Reactem hrát. **V tomto kroku nepotřebujete žádné nástroje a nemusíte se tak trápit s jejich dokumentací ještě před tím, než se seznámíte se základy Reactu.**

Za nejsnažší cestu k naučení Reactu stále pokládám [oficiální tutoriál](https://facebook.github.io/react/docs/tutorial.html).

## Naučte se `npm`

`npm` je balíčkovací systém pro Node.js a zdaleka nejpopulárnější kanál, kterým si frontend vývojáři sdílí svůj kód. Je postaven na modulárním systému `CommonJS` a nechá vás instalovat CLI  nástroje psané v JavaScriptu. Přečtěte si [tento článek](http://0fps.net/2013/01/22/commonjs-why-and-how/), pokud vás zajímá, proč je `CommonJS` nezbytný pro prohlížeče nebo [CommonJS Spec Wiki](http://wiki.commonjs.org/wiki/Introduction), pokud se chcete rovnou ponořit do `CommonJS` API.

Většina znovupoužitelných komponent, knihoven a nástrojů v React ekosystému je k dispozici jako `CommonJS` modul, který se dá nainstalovat pomocí `npm`.

## Naučte se JavaScript bundlery

Hned z několika dobrých technických důvodů nemůžou `CommonJS` moduly (vše v `npm`) nativně běžet v prohlížeči. Potřebujete JavaScript bundler, který vám tyto moduly převede do `.js` souborů. Ty pak můžete vložit na svoji stránku pomocí tagu `<script>`.

Příkladem JS bundlerů je `webpack` a `browserify`. Oba jsou dobrou volbou, ale osobně preferuji `webpack`, protože nabízí více funkcí, které dělají vývoj velkých aplikací jednodušší. Protože je jeho dokumentace občas matoucí, mám připravenou [univerzální šablonu](https://github.com/petehunt/react-webpack-template). Napsal jsem také [Webpack návod](https://github.com/petehunt/webpack-howto) pro složitější případy.

Důležitá poznámka: `CommonJS` používá `require()` funkci k importování modulů a tak si ho hodně lidí plete s projektem nazvaným `require.js`. Z mnoha vážných důvodů vám doporučuji se `require.js` vyhnout. V React ekosystému navíc není moc populární.

## Naučte se ES6

Kromě JSX (který jste se naučili v React tutoriálu), můžete narazit v React příkladech ještě na další prapodivnou syntax. Jedná se o ES6, což je nejnovější verze JavaScriptu a může se tak stát, že jí vidíte poprvé. Protože je natolik nová, nemá ještě moc velkou podporu v prohlížečích. Avšak správně nastavený bundler ji může přeložit do starší verze, tak aby ve všech prohlížečích fungovala.

Pokud chcete jednoduše začít vyvíjet v Reactu, **můžete učení se ES6 syntaxe přeskočit** nebo jí prostě přibrat po cestě.

Můžete narazit na názory, že ES6 třídy jsou preferovaná cesta pro vytváření React komponent. Toto není pravda. Většina lidí (včetně Facebooku) používá `React.createClass()`.

## Naučte se routing

Všichni dnes mluví o “single-page aplikacích”. Tyto aplikace se načtou naráz. JavaScript v pozadí pak mění URL adresu, když uživatel klikne na odkaz či tlačítko, ale samotná stránka se znova už nenačítá. Správa adresního řádku je řízena tzv. **routerem**.

Nejpopulárnějším routerem v React ekosystému je [react-router](https://github.com/rackt/react-router). Pokud vytváříte single-page aplikaci, použijte ho, pakliže nemáte dobrý důvod proč ne.

**Nepoužívejte router, pokud nevytváříte single-page aplikaci**. Většina projektů beztak začíná pouze jako soubor několika menších komponent v rámci větší aplikace.

## Naučte se Flux

Pravděpodobně jste slyšeli o Fluxu. Existuje *ohromné množství* bludů o Fluxu.

Spousta lidí začne vyvíjet aplikaci tak, že si sedne a začne přemýšlet o datovém modelu. Myslí si, že se nelze bez Fluxu obejít. **Tohle je ovšem špatná cesta, jak s Fluxem začít. Flux by měl být nasazen až když už máte několik různých komponent.**

React komponenty jsou organizované v hierarchii, kterou datový model většinou následuje. V takových případech vám Flux moc nepomůže. Občas však váš datový model má strukturu jinou. Jakmile si musíte předávat v React komponentách nadměrné množství `props` nebo některé komponenty začnou být příliš komplexní, až tehdy se vyplatí začít o Fluxu přemýšlet.

**Bezpečně poznáte chvíli, kdy budete Flux potřebovat. Pokud si nejste jisti, tak ho nepotřebujete.**

Pokud jste se rozhodli použít Flux, mrkněte na nejpopulárnější a dobře zdokumentovanou Flux knihovnu [Redux](http://redux.js.org/). Existuje spousta alternativ a může být těžké odolat pokušení je všechny prozkoumat. Moje rada však je, abyste použili tu nejpopulárnější.

## Naučte se inline styly

Před érou Reactu hodně lidí používalo pro lepší správu CSS stylů komplikované preprocesory jako SASS. React zjednodušil psaní znovupoužitelných komponent, avšak i vaše styly mohou být méně komplikované. Mnoho lidí v naší komunitě (včetně mě) experimentuje s úplným odstraněním kaskádových stylů.

Jde o trochu šílenou myšlenku z mnoha důvodů. Komplikuje to media queries a může to představovat i výkonnostní problém. **Pokud začínáte s Reactem, použijte styly tak jak je normálně znáte**.

Jakmile se s Reactem více seznámíte, můžete vyzkoušet některé alternativní techniky. Jednou z populárních je [BEM](https://en.bem.info/). Doporučuji, abyste se postupně zbavovali CSS preprocesoru, protože React vám dává daleko mocnější cestu, jak styly znovu používat (znovu používáním komponent) a váš JavaScript bundler může vygenerovat více efektivní styly za vás. (Měl jsem o tomto [přednášku na OSCONu](https://www.youtube.com/watch?v=VkTCL6Nqm6Y)). Na druhou stranu, pokud trváte na svém, React bude fungovat s preprocesorem stejně dobře jako jakákoliv jiná JS knihovna.

Další možností je použít [CSS Modules](http://glenmaddern.com/articles/css-modules), konkrétně knihovnu [react-css-modules](https://github.com/gajus/react-css-modules). Díky CSS Modules můžete pořád psát CSS (nebo SASS/LESS/Stylus), ale zároveň i spravovat a komponovat vaše CSS soubory tak, jak byste to dělali s inline styly v Reactu. Také se nemusíte starat o názvy CSS tříd (narozdíl od BEM), jelikož i to za vás tato knihovna vyřeší.

## Naučte se server rendering

Server rendering je často označován jako "univerzální" nebo "isomorfní" JavaScript. Znamená to, že můžete vzít na serveru vaši React komponentu a vyrendrovat ji do statického HTML, které pak pošlete do prohlížeče. To zlepší prvotní načtení stránky, protože uživatel nemusí čekat na stažení JS před tím, než se cokoliv zobrazí. React navíc umí použít předrendrované HTML ze serveru, takže se už nemusí v prohlížeči nic přepočítávat.

Server rendering se může hodit, pokud se vaše stránka načítá příliš pomalu nebo pokud chcete zlepšit indexaci ve vyhledávačích. Je sice pravda, že Google už umí indexovat i stránky generované JS v prohlížeči, avšak dle měření z ledna 2016 plyne, že to má vždy negativní efekt na výsledné umístění stránky. Pravděpodobně kvůli delší odezvě.

Server rendering navíc vyžaduje spoustu dalších nástrojů. React komponenty mohou být vyrendrované na serveru bez jakýchkoliv dalších úprav. Můžete tudíž nejdříve vytvořit celou aplikaci a o server rendering se starat až později. Nemusíte přepsat všechny své komponenty, aby fungoval.

## Naučte se Immutable.js

[Immutable.js](https://facebook.github.io/immutable-js/) poskytuje sadu datových struktur, která vám může pomoci vyřešit jisté výkonnostní problémy při vývoji React aplikací. Je to skvělá knihovna a pravděpodobně ji použijete časem ve spoustě svých aplikací. Avšak lze se zcela obejít i bez ní. Minimálně do chvíle, než vám bude připadat vaše aplikace pomalá.

## Naučte se Relay, Falcor atd

Tyto technologie vám mohou pomoci zredukovat počet AJAX požadavků. Jsou však pořád velmi experimentální. Pokud nemáte problém s nadměrným množstvím AJAX požadavků, nepotřebujete Relay ani Falcor.
