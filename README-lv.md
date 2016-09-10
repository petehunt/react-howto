# react-howto

Ja jūs tikai sākat apgūt React (vai frontendu kopumā), tad šī ekosistēma, var jums likties samērā mūlsinoša. Tam ir vairāki iemesli:

* Vēsturiski React mērķauditorija bija eksperti un šīs ekosistēmas agrīnie sekotāji
* Facebook atver pirmkodu tikai tiem resusriem, kas tiek izmantoti šīs kompānijas ietvaros, tādējādi kompānija nefokusējas uz to rīku izstrādi, kas paredzēti mazākiem projektiem kā Facebook
* Tīklā atrodamas daudzas sliktas kvalitātes React rokasgrāmatas

Šī dokumenta ietvaros, es pieņemu, ka jums ir pieredze tīmekļa vietņu izstrādē, izmantojot HTML, CSS un JavaScript.

## Kāpēc jums būtu manī jāklausās?

Visapkārt ir daudz un dažādu konfliktējošu ieteikumu sakarā ar React; Kāpēc gan klausīties manī?

Es biju viens no sākotnējiem Facebook komandas biedriem, kas izstrādāja un publiskoja React. Es vairs nestrādāju Facebook un šobrīd es darbojos mazā jaunuzņēmumā, tādējādi uz šo visu man ir arī ne-Facebook skatījums.

## Kā apgūt React ekosistēmu?

Jebkurš programnodrošinājums ir izstrādāts pamatojoties uz kāda noteikta tehnoloģiju steka, tāpēc jums ir nepieciešams apgūt pietiekami daudz šī steka satura, lai jūs paši spētu izstrādāt lietojumus. Iemesls, kāpēc React ekosistēma liekas tik milzīga ir tas, ka tā vienmēr tiek izskaidrota nepareizā kārtībā.

Jums būtu jāmācās, lūk šādā kārtībā, **neko neizlaižot un nemācoties vairākas lietas vienlaicīgi**:

* [React apguve](#react-apguve)
* [`npm`](#npm-apguve)
* [JavaScript “bundlers” (pakotāji)](#javascript-pakotāju-apguve)
* [ES6](#es6-apguve)
* [Maršrutēšana](#maršrutēšanas-apguve)
* [Flux](#flux-apguve)

**Jums nav jāapgūst viss no šī, lai būtu produktīvi izmantojot React.** 
Pārejiet pie nākamā soļa tikai tad, kad Jums ir problēma, kuru tas risina.

Kā arī, React kopienā ir dažas tēmas, kuras ir "super-mūsdienīgas prakses" ("bleeding edge"). Šīs tēmas ir interesantas, taču ar tām ir sarežģītāk tikt skaidrībā, salīdzinot ar tām, kas ir pieminētas augstāk, kā arī **izstrādājot vairumu lietojumu, tās nav nepieciešamas**
* [Iekļautie stili](#ekļauto-stilu-apguve)
* [Renderēšana servera pusē](#renderēšana-servera-pusē)
* [Immutable.js](#immutablejs-apguve)
* [Relay, Falcor, utt.](#relay-falcor-utt-apguve)

## React apguve

Pastāv maldīgs uzskats, ka ir jāvelta daudz laika, lai uzstādītu visus nepieciešamos rīkus, lai varētu uzsākt React apguvi. Oficiālajā dokumentācijā, jūs atradīsiet [copy-paste HTML veidni](https://facebook.github.io/react/docs/getting-started.html#quick-start-without-npm), ko jūs varēsēsiet saglabāt kā `.html` failu un spēsiet uzreiz uzsākt to apgūt. **Šim solim nav nepieciešami nekādi rīki, un neturpiniet mācīties jaunus rīkus, līdz jūs būsiet pārliecināti par savām zināšanām React pamatos.**

Es joprojām uzskatu, ka vieglākais veids, kā apgūt React ir [oficiālā rokasgrāmata](https://facebook.github.io/react/docs/tutorial.html).

## NPM apguve

`npm` ir Node.js pārvaldnieks, un tas ir vispopulārākais veids, kādā front-end izstrādātāji un dizaineri dalās ar JavaScript kodu. Tas iekļauj moduļu sistēmu `CommonJS` un ļauj jums instalēt komandrindas rīkus, kas izstrādāti izmantojot JavaScript. Lasiet [šo rakstu](ttp://0fps.net/2013/01/22/commonjs-why-and-how/), lai gūtu pamata zināšanas par to, kāpēc `CommonJS` ir nepieciešams pārlūkiem, vai [CommonJS Spec Wiki](http://wiki.commonjs.org/wiki/Introduction), kur atrodas sīkāka informācija par `CommonJS` API.

Lielākā daļa pakešu, rīku un komponenšu React ekosistēmā ir pieejamas kā `CommonJS` moduļi un tiek instalēti izmantojot `npm`.

## JavaScript pakotāju apguve

Vairāku tehnisku iemeslu dēļ `CommonJS` moduļi (tas ir viss, kas ir iekš `npm`) nevar tikt izmantoti pa tiešo pārlūkā. Tādēļ jums ir nepieciešams izmantot JavaScript pakotāju “bundler”, lai varētu iepakot šos moduļus `.js` failos, kurus jūs varēsiet iekļaut savā tīmekļa lapā izmantojot `<script>` tagu.

`Webpack` un `browserify` ir JavaScript pakotāji. Abi ir labas izvēlas, taču es dotu priekšroku `webpack`, tā kā tam ir vairākas īpašības, kas padara lielu lietojumu izstrādi vienkāršāku. Tā dokumentācija var būt mūlsinoša, taču man ir [viedne ātram startam](https://github.com/petehunt/react-webpack-template) un es esmu uzrakstījis [how-to-rokasgrāmatu priekš webpack](https://github.com/petehunt/webpack-howto), kur tiek izskatīti sarežģītāki gadījumi.

Viena lieta ir jāpatur prātā: `CommonJS` izmanto `require()` funkciju, lai importētu moduļus, šīs funkcijas dēļ cilvēki beiži vien apmūlst, jo domā, ka tai ir kāda darīšana ar projektu, kas saucas `require.js`. Vairāku tehnisku iemeslu dēļ, es ieteiktu izvairīties no `require.js`. Kā arī šis projekts nav populārs React ekosistēmā.

## ES6 apguve

Neskaitot JSX (ko jūs apguvā React rokasgrāmatā), jūs varat sastapt jocīgu sintaksi React piemēros. To sauc par ES6, un tā ir jaunākā JavaScript versija, kuru, iespējams, jūs vēl neesat apguvuši. Tā kā šī versija ir tik jauna, ne visi pārlūki to atbalsta, taču jūsu pakotājs to var translēt jūsu vietā, izmantojot noteiktu konfigurāciju.

**Jums nav nepieciešams apgūt ES6, lai varētu izstrādāt lietojumus, izmantojot React**, jūs varat to apgūt arī vēlāk.

Jūs noteikti esat dzirdējuši dažādas runas par to, ka jums būtu jādod priekšroka ES6 klasēm, lai izstrādātu React komponentes. Tā nav taisnība. Lielākā daļa cilvēku (ieskaitot Facebook) izmanto `React.createClass()`.

## Maršrutēšanas apguve

“Vienas lapas lietojumi” (Single-page applications vai SPA) - ir mūsdienīgs trends. Pastāv lapas, kas tiek ielādētas vienreiz, un tad, kad lietotājs noklikšķina uz saites vai pogas, JavaScript, kas darbojas lapā, atjaunina adreses joslu, taču pati lapa netiek pārlādēta. Adreses joslas pārlāde tiek nodrošināta izmantojot **maršrutētāju**.

Vispopulārākais maršrutētājs React ekosistēmā ir [react-router](https://github.com/rackt/react-router). Ja jūs izstrādājat vienas lapas lietojumu, tad cenšaties to izmantot, ja vien jums nav kāds labs iemesls to nedarīt.

**Neizmantojiet maršrutētāju, ja jūs neizstrādājat vienas lapas lietojumu**.
Lielākā daļa projektu tiek radīti sākot ar mazām komponentēm iekš pastāvoša liela lietojuma.

## Flux apguve

Jūs noteikti esat dzirdējuši par Flux. Pastāv *daudz* maldīgas informācijas par Flux.

Liela daļa cilvēku cenšas izlemt par labāko datu modeli un uzskata, ka lai to izstrādātu tiem ir nepieciešams Flux. **Tas ir nepareizs veids kā iekļaut Flux. Par Flux ir jāsāk domāt tikai tad, kad vairākas komponentes jau ir izstrādātas**

React komponentes tiek izkārtotas hierarhijā. Lielākoties, jūsu datu modelis arī seko kādai noteiktai hirerhijai. Šajās situācijās, Flux nedod jums daudz pievienotās vērtības. Taču, dažkārt, jūsu datu modelis nav hierarhisks. Kad jūsu React komponentes sāk saņemt `props`, kas var likties "ārēji", vai arī tad, kad jums ir mazs komponenšu skaits un tās sāk palikt diezgan sarežģītas, tad tas varētu būt gana labs iemesls, lai jūs iepazītos ar Flux.

**Jūs zināsiet, kad jums būs nepieciešams Flux. Ja jūs neesat pārliecināti, vai tas jums ir vajadzīgs, tad jums tas nav vajadzīgs.**

Ja jūs tomēr esat nolēmuši lietot Flux, tad vispopulārākā un vislabāk dokumentētā Flux bibliotēka ir [Redux](http://redux.js.org/). Tam pastāv *daudz* un dažādas alternatīvas, un jums var likties vilinoši daudzas no tām salīdzināt, taču es iesaku izvēlēties vispopulārāko un to izmantot.

## Iekļauto stilu apguve

Prims React, vairums cilvēku lietoja CSS-preprocessorus, piemēram, SASS, lai varētu pārizmantot stilus. React padara pārizmantojamu kopmonenšu izstrādi vienkāršu, tādējādi stilu izstrāde var būt mazāk sarežģīta. Daudzi no kopienas (ieskaitot mani) veic eksperimentus, lai nākotnē varētu tikt vaļā no CSS pavisam.

Tā ir samērā traka ideja, vairāku iemeslu dēļ. Tā sarežģī media vaicājumu (media queries) izstrādi, kā arī, iespējams, izmantojot šo metodoloģiju, pastāv arī veiktspējas ierobežojumi. **Ja jūs tikai sākat darbu ar React, tad turpiniet rakstīt css-stilus tā, kā esat raduši.**

Kad jūs būsiet izjutuši to, kā React darbojas, jūs varat apskatīt alternatīvas pieejas. Viena no populārākajām ir [BEM](https://en.bem.info/). Es ieteiktu izvairīties no CSS-preprocessoriem, tā kā React piedāvā lokanāku pieeju stilu pārizmantošanā (pārizmantojot komponentes), kā arī tādējādi jūsu JavaScript pakotājs būs spējīgs ģenerēt efektīvākas stilu tabulas priekš jums ([Mana runa par šo tēmu OSCON konferencē](https://www.youtube.com/watch?v=VkTCL6Nqm6Y)). Līdz ar to, React, kā jau jebkura cita JavaScript bibliotēka, strādās labi arī ar CSS-preprocessoru.

Alternatīvi,  jūs varat arī izmantot [CSS moduļus](http://glenmaddern.com/articles/css-modules), konkrētāk [react-css-modules](https://github.com/gajus/react-css-modules). Ar CSS moduļiem jūs joprojām varat rakstīt CSS (vai SASS/LESS/Stylus), taču jūs varēsiet pārvalīdīt savus CSS failus līdzīgi, kā to darītu ar iekļautajiem stiliem izmantojot React. Kā arī jums nav nepieciešams uztraukties par to, kā saukt CSS klases, izmantojot tādas metodoloģijas kā BEM, jo to pārvaldīs moduļu sistēma jūsu vietā.

## Renderēšana servera pusē

Renderēšana servera pusē, bieži tiek saukta par "universālu" vai "izomorfisku" JS. Tas nozīmē, ka jūs varat paņemt savas React komponentes un renderēt tās par statusku HTML servera pusē. Tas uzlabo sākotnējo lapas ielādi, jo tādā veidā, lietotājam nav nepieciešams gaidīt, kamēr JS tiks ielādēts, lai redzētu sākotnējo lietotāja interfeisu, kā arī React var pārizmantot servera pusē renderēto HTML, tādā veidā tam nav nepieciešams to ģenerēt lietotāja pusē.

Jums ir nepieciešama servera puses renderēšana, ja jūs manat, ka jūsu pirmreizējā renderēšana ir pārāk lēna, vai arī, ja jūs vēlaties veikt SEO (meklētājprogrammas optimizāciju). Kautgan, Google tagad ir spējīgs indeksēt lietotāja pusē renderētu saturu, ir pierādīts, ka līdz ar 2016. gada mērijumiem, satura renderēšana lietotāja pusē joprojām negatīvi ietekmē ranžēšanu, potenciāli dēļ lēnās renderēšanas lietotāja pusē.

Lai panāktu renderēšanu servera pusē ir nepieciešama tās "pareiza" realizācija izmantojot daudzus rīkus. Tā kā, React komponenšu izstrādes rīki ir izstrādāti neturot prātā problēmas, kas saistītas ar renderēšanu servera pusē, ieteicams sākumā izstrādāt lietojumu un satraukties par renderēšanu servera pusē tikai pēc tam. Jums nebūs nepieciešams pārrakstīt visas jūsu komponentes, lai varētu to ieviest.

## Immutable.js apguve

[Immutable.js](https://facebook.github.io/immutable-js/) piedāvā datu struktūru kopumu, kas var palīdzēt atrisināt noteiktas problēmas saistītas ar veiktspēju, izstrādājot React lietojumus. Tā ir brīnišķīga bibliotēka, un jums noteikt nāksies to izmantot nākotnē lietojumu izstrādē, taču tā absolūti nav nepieciešama, kamēr jūs nesastapsieties ar lietojuma veiktspējas problēmām.

## Relay, Falcor utt. apguve

Šīs tehnoloģijas palīdz jums samazināt AJAX pieprasījumu skaitu. Tās ir relatīvi eksperimentālas, tāpēc, ja jums nav problēmu, kas saistītas ar pārmērīgi daudziem AJAX izsaukumiem, jums nav nepieciešamības izmantot Relay vai Falcor.
