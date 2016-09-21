# react-howto

React (veya genel olarak önyüz tasarımı) ile yeni tanıştıysanız, bu ekosistemi kafa karıştırıcı bulabilirsiniz. Bunun bir kaç sebebi var.

* React ın hedeflediği kitle; uzmanlar ve onunla başından beri ilgilenenler
* Facebook'un gerçek anlamda kullandığı tek açık kaynaklı proje, bundan dolayı Facebook kendisinden daha küçük projeler için React'ı şekillendirmeye çalışmıyor
* React uzmanıymış gibi davranan, kötü reklam yapan pek çok insan var.

Bu döküman boyunca,kendimizi sadece HTML,CSS ve Javascript ile web sayfası yapıyormuş gibi kabul edeceğiz. 

## Dediklerimi neden dinleyesin ?

Dışarda React ile ilgili birbiriyle çelişen pek çok tavsiye var; işte bu yüzden beni dinlemelisin.

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
* [Relay, Falcor, etc](#relay-falcor-etc)

## React

React'ı öğrenmeye başlarken zamanının çoğunu "tool" ları kurmaya harcaman lazımmış gibi genel bir yanlış kanı var. Resmi dökümanda `.html` uzantılı kaydedebileceğin ve hemen öğrenmeye başlayabileceğin, bir [kopyala-yapıştır HTML taslak](https://facebook.github.io/react/docs/getting-started.html#quick-start-without-npm) göreceksin. **Bu adımda herhangi bir "tool" a gerek yok ve React'ın temellerini tam anlamıyla kavrayana kadar ekstra bir "tool" u öğrenmeye başlamamalısın.**

React'ı öğrenmek için halâ en kolay yolun [resmi dökümanındaki bu örnek](https://facebook.github.io/react/docs/tutorial.html) olduğunu düşünüyorum.

## `npm`

`npm`, ön-yüz geliştiricilerin ve tasarımcıların Javascript kodlarını paylaşmak için en çok kullandıkları, Node.js paket yöneticisidir. npm `CommonJS` denilen bir modüler sisteme sahip olmasından ötürü, Javascript ile yazılmış "tool" ları komut satırıyla indirebilirsin. `CommonJS` in web tarayıcılar için neden gerekli olduğunu öğrenmek için [bu linki](http://0fps.net/2013/01/22/commonjs-why-and-how/) okumalısın veya `CommonJS` API hakkında daha fazla bilgi için [CommonJS Spec Wiki](http://wiki.commonjs.org/wiki/Introduction) ye bakabilirsin.

React ekosisteminde en çok kullanılan yeniden kullanılabilir(reusable) komponentleri, kütüphaneleri, ve "tool" ları `CommonJS` modülü olarak erişip, `npm` ile indirebilirsin.

## JavaScript bundlers

Geçerli bir kaç teknik sebepten dolayı, `CommonJS` modüller (yani `npm` deki her şey) web tarayıcısında olduğu gibi kullanılamazlar. Bundan dolayı `<script>` tagi ile web sayfana koyduğun `.js` dosyalarını "bundle" a dönüştürecek bir "bundler" a ihtiyacın var.

Javascript bundler'lara örnek olarak `webpack` ve `browserify` gösterilebilir. İkisi de gayet iyi bir seçim fakat büyük uygulamaları geliştirmeyi kolaylaştıran pek çok özelliğe sahip olmasından dolayı ben `webpack`'i tercih ediyorum. `Webpack`' in dökümantasyonu kafa karıştırıcı olabiliyor, bunun için taslak olarak kullanabileceğiniz bir paketim var [plug-and-play template for getting started](https://github.com/petehunt/react-webpack-template) ve daha kompleks kullanımlar için de yazmış olduğum [how-to guide for webpack](https://github.com/petehunt/webpack-howto/blob/master/README-tr.md) linkine göz atabilirsiniz.

React'ın artık [resmi olarak desteklediği Create React App isminde](https://github.com/facebookincubator/create-react-app) yeni bir önerisi var. Bu size herhangi bir konfigürasyon yapmanıza gerek kalmadan `webpack` ile çalışan React projeler yapmanıza imkân sağlıyor. Evet biraz kısıtlamaları var ama çok iyi bir başlangıç noktasıymış gibi görünüyor ve zaman içinde gelecek olan güncellemelerle daha fazla özelliği olacaktır. Ayrıca `ejection` özelliği sayesinde tüm konfigürasyonu ve dependency'leri projenizin içine alabilir böylece onları istediğiniz gibi değiştirebilirsiniz.

Aklınızdan çıkarmayacağınız bir şey; `CommonJS`, modülleri import etmek için `require()` fonksiyonunu kullanır ve bir çok kafası karışmış insan, `require.js` ile ilgili bir şeymiş gibi düşünür. Teknik bir kaç sebepten ötürü `require.js` i kullanmaktan kaçınmanızı öneriyorum. Ayrıca zaten React ekosisteminde çok kullanılan bir şey de değil.

## ES6

React tutoriallarında öğrendiğiniz JSX dışında, React örneklerinde bazı ilginç sentakslara rastlayabilirsiniz. ES6 diye adlandırılan ve belki henüz öğrenmediğiniz Javascriptin en son versiyonu. Çok yeni olmasında dolayı, henüz web tarayıcıları tarafından desteklenmemektedir fakat `bundler`ınız özel konfigürasyonlarla onu sizin için çalışır hale getirebilir.

Eğer siz önce bir React'ı halletmek istiyorsanız, **ES6 öğrenme işini es geçebilirsiniz**, veya ilerleyen zamanlarda halletmeyi deneyebilirsiniz.

React komponentler geliştirmek için önerilen yolun ES6 sınıfları yaratmak olduğuyla ilgili bazı konuşmalara rastlayabilirsiniz ki bu doğru değil. Çoğu insan (Facebook'dakiler dahil) `React.createClass()` kullanıyorlar.

## routing

Günümüzün trendi “Single-page uygulamalar”. Bu web sayfaları bir kere yükleniyorlar ve kullanıcı bir linke ve butona tıkladığı anda, sayfadaki Javascript çalışıyor ve adres çubuğunu güncelliyor ama web sayfası yenilenmiyor. Adres çubuğunun yönetimi **router** dediğimiz bir şeyle yapılıyor.

React ekosistemindeki en popüler router, [react-router](https://github.com/rackt/react-router). Single-page uygulama yapıyorsanız, kullanmamak için iyi bir sebebiniz yoksa bunu kullanın.

**Bir single-page uygulama yapmıyorsanız, router kullanmayın**. Zaten projelerin çoğu büyük uygulamaların parçaları olan küçük komponentleri oluşturarak başlar.

## Flux

Muhtemelen Flux'ı duymuşsunuzdur. Flux hakkında *tonlarca* yanlış bilgilendirmeler var.

Uygulama yapmak için yola koyulan çoğu insan, veri modellerini tanımlamak isterken, bunun için Flux'a mecbur olduklarını düşünüyorlar. Flux kullanmak için yanlış bir yol. Flux, hali hazırda zaten bir çok komponent yazılmış ise ancak eklenebilir. 

React komponentler bir hiyerarşiye göre düzenlenir. Çoğu zaman, veri modeliniz bu hiyerarşiye göre çalışır. Bu durumlarda Flux'ın size çok fazla faydası olmaz. Bununla birlikte, bazen, veri modeliniz hiyerarşik olmayabilir. React komponentler alakalı alakasız `props`'lar almaya başladıklarında veya senin az sayıda komponentin git gide daha karmaşık hale geiyorsa, evet o zaman Flux'ı projene eklemek isteyebilirsin.  

**Flux'a ihtiyaç duyacağın zamanı anlayacaksın. İhtiyacın olup olmadığını tam kestiremiyorsan, ihtiyacın yoktur.**

Flux kullanmaya karar verdiysen, bilmen gereken en popüler ve en iyi dökümantasyona sahip Flux kütüphanesi, [Redux](http://redux.js.org/). Dışarıda *pek çok* alternatif var ve sen bunların çoğunu denemek için can atıyor olacaksın ama benim tavsiyem sadece en çok popüler olanlardan birini seçmen.

## Inline styles

Pre-React, a lot of people reused CSS styles with complicated style sheets built by preprocessors like SASS. Since React makes writing reusable components easy, your stylesheets can be less complicated. Many in the community (including myself) are experimenting with getting rid of stylesheets altogether.

This is a fairly crazy idea for a number of reasons. It makes media queries more difficult, and it's possible that there are  performance limitations using this technique. **When starting out with React, just style things the way you normally would.**

Once you've got a feel for how React works, you can look at alternate techniques. One popular one is [BEM](https://en.bem.info/). I recommend phasing out your CSS preprocessor, since React gives you a more powerful way to reuse styles (by reusing components) and your JavaScript bundler can generate more efficient stylesheets for you (I gave [a talk about this at OSCON](https://www.youtube.com/watch?v=VkTCL6Nqm6Y)). With that said, React, like any other JavaScript library, will work just fine with a CSS preprocessor.

Alternatively, you can also use [CSS Modules](http://glenmaddern.com/articles/css-modules), more specifically [react-css-modules](https://github.com/gajus/react-css-modules). With CSS Modules you'll still write CSS (or SASS/LESS/Stylus), but you can manage and compose your CSS files like you'd do with inline styles in React. And you don't need to worry about managing your class names using methodologies like BEM, as this will be handled for you under the hood by the module system.

## server rendering

Server rendering is often called "universal" or "isomorphic" JS. It means that you can take your React components and render them to static HTML on the server. This improves initial startup performance because the user does not need to wait for JS to download in order to see the initial UI, and React can re-use the server-rendered HTML so it doesn't need to generate it client-side.

You need server rendering if you notice that your initial render is too slow or if you want to improve your search engine ranking. While it's true that Google now indexes client-rendered content, as of January 2016 every time it's been measured it's been shown to negatively affect ranking, potentially because of the performance penalty of client-side rendering.

Server rendering still requires a lot of tooling to get right. Since it transparently supports React components written without server rendering in mind, you should build your app first and worry about server rendering later. You won't need to rewrite all of your components to support it.

## Immutable.js

[Immutable.js](https://facebook.github.io/immutable-js/) provides a set of data structures that can help to solve certain performance issues when building React apps. It's a great library, and you'll probably use it a lot in your apps moving forward, but it's completely unnecessary until you have an appreciation of the performance implications. 

## Relay, Falcor etc

These are technologies that help you reduce the number of AJAX requests. They’re still very cutting-edge, so if you don’t have a problem with too many AJAX requests, you don’t need Relay or Falcor.
