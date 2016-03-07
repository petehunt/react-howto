# react-howto

Ja jūs tikai sākat apgūt React (vai frontendu kopumā), tad šī ekosistēma, var jums likties samērā mūlsinoša. Tam ir vairāki iemesli:

* Vēsturiski React mērķauditorija bija eksperti un šīs ekosistēmas agrīnie sekotāji
* Facebook atver pirmkodu tikai tiem resusriem, kas tiek izmantoti šīs kompānijas ietvaros, tādējādi kompānija nefokusējas uz rīku izstrādi, kas paredzēta mazākiem projekties kā Facebook
* Tīklā atrodami daudzas sliktas kvalitātes React rokasgrāmatas

Šī dokumenta ietvaros, es pieņemu, ka Tev ir pieredze tīmekļa vietņu izstrādē, izmantojot HTML, CSS un JavaScript.

## Kāpēc Tev būtu manī jāklausās?

Visapkārt ir daudz un dažādu konfliktējošu ieteikumu par React; Kāpēc gan klausīties manī?

Es biju viens no sākotnējiem Facebook komandas biedriem, kas izstrādāja un publicēja React. Es vairs nestrādāju Facebook un šobrīd es darbojos mazā jaunuzņēmumā, tādējādi man arī ir ne-Facebook skatījums uz šo visu.

## Kā apgūt React ekosistēmu

Jebkurš programnodrošinājums ir izstrādāts uz tehnoloģiju steka, un Tev ir nepieciešams apgūt pietiekami daudz šī steka satura, lai Tu pats spētu izstrādāt programnodrošinājumu. Iemesls, kāpēc React rīku ekosistēma liekas tik milzīga ir tas, ka tā vienmēr tiek izskaidrota nepareizā kārtībā.

Tev būtu jāmācās, šajā kārtībā, **neko neizlaižot un nemācoties vienlaicīgi vairākas lietas**:

* [React apguve](#user-content-React-apguve)
* [`npm`](#user-content-NPM-apguve)
* [JavaScript “bundlers” (pakotāji)](#user-content-JavaScript-pakotāju-apguve)
* [ES6](#user-content-ES6-apguve)
* [Maršrutēšana](#user-content-Maršrutēšanas-apguve)
* [Flux](#user-content-Flux-apguve)

**Tev nav jāapgūst viss no šī, lai būtu produktīvs izmantojot React.** 
Pārejiet pie nākamā soļa tikai tad, ja Jums ir problēma, kuru tas risina.

Kā arī, React kopienā ir dažas tēmas, kuras ir "super-mūsdienīgas prakses" ("bleeding edge"). Šīs tēmas ir interesantas, taču ar tām ir sarežģītāk tikt ar tām skaidrībā, kā ar tām, kas pieminētas augstāk, un **izstrādājot lietojumu vairumu, tās nav nepieciešamas**
* [Iekļautie stili](#user-content-Iekļauto-stilu-apguve)
* [Renderēšana servera pusē](#user-content-Renderēšana-servera-pusē)
* [Immutable.js](#user-content-Immutablejs-apguve)
* [Relay, Falcor, utt.](#user-content-Relay-falcor-utt-apguve)

## React apguve

Pastāv maldīgs uzskats, ka ir jāpatērē daudz laika, lai uzstādītu visus nepieciešamos rīkus, lai varētu uzsākt React apguve. Oficiālajā dokumentācijā, Tu atradīsi [copy-paste HTML veidni](https://facebook.github.io/react/docs/getting-started.html#quick-start-without-npm), ko Tu varēsi saglabāt `.html` failā un spēsi uzreiz uzsākt to apgūt. **Šim solum nav nepieciešami nekādi rīki, un nesāc mācīties jaunus rīkus, līdz Tu būsi pārliecināts par savām zināšanām React pamatos.**

Es joprojām uzskatu, ka vieglākais veids, kā apgūt React ir [oficiālā rokasgrāmata](https://facebook.github.io/react/docs/tutorial.html).

## NPM apguve

`npm` ir Node.js pārvaldnieks, un tas ir vispopulārākais veids, kādā front-end izstrādātāji un dizaineri dalās ar JavaScript kodu. Tas iekļauj moduļu sistēmu `CommonJS` un ļauj Tev instalēt komandrindas rīkus, kas izstrādāti ar JavaScript. Lasi [šo rakstu](ttp://0fps.net/2013/01/22/commonjs-why-and-how/), lai gūtu pamata zināšanas, kāpēc `CommonJS` ir nepieciešams pārlūkprogrammām, vai [CommonJS Spec Wiki](http://wiki.commonjs.org/wiki/Introduction), kur atrodas vairāk informācijas par `CommonJS` API.

Lielākā daļa pakotņu, rīku un komponenšu React ekosistēmā ir pieejamas kā `CommonJS` moduļi un tiek instalēti izmantojot `npm`.

## JavaScript pakotāju apguve

Vairāku tehnisku iemeslu dēļ `CommonJS` moduļi (tas ir viss iekš `npm`) nevar tikt izmantots pa tiešo pārlūkprogrammā. Tādēļ Tev ir nepieciešams izmantot JavaScript pakotāju “bundler”, lai varētu iepakot šos moduļus `.js` failos, kurus Tu varēsi iekļaut savā tīmekļa lapā ar `<script>` tagu.

`Webpack` un `browserify` ir JavaScript pakotāji. Abi ir labas izvēlas, taču es dotu priekšroku `webpack`, tā kā tam ir vairākas īpašības, kas padara lielu lietojumu izstrādi vienkāršāku. Tā dokumentācija var būt mūlsinoša, taču man ir [viedne ātram startam](https://github.com/petehunt/react-webpack-template) un es esmu uzrakstījis [how-to-rokasgrāmatu priekš webpack](https://github.com/petehunt/webpack-howto), kur tiek izskatīti sarežģītāki gadījumi.

Viena lieta ir jāpatur prātā: `CommonJS` izmanto `require()` funkciju, lai importētu moduļus, šīs funkcijas dēļ cilvēki mūlst, jo domā, ka tai ir kāda darīšana ar projektu, kas saucas `require.js`. Vairāku tehnisku iemeslu dēļ, es ieteiktu izvairīties no `require.js`. Kā arī šis projekts nav populārs React ekosistēmā.

## ES6 apguve

Neskaitot JSX (ko Tu apguvi React rokasgrāmatā), Tu vari sastapt jocīgu sintaksi React piemēros. To sauc par ES6, un tā ir jaunākā JavaScript versija, kuru, iespējams, Tu vēl neesi apguvis. Tā kā šī versija ir tik jauna, ne visi pārlūki to atbalsta, taču Tavs pakotājs to var translēt tavā vietā, izmantojot noteiktu konfigurāciju.

**Tev nav nepieciešams apgūt ES6, lai varētu izstrādāt lietojumus, izmantojot React**, Tu vari to apgūt arī vēlāk.

Tu noteikti dzirdēsi dažādas runas par to, ka Tev būtu jādod priekšroka ES6 klasēm, lai izstrādātu React komponentes. Tā nav taisnība. Lielākā daļa cilvēku (ieskaitot Facebook) izmanto `React.createClass()`.

## Maršrutēšanas apguve

“Vienas lapas lietojumi” (Single-page applications vai SPA) - ir mūsdienīgs trends. Pastāv lapas, kas tiek ielādētas vienreiz, un tad, kad lietotājs noklikšķina uz saites vai pogas, JavaScript, kas darbojas lapā, atjaunina adreses joslu, taču pati lapa netiek pārlādēta. Adreses joslas pārbaldība tiek nodrošināta ar **maršrutētāju**.

Vispopulārākais maršrutētājs React ekosistēmā ir [react-router](https://github.com/rackt/react-router). Ja Tu izstrādā vienas lapas lietojumu, tad centies to izmantot, ja vien Tev nav kāds labs iemesls tā nedarīt.

**Neizmanto maršrutētāju, ja tu neizstrādā vienas lapas lietojumu**.
Lielākā daļa projektu tiek radīti sākot ar mazām komponentēm iekš pastāvoša liela lietojuma.

## Flux apguve

Tu noteikti esi dzirdējis par Flux. Pastāv *daudz* maldīgas informācijas par Flux.

Liela daļa cilvēku cenšas izlemt par labāku datu modeli un uzskata, ka lai to izstrādātu tiem ir nepieciešams Flux. **Tas ir nepareiz veids kā iekļaut Flux. Par Flux ir jāsāk domāt tikai tad, kad vairākas komponentes jau ir izstrādātas**

React komponentes tiek izkārtoti hierarhijā. Lielākoties, Tavs datu modelis arī seko kādai noteiktai hirerhijai. Šajās situācijās, Flux nedod Tev daudz pievienotās vērtības. Taču, dažkārt, Tavs datu modelis nav hierarhisks. Kad tavas React komponentes sāk saņem `props`, kas var likties "ārēji", vai arī kad, Tev ir mazs komponenšu skaits un tās sāk palikt diezgan sarežģītas, tad tas varētu būt gana labs iemesls iepazīties ar Flux.

**Tu zināsi, kad Tev būs nepieciešams Flux. Ja Tu neesi pārliecināts, vai tas Tev ir vajadzīgs, tad Tev tas nav vajadzīgs.**

Ja Tu esi izlēmis lietot Flux, tad vispopulārākā un vislabāk dokumentētā Flux bibliotēka ir [Redux](http://redux.js.org/). Tam pastāv *daudz* un dažādas alternatīvas, un Tev var likties vilinoši daudzas no tām salīdzināt, taču es iesaku izvēlēties vispopulārāko un to izmantot.

## Iekļauto stilu apguve

Prims-React, vairums cilvēku lietoja CSS-preprocessorus, piemēram, SASS, lai varētu pārizmantot stilus. React padara pārizmantojamu kopmonenšu izstrādi vienkāršu, tādējādi stilu izstrāde var būt mazāk sarežģīta. Daudzi no kopienas (ieskaitot mani) veic eksperimentus, lai nākotnē varētu tikt vaļā no CSS pavisam.

Tā ir samērā traka ideja, vairāku iemeslu dēļ. Tā sarežģī media vaicājumu (media queries) izstrādi, kā arī, iespējams, izmantojot šo metodoloģiju, pastāv arī veiktspējas ierobežojumi. **Ja Tu tikai sāc darbu ar React, tad turpini rakstīt css-stilus tā, kā esi radis.**

Kad jūs būsiet izjutuši to, kā React darbojas, jūs varat apskatīt alternatīvas pieejas. Viena no populārākajām ir [BEM](https://en.bem.info/). Es ieteiktu izvairīties no CSS-preprocessoriem, tā kā React piedāvā lokanāku pieeju stilu pārizmantošanā (pārizmantojot komponentes), kā arī tādējādi jūsu JavaScript pakotājs būs spējīgs ģenerēt efektīvākas stilu tabulas priekš jums ([mana runa par šo tēmu OSCON konferencē](https://www.youtube.com/watch?v=VkTCL6Nqm6Y)). Līdz ar to, React, kā jau jebkura cita JavaScript bibliotēka, strādās labi arī ar CSS-preprocessoru.

Alternatīvi,  jūs varat arī izmantot [CSS moduļus](http://glenmaddern.com/articles/css-modules), konkrētāk [react-css-modules](https://github.com/gajus/react-css-modules). Ar CSS moduļiem jūs joprojām varat rakstīt CSS (var CASS/LESS/Stylus), taču jūs varēsiet pārvalīdīt savus CSS failus līdzīgi, kā to darītu ar iekļautajiem stiliem izmantojot React. Kā arī jums nav nepieciešams uztraukties par to kā saukt CSS klases, izmantojot tādas metodoloģijas kā BEM, jo to pārvaldīs moduļu sistēma jūsu vietā.

## Renderēšana servera pusē

Renderēšana servera pusē, bieži tiek sauktā par "universālu" vai "izomorfisku" JS. Tas nozīmē, ka jūs varat paņemt savas React komponentes un renderēt tās par statusku HTML servera pusē. Tas uzlabo sākotnējo lapas ielādi, jo tādā veidā, lietotājam nav nepieciešams gaidīt, kamēr JS tiks ielādēts, lai redzētu sākotnējo lietotāja interfeisu, kā arī React var pārizmantot servera pusē renderēto HTML, tādā veidā tam nav nepieciešams to ģenerēt lietotāja pusē.

Jums ir nepieciešama servera puses renderēšana, ja jūs manat, ka jūsu pirmreizējā renderēšana ir pārāk lēna, vai arī, ja jūs vēlaties veikt SEO (meklētājprogrammas optimizāciju). Kautgan, Google tagad ir spējīgs indeksēt lietotāja pusē renderētu saturu, ir pierādīts, ka līdz ar 2016. gada mērijumiem, satura renderēšana lietotāja pusē joprojām negatīvi ietekmē ranžēšanu, potenciāli dēļ lēnas renderēšanas lietotāja pusē.

Lai panāktu renderēšanu servera pusē ir nepieciešama tās "pareiza" realizācija izmantojot daudzus rīkus. Tā kā React komponenšu izstrādes rīki ir izstrādāti neturot prātā problēmas, kas saistītas ar renderēšanu servera pusē, ieteicams sākumā izstrādāt lietojumu un satraukties par renderēšanu servera pusē pēc tam. Jums nebūs nepieciešams pārrakstīt visas jūsu komponentes lai varētu to nodrošināt.

## Immutable.js apguve

[Immutable.js](https://facebook.github.io/immutable-js/) piedāvā datu struktūru kopumu, kas var palīdzēt atrisināt noteiktas problēmas saistītas ar veiktspēju, izstrādājot React lietojumus. Tā ir brīnišķīga bibliotēka, un jums noteikt nāksies to izmantot nākotnē lietojumu izstrādē, taču tā absolūti nav nepieciešama, kamēr jūs nesastapsieties ar lietojuma veiktspējas problēmām.

## Relay, Falcor utt. apguve

Šīs tehnoloģijas palīdz jums samazināt AJAX pieprasījumu skaitu. Tās ir relatīvi eksperimentālas, tāpēc, ja jums nav problēmu, kas saistītas ar pārmērīgi daudziem AJAX izsaukumiem, jums nav nepieciešamības izmantot Relay vai Falcor.
