# react-howto

Wenn man mit React, oder Frontendentwicklung allgemein, beginnt, kann das Ökosystem verwirrend sein. Dafür gibt es mehrere Gründe:

* React war ursprünglich an Early Adopter und Experten gerichtet
* Facebook veröffentlicht nur Open-Source Software, die es auch selbst nutzt. Deshalb sind alle Tools um diese Software nicht für Projekte ausgelegt, die kleiner als Facebook sind.
* Es gibt viel Marketing, das sich als React Einführung verkleidet

Dieses Dokument setzt voraus, dass der Leser bereits eine Webseite mit HTML, CSS und JavaScript geschrieben hat.

## Warum auf mich hören?

Es gibt jede Menge widersprüchliche Empfehlungen und Best Practices zu React da draußen - warum solltest du auf mich hören?

Ich war Mitglied des ursprünglichen Teams bei Facebook, das React gebaut und als Open-Source veröffentlicht hat. Mittlerweile arbeite ich nicht mehr bei Facebook, sondern bei einem kleinen Startup, wodurch ich auch die Perspektive von außerhalb Facebooks kenne.

## Wie man ins React Ökosystem reinkommt

Alle Software baut auf einem bestimmten Technologie-Stack auf, den man hinreichend gut genug beherrschen muss, um seine Anwendung bauen zu können. Der Grund, warum das Ökosystem von React-Tools leicht überwältigend wirkt, ist, dass es bislang in der falschen Reihenfolge erklärt wurde.

Du solltest React und seine Tools in folgender Reihenfolge lernen - **ohne nach vorne zu springen oder mehrere der Teile gleichzeitig zu lernen**:

* [React selbst](#react-selbst-lernen)
* [`npm`](#npm-lernen)
* [JavaScript „Bundler“](#javascript-bundler-benutzen-lernen)
* [ES6](#es6-lernen)
* [Routing](#routing-lernen)
* [Flux](#flux-lernen)

**Du musst nicht alle Themenblöcke lernen um React produktiv einsetzen zu können.** Schau dir den nächsten Themenblock erst an, wenn du im aktuellen Probleme hast, die du mit den bestehenden Mitteln nicht lösen kannst.

Des weiteren gibt es ein paar Themen, die in der React-Community viel diskutiert werden, die „bleeding edge“ sind. Die folgenden Themen sind interessant, aber schwer zu verstehen und viel weniger verbreitet als die eben genannten. **Für die meisten Anwendungen sind sie nicht notwendig.**

* [Inline Styles](#inline-styles-lernen)
* [Serverseitiges Rendern](#serverseitiges-rendern-lernen)
* [Immutable.js](#immutablejs-lernen)
* [Relay, Falcor etc.](#relay-falcor-etc-lernen)

## React selbst lernen

Es ist ein weitverbreiteter Irrglaube, dass man erstmal viel Zeit damit verbringen muss das Tooling um React aufzusetzen, bevor man React lernen kann. In der offiziellen Dokumentation gibt es ein [HTML template](https://facebook.github.io/react/docs/getting-started.html#quick-start-without-npm), mit dem ihr arbeiten und direkt loslegen könnt. **Ihr braucht keine Tools für diesen ersten Schritt und ihr solltet nicht anfangen Tools zu lernen bevor ihr mit den Grundlagen von React vertraut seid.**

Ich finde nach wie vor, der einfachste Weg React zu lernen ist, das [offizielle Tutorial](https://facebook.github.io/react/docs/tutorial.html) durchzugehen.

## `npm` lernen

`npm` ist der Node.js Paketmanager und die populärste Lösung mit der Frontendler und Designer JavaScript Code miteinander teilen. Es umfasst ein Modulsystem namens `CommonJS` und erlaubt es Kommandozeilentools, die in JavaScript geschrieben wurden zu installieren. [Dieser Artikel](http://0fps.net/2013/01/22/commonjs-why-and-how/) erklärt die Hintergründe warum `CommonJS` für Browser notwendig ist. Im [CommonJS Spec Wiki](http://wiki.commonjs.org/wiki/Introduction) gibt es mehr Informationen zur `CommonJS` API.

Die meisten wiederverwendbaren Komponenten, Bibliotheken und Tools im React Ökosystem sind als `CommonJS`-Module verfügbar und werden mit `npm` installiert.

## JavaScript Bundler benutzen lernen

Aus mehreren wichtigen technischen Gründen können `CommonJS`-Module, also alle `npm`-Module, nicht nativ in Browsern benutzt werden. Man braucht daher einen sogenannten JavaScript „Bundler“, der diese Module in einzelne `.js`-Dateien „bundlet“, die dann via `<script>`-Tag in Webanwendungen integriert werden können.

Beispiele für JavaScript Bundler sind u.a. `Webpack` und `Browserify`. Beide sind gute Alternativen, aber ich bevorzuge `webpack`, da es viele Features hat, die das entwickeln von großen Anwendungen leichter machen. Da die offizielle Dokumentation etwas verwirrend sein kann, habe ich ein [Plug & Play Startertemplate](https://github.com/petehunt/react-webpack-template) gebaut und ein [Webpack Howto](https://github.com/petehunt/webpack-howto) für komplexere Anwendungsfälle geschrieben.

Wichtiger Hinweis: `CommonJS` benutzt die `require()`-Funktion, um Module zu importieren. Viele glauben, dass diese Funktion etwas mit dem `require.js` Projekt zu tun haben muss. Aus mehreren technischen Gründen würde ich euch nahelegen auf `require.js` zu verzichten. Es ist außerdem nicht sehr populär im React Ökosystem.

## ES6 lernen

Neben JSX, das ihr im React Tutorial gelernt habt, kann euch noch andere merkwürdige Syntax in React Beispielcode begegnen. Sie kommt aus ES6, was die neueste Version von JavaScript ist, die ihr vielleicht noch nicht kennt. Da sie noch sehr neu ist, wird sie von Browsern noch nicht unterstützt, aber euer Bundler kann sie mit der richtigen Konfiguration für euch übersetzen.

Wenn ihr einfach nur mit React loslegen wollt **könnt ihr ES6 lernen überspringen**, oder es beiläufig lernen während ihr eure React Anwendungen baut.

Womöglich wird euch gesagt, dass ES6 Klassen jetzt der neue Standardweg sein sollen React-Komponenten zu schreiben. Das ist nicht wahr. Die meisten Leute (inklusive Facebook) benutzen weiterhin `React.createClass()`.

## Routing lernen

„Single-page Applications“ sind gerade der letzte Schrei. Sie sind Webseiten die nur einmal geladen werden und wenn der Nutzer auf einen Link oder Button klickt, sorgt das JavaScript das auf der Seite läuft dafür, dass die URL in der Adresszeile aktualisiert wird ohne dass die Seite refresht wird. Das Verwalten der URL in der Adresszeile wird vom sogenannten **Router** übernommen.

Der beliebteste Router im React Ökosystem ist der [react-router](https://github.com/rackt/react-router). Wenn ihr eine Single-page Application schreibt, solltet ihr ihn nutzen - außer ihr habt einen triftigen Grund, der dagegen spricht. 

**Ihr solltet keinen Router benutzen, wenn ihr keine Single-page Application schreibt.** Die meisten Projekte beginnen ohnehin als kleinere Komponenten, die in größere Anwendungen eingebettet sind.

## Flux lernen

Ihr habt wahrscheinlich schon von Flux gehört. Es wird **jede Menge** Falsches über Flux gesagt.

Viele Leute beginnen ihre App zu bauen und glauben, sie brauchen Flux, um ihr Datenmodell zu definieren. **Das ist nicht der richtige Weg, um in Flux einzusteigen. Flux sollte man erst hinzufügen, wenn man bereits viele Komponenten gebaut hat.**

React-Komponenten sind hierarchisch angeordnet. Meistens folgt euer Datenmodell auch einer Hierarchie. In solchen Situationen bringt Flux nicht so viel. Manchmal allerdings, ist das Datenmodell nicht hierarchisch. Wenn ihr anfangt euren React-Komponenten `props` zu übergeben, die für sie belanglos sind, oder wenn ihr ein paar wenige Komponenten habt, die sehr komplexer werden, dann solltet ihr euch Flux genauer anschauen.

**Wenn ihr Flux braucht merkt ihr das von selbst. Wenn ihr zweifelt, ob ihr es braucht, dann braucht ihr es nicht.**

Wenn ihr euch entschieden habt Flux zu nutzen: [Redux](http://redux.js.org/) ist die populärste und bestdokumentierte Flux-Bibliothek, die es gibt. Es gibt _viele_ Alternativen und ihr werdet versucht sein euch viele davon anzuschauen und zwischen ihnen abzuwägen. Mein Tipp ist, einfach die populärste zu nehmen.

## Inline Styles lernen

In der Zeit vor React haben viele Leute CSS Styles wiederverwendbar gemacht mithilfe komplizierter Stylesheets, die von CSS-Präprozessoren wie SASS erstellt wurden. Da es React einfach macht, wiederverwendbare Komponenten zu schreiben, kann euch das helfen weniger kompliziertes CSS zu schreiben. Viele in der Community, darunter auch ich, experimentieren mit verschiedenen Lösungen, die Stylesheets ganz abschaffen.

Aus mehreren Gründen ist das eine ziemlich verrückte Idee. Media Queries werden schwieriger und es gibt mögliche Performanceeinschränkungen. **Wenn ihr mitten im React-Einstieg steckt, stylet alles wie ihr es bisher immer getan habt.**

Sobald ihr ein Gefühl dafür bekommen habt wie React funktioniert, könnt ihr euch nach Alternativen umschauen. Eine beliebte davon ist [BEM](https://en.bem.info). Ich empfehle, euer CSS immer weniger von einem CSS-Präprozessor bauen zu lassen, da React eine bessere Lösung bietet Styles wiederzuverwenden - durch wiederverwendbare Komponenten - und da euer JavaScript Bundler effizientere Stylesheets für euch generieren kann (hierzu habe ich [einen Vortrag bei der OSCON](https://www.youtube.com/watch?v=VkTCL6Nqm6Y) gehalten). Ansonsten funktioniert React, wie jede JavaScript Bibliothek, natürlich hervorragend mit CSS-Präprozessoren.

Alternativ könnt ihr auch [CSS Modules](http://glenmaddern.com/articles/css-modules) nutzen, oder genauer [react-css-modules](https://github.com/gajus/react-css-modules). Mit CSS Modules schreibt ihr wie gewohnt CSS (oder Sass/LESS/Stylus) aber ihr könnt trotzdem eure CSS-Dateien wie React Inline Styles verwalten und zusammenstellen. Und ihr müsst euch dabei keine Sorgen darum machen eure Klassennamen mit Methodologien wie BEM einmalig zu halten - CSS Modules sorgen mit ihrem Modulsystem für euch hinter den Kulissen dafür.

## Serverseitiges Rendern lernen

Serverseitiges Rendern wird oft "universelles" oder "isomorphes" JavaScript genannt, was soviel heißt wie, dass eure React Komponenten vom Server zu statischem HTML gerendert werden. Dies verbessert die Initialisierungsgeschwindigkeit, da der Nutzer nicht warten muss bis JavaScript fertig heruntergeladen wurde bevor er die initiale Nutzeroberfläche sehen kann. React kann das serverseitig gerenderte initiale HTML nutzen und muss es nicht auf dem Client generieren.

Ihr braucht serverseitiges Rendern, wenn eure initialen Renderzeiten zu langsam werden oder wenn ihr euren Suchmaschinenrang verbessern wollt. Obwohl Google mittlerweile clientseitig gerenderte Inhalte mitindiziert, so fiel zumindest bis Januar 2016 bei jeder Analyse auf, dass diese Inhalte weniger gut gerankt werden als serverseitige - vermutlich wegen der Performanceeinbußen, die clientseitiges Rendern mit sich bringt.

Serverseitiges Rendern erfordert noch viele Tools, um es richtig aufzusetzen. Da es deutlich React-Komponenten unterstützt, die geschrieben wurden, ohne an serverseitiges Rendern zu denken, solltet ihr zunächst mal eure App schreiben und euch dann um serverseitiges Rendern kümmern. Ihr werdet nicht all eure Komponenten umschrieben müssen, um es zu unterstützen.

## Immutable.js lernen

[Immutable.js](https://facebook.github.io/immutable-js/) bietet eine Menge von Datenstrukturen, die helfen können bestimmte Performanceprobleme von React Anwendungen zu lösen. Es ist eine großartige Bibliothek, die ihr wahrscheinlich in Zukunft viel in euren Apps verwenden werdet, aber sie ist vollkommen unnötig bis ihr einen Sinn für die Performanceauswirkungen gewonnen habt.

## Relay, Falcor etc. lernen

Sind Technologien, die euch helfen die Zahl der AJAX-Requests zu reduzieren. Sie sind noch sehr brandneu. Wenn ihr keine Probleme mit zu vielen AJAX-Requests habt braucht ihr Relay und Falcor nicht.
