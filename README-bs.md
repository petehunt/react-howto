# react-howto

Ako niste upoznati s Reactom (ili s frontendom generalno), ovaj ekosistem će vam se činiti zbunjujućim. Ovo su neki od razloga

* React je prethodno bio meta ranih usvojitelja i eksperta
* Facebook stavlja open-source samo one projekte koje stvarno koristi, tako da nije fokus na projekte koji su manji od Facebooka
* Mnogo je lošeg sadržaja zamaskiranog kao React uputstvo

Kroz ovaj dokument, pretpostavit ću da ste već pravili web stranice koristeći HTML, CSS i JavaScript.

## Zašto da slušate mene?

Mnogo je savjeta i uputstava za React; zašto poslušati mene?

Bio sam jedan od prvobitnih članova Facebook tima koji je napravio React. Nisam više u Facebook-u, nego sam član jednog malog startupa, tako da imam i tu non-Facebook perspektivu.

## Kako započeti u React ekosistemu

Sav software je napravljen na steku tehnologija, i potrebno je razumijeti dovoljno tog steka da napravite vašu aplikaciju. Razlog zašto Reactov ekosistem alata izgleda preobiman je zato što je uvijek objašnjavan u pogrešnom redoslijedu.

Trebate učiti po ovom redoslijedu, **bez preskakanja ili istovremenog učenja**:

* [React](#react)
* [`npm`](#npm)
* [JavaScript “bundler”-i](#javascript-bundleri)
* [ES6](#es6)
* [Rutiranje](#rutiranje)
* [Flux](#flux)

**Ne trebate učiti svaku od ovih da biste bili produktivni s Reactom.** Samo ako imate problem koji trebate riješiti, tada pređite na sljedeći korak.

Dodatno, postoje još neke teme spomenute u React zajednici koje su u trendu. Te teme su interesantne ali su dosta teške za razumijeti, manje su popularne od gore navedenih tema i **nisu potrebne za većinu aplikacija**.
* [Inline stilovi](#inline-stilovi)
* [Server rendering](#server-rendering)
* [Immutable.js](#immutablejs)
* [Relay, Falcor, itd](#relay-falcor-itd)

## React

Generalno, pogrešno je shvatanje da je potrebno dosta vremena izgubiti za uspostavljanja alata da bi počeli učiti React. U oficijelnoj dokumentaciji naći ćete [copy-paste HTML templejt](https://facebook.github.io/react/docs/getting-started.html#quick-start-without-npm) kojeg možete spasiti kao`.html` fajl i možete početi s tim raditi. **Nikakvi alati nisu potrebni za ovaj korak, i ne treba početi učiti neke dodatne alate dok niste upoznati s osnovama Reacta.**

Mišljenja sam da je najjednostavniji način da naučite React preko [zvaničnog tutorijala](https://facebook.github.io/react/docs/tutorial.html).

## `npm`

`npm` je Node.js-ov package menadžer i najpopularniji način za front-end inžinjere i dizajnere da dijele JavaScript kod. Uključuje modul sistem pod imenom `CommonJS` i instalira alat za komandni prompt napisan u JavaScriptu. Pročitajte [ovaj članak](http://0fps.net/2013/01/22/commonjs-why-and-how/) za više o tome zašto je `CommonJS` potreban za web-pretraživače, ili [CommonJS Wiki](http://wiki.commonjs.org/wiki/Introduction) za informacije o `CommonJS` API-u.

Većina iskoristivih komponenti, biblioteka i alata u Reactu su dostupni kao `CommonJS` moduli i instaliraju se pomoću `npm`-a.

## JavaScript bundleri

Zbog dosta tehničkih razloga `CommonJS` moduli ne mogu biti korišteni nativno u browseru. Potreban vam je JavaScript “bundler” da "sveže" te module u `.js` fajlove koje možete uključiti u vašoj web stranici sa `<script>` tagom.

Primjeri JavaScript bundlera uključuju `webpack` i `browserify`. Oba su dobre opcije, ali preferiram `webpack` zbog velikog broja feature-a koji čine development velikih aplikacija lakšim. Dokumentacija mu je ponekad komplikovana, imam [plug-and-play templejt za početnike](https://github.com/petehunt/react-webpack-template) i napisao sam [how-to uputstvo za webpack](https://github.com/petehunt/webpack-howto) za kompleksnije upotrebe.

React takođe pruža [zvanični CLI alat zvani Create React App](https://github.com/facebookincubator/create-react-app). Omogućuje vam da napravite vaše React projekte s `webpack`-om bez ikakve konfiguracije. Ima svoja ograničenja, ali dobro služi kao početna tačka, i stalni update-i će dodavati više opcija s vremenom. Također, pruža opcija "ejection" koja kopira sve konfiguracije i zavisnosti u vaš projekat, tako da imate potpunu kontrolu nad njima.

Jednu stvar treba imati na umu: `CommonJS` koristi `require()` funkciju da importuje module, pa se dosta ljudi zbuni i misli da je to zbog projekta pod imenom `require.js`. Zbog dosta tehničkih razloga, preporučujem da se klonite `require.js`-a. Također, nije popularno u React ekosistemu.

## ES6

Izvan JSX-a (kojeg ste naučili u React tutorijalu), možete naći neke čudne sintakse u React primjerima. To se zove ES6, i to je zadnja verzija JavaScripta, tako da postoji mogućnost da ga još niste naučili. Pošto je još novo, nije podržano u svim browserima, ali ga bundler može prevesti za vas sa odgovarajućom konfiguracijom.

Ako želite da uradite nešto s Reactom, **možete preskočiti učenje ES6**, ili početi da ga učite usput.

Možda ste slušali neku priču o ES6 klasama kao preferirani način kreiranja React komponenti. To nije istina. Većina ljudina (uključujući Facebook) koriste `React.createClass()`.

## Rutiranje

“Single-page aplikacije” su jako popularne ovih dana. To su web stranice koje se jednom učitaju, i kada korisnik klikne na link ili dugme, JavaScript ažurira adresnu traku, ali se stranica ne refrešuje. To se postiže takozvanim **routerom**.

Najpopularniji router u React ekosistemu je [react-router](https://github.com/rackt/react-router). Ako pravite single-page aplikaciju, koristite ga, osim ako imate dobar razlog da ga ne koristite.

**Ne koristite router ako ne pravite single-page aplikaciju**. Svakako većina projekata počinju kao manje komponente unutar velikih aplikacija.

## Flux

Vjerovatno ste čuli za Flux. Postoji *tona* pogrešnih informacija o Fluxu.

Dosta ljudi počne praviti aplikaciju i kada žele da definišu model podataka, misle da im je potreban Flux za to. **To je pogrešan način za korištenje Fluxa. Flux treba dodati tek kada je dosta komponenti već napravljeno.**

React komponente su složene u hijerarhiju. Većinom, model podataka prati neku hijerarhiju. U takvim situacijama Flux ne pomaže mnogo. Ponekad, vaš model podataka nije hijerarhijalan. Kada React počinje da dobija `props`-e koji su strani, ili imate manji broj komponenti koji postaju kompleksniji, tada bi trebali da koristite Flux.

**Znat ćete kada vam bude potreban Flux. Ako niste sigurni da vam treba, tada vam sigurno ne treba.**

Ako ste se odlučili da koristite Flux, najpopularnija i najbolje dokumentovana Flux biblioteka je [Redux](http://redux.js.org/). Postoji *mnogo* alternativa, i sigurno ćete htjeti da pokušate neke od njih, ali moj je savjet da koristite najpopularniju.

## Inline stilovi

Prije Reacta, dosta developera je ponovno iskorištavalo CSS stilove sa komplikovanim stilovima generisanih pretprocesorima kao što su SASS. Pošto React čini pisanje ponovo iskoristivih komponenti veoma lakim, vaši CSS fajlovi će biti manje komplikovani. Mnogi u zajednici (uključujući i mene) eksperimentišu idejom uklanjanja CSS fajlova u potpunosti.

Ovo je suluda ideja zbog mnogo razloga. Ono čini media upite mnogo težima, i moguće je da postoje  ograničenja s performansama koristeći tu tehniku. **Kada počinjete s Reactom, radite stilove kao što ste inače radili.**

Nakon što steknete malo osjećaja s načinom rada Reacta, možete pogledati neke od alternativnih tehnika. Najpopularnija je [BEM](https://en.bem.info/). Preporučujem da ukinete vaš CSS pretprocesor, pošto vam React nudi moćniji način korištenja stilova (ponovnim iskorištavanjem komponenti) i vaš JavaScript bundler može efikasnije generisati CSS za vas (o čemu sam pričao [na OSCON-u](https://www.youtube.com/watch?v=VkTCL6Nqm6Y)). Na kraju, React, kao i svaka druga JavaScript biblioteka, funkcionisat će bez problema i sa nekim od CSS pretprocesora.

Alternativno, možete koristiti [CSS Module](http://glenmaddern.com/articles/css-modules), ili specifičnije, [react-css-modules](https://github.com/gajus/react-css-modules). Sa CSS Modulima možete i dalje pisati vaš CSS (ili SASS/LESS/Stylus), ali takođe možete i pisati vaše CSS fajlove kao inline stilove u Reactu. Ne trebate da brinete o imenima vaših klasa koristeći metodologije kao što su BEM, jer će to biti riješeno od strane modul sistema.

## Server rendering

Server rendering je često nazivan "univerzalni" ili "izomorfni" JS. To znači da možete uzeti vaše React komponente i renderirati ih u statični HTML na serveru. Ovo poboljšava inicijalni performans jer korisnik ne mora da čeka da se JS snimi da bi vidio inicijalni UI, i React može da iskoristi serverski izrenderirani HTML tako da ne mora da ga generiše na klijentskoj strani.

Server rendering je potreban ako primjetite da je inicijalno renderiranje presporo ili ako hoćete da poboljšate rangiranje na pretraživačima. Iako je istina da Google sada indeksira i klijentski izrenderiran sadržaj, od Januara 2016te svaki put nakon testiranja je dokazano da lošije utiče na rangiranje, najviše zbog klijentski renderiranog sadržaja.

Server rendering zahtijeva i dalje dosta da se napravi da bude dobro. Prvo napravite vašu aplikaciju, pa kasnije brinite od serverskom renderiranju. Nećete biti potrebe da sve komponente prepravljate da bi to podržavale.

## Immutable.js

[Immutable.js](https://facebook.github.io/immutable-js/) pruža set struktura podataka koji pomažu u rješavanju određenih problema s performansom kod buildanja React aplikacija. Odlična je biblioteka, i vjerovatno ćete je dosta koristiti u vašim aplikacijama, ali je potpuno bespotrebno dok god ne budete imali problema s performansama.

## Relay, Falcor, itd.

Ovo su tehnologije koje vam pomažu da reducirate broj AJAX poziva. Ako nemate problem sa previše AJAX poziva, neće vam trebati Relay ili Falcor.
