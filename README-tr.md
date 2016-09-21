# react-howto

React (veya genel olarak önyüz tasarımı) ile yeni tanıştıysanız, bu ekosistemi kafa karıştırıcı bulabilirsiniz. Bunun bir kaç sebebi var.

* React ın hedeflediği kitle; bu işin uzmanları ve onunla başından beri ilgilenenler
* Facebook'un gerçek anlamda kullandığı tek açık kaynaklı proje, bundan dolayı Facebook kendisinden daha küçük projeler için React'ı şekillendirmeye çalışmıyor
* React uzmanıymış gibi davranan, kötü reklam yapan pek çok insan var.

Bu döküman boyunca,kendimizi sadece HTML,CSS ve Javascript ile web sayfası yapıyormuş gibi kabul edeceğiz. 

## Neden beni dinlemelisiniz ?

Dışarıda React ile ilgili birbiriyle çelişen pek çok tavsiye var; işte bu yüzden beni dinlemelisin.

React'ı yazan ve onu açık kaynak kodlu hale getiren Facebook ekibinin orjinal üyelerinden biriydim.Artık Facebook'ta çalışmıyorum, küçük bir startup'dayım. Bu sayede Facebook dışından da olaya bakan bir bakış açısına sahibim. 

## React ekosistemiyle nasıl baş ederim ?

Her yazılım, bir sürü teknolojinin birleşmesiyle oluşmuştur ve sen bu teknolojileri uygulamanda kullanmaya yetecek kadar iyi anlamalısın. React sana çok bunaltıcı, aşırı karışık gelmesinin sebebi, bazı şeyleri yanlış sırayla öğrenmiş olman.  

Takip etmen gereken liste şu şekilde olmalı **sırasını atlamadan ve aynı zamanda ikisini birden değil, hepsini teker teker öğrenmelisin.**   

* [React](#react)
* [`npm`](#npm)
* [JavaScript “bundlers”](#javascript-bundlers)
* [ES6](#es6)
* [Routing](#routing)
* [Flux](#flux)


**React ile bir şeyler yapmak için bunların hepsini harfi harfine öğrenmene gerek yok.** Bunların herhangi birinde ayağın taşa takılırsa, durma bir sonrakine geç.

Ek olarak, React camiasının sıklıkla bahsettiği "yeni teknolojiler" var. Anlaması zor olmayan, hayli ilgi çekici bu konular yukarıda ki konulardan daha az popüler ve **çoğu uygulama için gerekli değiller**  

* [Inline styles](#inline-styles)
* [Server rendering](#server-rendering)
* [Immutable.js](#immutablejs)
* [Relay, Falcor, etc](#relay-falcor-vb)

## React

React'ı öğrenmeye başlarken zamanının çoğunu "tool" ları kurmaya harcaman lazımmış gibi genel bir yanlış kanı var. Resmi dökümanda `.html` uzantılı kaydedebileceğin ve hemen öğrenmeye başlayabileceğin, bir [kopyala-yapıştır HTML taslak](https://facebook.github.io/react/docs/getting-started.html#quick-start-without-npm) göreceksin. **Bu adımda herhangi bir "tool" a gerek yok ve React'ın temellerini tam anlamıyla kavrayana kadar ekstra bir "tool" u öğrenmeye başlamamalısın.**

React'ı öğrenmek için halâ en kolay yolun [resmi dökümanındaki bu örnek](https://facebook.github.io/react/docs/tutorial.html) olduğunu düşünüyorum.

## `npm`

`npm`, ön-yüz geliştiricilerin ve tasarımcıların Javascript kodlarını paylaşmak için en çok kullandıkları, Node.js paket yöneticisidir. npm `CommonJS` denilen bir modüler sisteme sahip olmasından ötürü, Javascript ile yazılmış "tool" ları komut satırıyla indirebilirsin. `CommonJS` in web tarayıcılar için neden gerekli olduğunu öğrenmek için [bu linki](http://0fps.net/2013/01/22/commonjs-why-and-how/) okumalısın veya `CommonJS` API hakkında daha fazla bilgi için [CommonJS Spec Wiki](http://wiki.commonjs.org/wiki/Introduction) ye bakabilirsin.

React ekosisteminde en çok kullanılan yeniden kullanılabilir(reusable) komponentleri, kütüphaneleri, ve "tool" ları `CommonJS` modülü olarak erişip, `npm` ile indirebilirsin.

## JavaScript bundlers

Geçerli bir kaç teknik sebepten dolayı, `CommonJS` modüller (yani `npm` deki her şey) web tarayıcısında olduğu gibi kullanılamazlar. `<script>` tagi ile web sayfana koyduğun `.js` dosyalarını "bundle" a dönüştürecek bir "bundler" a ihtiyacın var.

Javascript bundler'lara örnek olarak `webpack` ve `browserify` gösterilebilir. İkisi de gayet iyi seçim fakat büyük uygulamaları geliştirmeyi kolaylaştıran pek çok özelliğe sahip olmasından dolayı ben `webpack`'i tercih ediyorum. `Webpack`' in dökümantasyonu kafa karıştırıcı olabiliyor, bunun için taslak olarak kullanabileceğiniz bir paketim var [plug-and-play template for getting started](https://github.com/petehunt/react-webpack-template) ve daha kompleks kullanımlar için de yazmış olduğum [how-to guide for webpack](https://github.com/petehunt/webpack-howto/blob/master/README-tr.md) linkine göz atabilirsiniz.

React'ın artık [resmi olarak desteklediği Create React App isminde](https://github.com/facebookincubator/create-react-app) yeni bir önerisi var. Bu size herhangi bir konfigürasyon yapmanıza gerek kalmadan `webpack` ile çalışan React projeler yapmanıza imkân sağlıyor. Evet biraz kısıtlamaları var ama çok iyi bir başlangıç noktasıymış gibi görünüyor ve zaman içinde gelecek olan güncellemelerle daha fazla özelliği olacaktır. Ayrıca `ejection` özelliği sayesinde tüm konfigürasyonu ve dependency'leri projenizin içine alabilir böylece onları istediğiniz gibi değiştirebilirsiniz.

Aklınızdan çıkarmamanız gereken bir şey; `CommonJS`, modülleri import etmek için `require()` fonksiyonunu kullanır ve bir çok insan, kafası karışıp, `require.js` tarzı bir şey mi yapıyorum diye düşünebilir. Teknik bir kaç sebepten ötürü `require.js` i kullanmaktan kaçınmanızı öneriyorum. Ayrıca zaten React ekosisteminde çok kullanılan bir şey de değil.

## ES6

React tutoriallarında öğrendiğiniz JSX dışında, React örneklerinde bazı ilginç sentakslara rastlayabilirsiniz. ES6 diye adlandırılan ve belki henüz öğrenmediğiniz Javascriptin en son versiyonu. Çok yeni olmasında dolayı, henüz web tarayıcıları tarafından desteklenmemektedir fakat `bundler`ınız özel konfigürasyonlarla onu sizin için çalışır hale getirebilir.

Eğer siz önce React'ı halletmek istiyorsanız, **ES6 öğrenme işini es geçebilirsiniz**, veya ilerleyen zamanlarda öğrenmeyi deneyebilirsiniz.

React komponentler geliştirmek için önerilen yolun ES6 sınıfları yaratmak olduğuyla ilgili bazı konuşmalara rastlayabilirsiniz ki bu doğru değil. Çoğu insan (Facebook'dakiler dahil) `React.createClass()` kullanıyorlar.

## routing

Günümüzün trendi “Single-page uygulamalar”. Bu web sayfaları, bir kere yükleniyorlar ve kullanıcı bir linke veya butona tıkladığı anda, sayfadaki Javascript, çalışıyor ve adres çubuğunu güncelliyor ama web sayfası tekrar yenilenmiyor. Adres çubuğunun yönetimi **router** dediğimiz şeyle yapılıyor.

React ekosistemindeki en popüler router, [react-router](https://github.com/rackt/react-router). Single-page uygulama yapıyorsanız, kullanmamak için iyi bir sebebiniz yoksa bunu kullanın.

**Bir single-page uygulama yapmıyorsanız, router kullanmayın**. Zaten projelerin çoğu büyük uygulamaların parçaları olan küçük komponentleri oluşturarak başlar.

## Flux

Muhtemelen Flux'ı duymuşsunuzdur. Flux hakkında *tonlarca* yanlış bilgi var.

Uygulama yapmak için yola koyulan çoğu insan, veri modellerini tanımlamak isterken, bunun için Flux'a mecbur olduklarını düşünüyorlar.Bu Flux kullanmak için yanlış bir yol. Flux,projenizde hali hazırda zaten bir çok komponent yazılmış ise ancak eklenebilir. 

React komponentler bir hiyerarşiye göre düzenlenir. Çoğu zaman, veri modeliniz bu hiyerarşiye göre çalışır. Bu durumlarda Flux'ın size çok fazla faydası olmaz. Bununla birlikte, bazen, veri modeliniz hiyerarşik olmayabilir. React komponentler alakalı alakasız `props`'lar almaya başladıklarında veya senin az sayıda komponentin git gide daha karmaşık hale geiyorsa, evet o zaman Flux'ı projene eklemek isteyebilirsin.  

**Flux'a ihtiyaç duyacağın zamanı anlayacaksın. İhtiyacın olup olmadığını tam kestiremiyorsan, ihtiyacın yoktur.**

Flux kullanmaya karar verdiysen, bilmen gereken en popüler ve en iyi dökümantasyona sahip Flux kütüphanesi, [Redux](http://redux.js.org/). Dışarıda *pek çok* alternatif var ve sen bunların çoğunu denemek için can atıyor olacaksın ama benim tavsiyem sadece en çok popüler olanlardan birini seçmen.

## Inline styles

React öncesi, bir çok insan SASS gibi önişlemcilerle yapılmış tekrar kullanılabilir karmaşık CSS style'lar kullandı. React yeniden kullaılabilir komponentlerin yazımını kolaylaştırdığına göre, style sayfalarımızın karmaşıklığı da azaltılabilirdi. React kominitesindekilerin çoğu (kendim dahil) tüm style sayfalarını beraber tutmaktan kurtulmayı deniyoruz.

Bir kaç nedenden ötürü bu oldukça çılgın bir fikir. Media query'ler yapması daha zor ve bu tekniğin, muhtemel performas sınırlandırmaları olacak. **React ile çalışmaya başladığımız zaman,sadece style işleri normal olarak yolunda devam ediyordu**

React'ın nasıl çalıştığını bir kere kavradığında, alternatif tekniklere göz atabilirsin. Bu tekniklerden popüler olanlardan biri [BEM](https://en.bem.info/). Benim tavsiyem, CSS önişlemcilerini adım adım kullanımdan kaldırmanız, çünkü React size style'larınızı tekrar kullanılabilir yapmak için daha etkin bir yol vadediyor. (Bunun hakkında [OSCON'da ki konuşmamı](https://www.youtube.com/watch?v=VkTCL6Nqm6Y) izleyebilirsiniz) Bununla beraber, React, diğer Javascript kütüphaneleri gibi, herhangi bir CSS önişlemcisiyle de ile de gayet iyi çalışabiliyor.

Alternatif olarak, [CSS Modules](http://glenmaddern.com/articles/css-modules) de kullanılabilir, daha özelleştirilmiş hali olarak da [react-css-modules](https://github.com/gajus/react-css-modules) var. CSS Modules ile sen yine CSS (veya SASS/LESS/Stylus) yazıyor olacaksın ama React içinde inline style kullanır gibi CSS dosyalarını yönetebilir ve birleştirebilirsin. Ve BEM'de ki methodları kullanır gibi class isimlerini nasıl yönetirim endişesini duymana gerek yok, moduler sistem  tarafından arkaplan da bu giderilecektir.   

## server rendering

Server rendering genel olarak "universal" veya "isomorphic" JS olarak adlandırılır. Bunun anlamı, React, komponentleri server tarafında render edip, onları static HTML olarak sana verir. İlk başta sayfa açılış performansı artar, çünkü kullanıcı görmek istediği ilk sayfada ki JS dosyasının yüklenmesini beklemek zorunda kalmaz ve React server-rendered HTML'i tekrar kullanabilir böylece client tarafında oluşturmasına, render etmesine gerek kalmaz. 

Başlangıçtaki sayfa yüklemesi çok yavaşsa veya arama motorunun performansını geliştirmek istiyorsan, server rendering yapmaya ihtiyacın var. Google'ın şu an içerikleri client tarafında render ettiği biliniyor,muhtemelen bu yaklaşımın bedeli olarak, Ocak 2016 verileri, performans anlamında olumsuz bir etkilenme olduğunu gösteriyor


Server rendering tam anlamıyla çalışabilmesi için halâ bir çok tool'a ihtiyaç var. Server rendering olmadan da net bir biçimde React komponentlerinin yazılabilmesinden dolayı, ilk önce uygulamanızı yapıp, server rendering olayını daha sonra düşünebilirsiniz. Sonradan uygulamanızın server rendering'i desteklemesi için bütün komponentlerinizi tekrardan yazmanıza gerek olmayacak.

## Immutable.js

[Immutable.js](https://facebook.github.io/immutable-js/), React uygulamalar geliştirirken meydana gelen performans sorunlarını tam anlamıyla çözmeye yardımcı veri yapıları kümesi sağlıyor ve muhtemelen uygulamalarınız için ilerde pek çok kez kullanıyor olacaksınız. İstenilen sizi tatmin eden bir performansa sahipse uygulamanız, kullanmanız tamamen gereksiz.

## Relay, Falcor vb

AJAX isteklerinin sayısını azaltmaya yardımcı teknojiler. Onlar halâ çok yeniler, bu yüzden eğer çok fazla AJAX isteğiyle herhangi bir probleminiz yoksa, Relay or Falcor kullanmanıza da gerek yok.
