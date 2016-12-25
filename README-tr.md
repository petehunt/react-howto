# react-howto

React ekosistemini karmaşık bulabilirsiniz. Bunun bir iki sebebi var;

* React geçmişte hep erken adapte olanlara ya da uzmanlara yönelik konumlandırıldı

* Facebook sadece kullandığı kaynak kodlarını açar. Bu nedenle, FB'dan-küçük-projelere destek ve geliştirme sunmaya odaklanmaz

* Etrafta "React öğrenme kılavuzu" adı altında bir çok anti-marketing var

Bu yazıda; HTML, CSS ve JS kullanarak bir web sitesi geliştirilmiş olduğunuzu varsayacağım.

## Neden beni dinleyesiniz?

React'i geliştiren ve kaynağını açan Facebook takımının ilk üyelerinden biriyim.

Ayrıca şu anda ayrı bir *startup*'dayım, o nedenle Facebook'a karşı objektif olabilirim.

## React ekosisteminin içinden çıkmak

Her yazılım, temelindeki bir takım teknolojilerin üzerine inşa edilir. Uygulamanızı daha iyi geliştirebilmek için de bu teknolojilerin oluşturduğu *stack* hakkında yeteri kadar bilgi sahibi olmanız gerekir.

React araçları ekosisteminin bu kadar karmaşık olmasının nedeni,bu teknolojilerin  yanlış sırayla öğrenilmelerinden kaynaklanıyor.

Müfredat aşağıdaki gibi olmalı. **Sırayla ve aynı anda tek bir konu işleyerek.**

* React
* `npm`
* JavaScript *bundler*'lar
* ES6
* Router
* Flux

**React kullanarak iş çıkarabilmek için bu teknolojilerin hepsine hakim olmanız gerekmez.** Bir sonraki konuya, sadece uygulamanızın o alanda çözmesi gereken bir problem olduğunda geçin.

React dünyasında, aşağıdaki teknolojilere rastlayabilirsiniz. Bu konular ilginç, evet, ancak anlaması zor ve yukarıdaki konulara göre daha az önemliler. Ek olarak, **bir çok uygulama bunlara ihtiyaç duymayacaktır**

* kod içinde stil (CSS) verme
* sunucu tarafında işleme
* Immutable.js
* Relay, Falcor, vb.

## React kütüphanesini öğrenmek

React öğrenmeye başlamak için fazla hazırlık yapmanız gerekmiyor. Dökümantasyonda, [copy-paste yaparak](https://facebook.github.io/react/docs/getting-started.html#quick-start-without-npm) bir .html dosyasında çalıştırabileceğiniz bir örnek var.

Bu adım için herhangi bir araç kullanmamız gerekmiyor. Zira, **temel React bilginize güvenmeden geliştirme araçlarını öğrenmeye çalışmayın.**

Ben, React öğrenmenin en kolay yolunun [dökümantasyonu]((https://facebook.github.io/react/docs/tutorial.html) olduğunu düşünüyorum.

## `npm` öğrenmek

Node.js paket yöneticisine `npm` deniyor. JS kodunun dağıtımı için şu anda en popüler araç. `CommonJS` modül sistemini kullanır. Ayrıca JS ile yazılmış komut satırı (*CLI*) uygulamalarını kullanmanızı sağlar.

[Şurada](http://0fps.net/2013/01/22/commonjs-why-and-how/) `CommonJS` modül sistemine tarayıcılarda neden ihtiyaç olduğu hakkında bir yazı var. `CommonJS` API'si hakkında daha fazla bilgi için ise [CommonJS Spec Wiki](http://wiki.commonjs.org/wiki/Introduction).

React ekosistemindeki kütüphanelerin ve araçların büyük çoğunluğu, `npm` ile erişebileceğiniz `CommonJS` modülleridir.

## Javascript *bundler*'larını öğrenmek

Bir takım teknik nedenden ötürü, `CommonJS` modülleri (yani npm'deki her şey) tarayıcılarda kullanılamıyor. Bu nedenle bir adet JS *bundler*'a ihtiyacımız var. Modülleri tek bir `.js` dosyasında bulunacak şekilde derler. Sonra da `bundle.js` dosyasını `<script>` ile uygulamamıza ekleyebiliriz.

Bu araca iki örnek; browserify ve webpack. İkisi de iyi çözümler ama ben webpack'i tercih ediyorum. Uygulama büyüdüğünde, geliştiricinin hayatını kolaylaştıran ayarlar yapılabiliyor webpack'le.

Dökümantasyonu karışık gelebilir. Başlarkenki konfigürasyonlarınızda kullanabileceğiniz [bir örnek] (https://github.com/petehunt/react-webpack-template) hazırladım. Ayrıca, ileri seviye kullanımlar için de [şurada](https://github.com/petehunt/webpack-howto) bir örnek var.

Artık, resmi olarak desteklenen, [Create React App](https://github.com/facebookincubator/create-react-app) adında bir adında bir CLI aracı da var. *Bundler* olarak webpack kullanarak, hiç bir konfigürasyon yapmadan bir React projesine başlayabilirsiniz.

Aracın bazı limitleri var ama başlangıç için çok iyi bir seçenek. Gelecek versiyonlarında özellikleri artacak. Ayrıca `npm run eject` komutu ile projenizin halihazırdaki konfigürasyonunu kaydeder ve kontrolü size geçirir.

Aklınızda olsun; `CommonJS` modülleri çağırmak için `require()` fonksiyonunu kullanıyor. Bazıları bunu `require.js` projesiyle karıştırıyorlar. İkisi farklı şeyler.

## ES6 öğrenmek

React projelerinde ES6 sentaksı da görebilirsiniz. Yeni olduğu için tarayıcıların hepsinde desteklenmiyor bu sentaks. Ama kullandığımız bundler, doğru konfigüre edildiğinde, bu kodu tarayıcıların anlayabileceği formata çevirebiliyor.

React projelerinde hızlı yol almak için ES6 öğrenimini **erteleyebilirsiniz**. Öğrenme süreci sırasında ES6'ya aşina olursunuz.

ES6 `class`'larının React yazarken tercih edilen usül olduğunu duyabilirsiniz. Doğru değil. Bir çok kişi (FB da dahil) `React.createClass()` kullanıyor.

## Router

Bugünlerde SPA'lar çok popüler. Bunlar, tek sefer tarayıcıya yüklenen ve kullanıcı ile interaksiyon sonucunda tarayıcının adres çubuğunu güncelleyen bir JS kodu kullanan uygulamalar. Ama sayfa değiştiğinde tarayıcı sayfayı yeniden yüklemiyor. Adres çubuğunun koordinasyonu *router* adı verilen parça ile sağlanıyor.

React ekosistemindeki en popüler seçenek [react-router](https://github.com/rackt/react-router). Eğer bir SPA yapıyorsanız, daha iyi sebebiniz olmadığı sürece bunu kullanın.

**Eğer SPA yapmıyorsanız router kullanmayın.** Bir çok proje büyük bir uygulamanın içindeki komponentler halinde başlar zaten.

## Flux öğrenmek

Bazıları, uygulamalarının data modellerini tasarlarken Flux kullanmak zorunda olduklarını düşünüyorlar. **Bu, Flux kullanmaya başlamak için yanlış bir neden. Flux, bir çok komponent hazırlanmış olduktan sonra uygulamaya dahil edilmeli.**


Komponentlerinizin aldığı `props` oraya ait değil gibi geldiğinde ya da koordinasyonları hızla karmaşıklaşmaya başlayan bir komponent öbeğiniz olduğunda, Flux mimarisine bir bakın.

**Ne zaman Flux'a ihtiyacınız olduğunu anlayabileceksiniz. Eğer ihtiyacınız olduğundan emin değilseniz, ihtiyacınız yok.**

Eğer Flux kullanmaya karar verdiyseniz, en popüler olanı [Redux](http://redux.js.org/). *Bir çok* alternatif var. Ancak benim önerim en popüler olan.

## kod içinde stil

React öncesinde, bir çok kişi CSS yönetimini SASS gibi ön-işleyicilerle yapıyordu. Bir projede kullanılan CSS'i *yeniden kullanılabilir* yapmak için CSS üzerinde bir soyutlaştırma gerekir; onu da bir pre-processor kullanarak çözersiniz.

React, yeniden kullanılabilir komponent yapmayı kolaylaştırdığı için stilleri yönetmek de kolaylaşıyor. Topluluktaki bir çok kişi (ben dahil) .css dosyalarını hiç kullanmadan stil vermeyi araştırıyoruz.

Bir çok açıdan ters bir fikir kod içinde stil vermek aslında. Bir kere @media sorgularını zorlaştırıyor. Ayrıca bu tekniği kullanmanın getireceği performans sorunları olması da hayli muhtemel. **React'e başlarken, uygulamaya stili bildiğiniz yöntemle verin.**

React'in nasıl çalıştığına aşina olduktan sonra stil vermek için alternatiflere bakabilirsiniz. Popüler yötemlerden biri [BEM](https://en.bem.info/). Ön-işlemcinizi bir süre sonra devre dışına almanızı öneririm zira React komponentleri yeniden kullanılabilir (birbirinin içine geçebilen) kıldığı için, stilleri de kodun içinde yönetmek kolaylaşıyor. Bundler'ınız size optimize bir CSS çıkarıyor. Bu konuyla ilgili  [OSCON'da bir konuşma](https://www.youtube.com/watch?v=VkTCL6Nqm6Y) yaptım.

Her halükarda, React, diğer her JS kütüphanesi gibi, bir CSS pre-processor olmadan da çalışır.

Bir alternatif de [CSS Modules](http://glenmaddern.com/articles/css-modules), React için olanı da [react-css-modules](https://github.com/gajus/react-css-modules). CSS modules ile, yine CSS (SASS/LESS/Stylus) yazıyor olacaksınız ama .css dosyalarınızı kod içindeki stiller gibi düzenleyebileceksiniz. Bu yöntemde, BEM türü metodolojileri takip etmenize gerek kalmıyor. HTML'de gereken `class` adı modül sistemi sayesinde belirleniyor.

## sunucu tarafında işleme

Bu teknolojiye '*universal* ya da *isomorphic* JS kullanmak' şeklinde rastlayabilirsiniz. Kısacası şu demek oluyor; React komponentlerinizi, sunucuda HTML'e dönüştürerek, kullanıcıya o şekilde iletebilirsiniz. Bu uygulamanın *load* süresini kısaltıyor zira tarayıcın arayüzün şeklini şemalini göstermek için büyük bir JS dosyasının *tamamının* yüklenmesini beklemesi gerekmiyor.

React, *backend*'de (sunucu tarafında) hazırlanmış HTML dizgisini *frontend*'de de kullanabiliyor. Yeniden işlemesine gerek yok.

Backend'de işlemeye, uygulamanızın ilk yüklemesinin yavaşladığını farkettiğinizde ya da SEO gerektiğinde ihtiyacınız olur. Google'ın kullanıcı tarafında hazırlanmış içeriği indeksleyebildiği doğru olsa da, Ocak 2016 itibariyle, yapılan bütün ölçümlerde, bu tür endekslemenin arama sıralamalarını negatif yönde etkilediği görüldü. Bir ihtimal, tarayıcıda içerik yaratmanın performansa etkileri nedeniyle.

Sunucu tarafında işlemeyi doğru yapabilmek için bir çok aracın kullanılması gerekecek. Ancak, bu özellik *backend rendering* özelliği hesaba katılmadan tasarlanmış React komponentleri ile uyumlu olduğu için, önce uygulamanızı hazırlayın, sunucu tarafında işlenmesini sonrasında düşünün. Uygulamanıza bu özelliği getirmek için her şeyi baştan yazmanıza gerek olmayacak.

## Immutable.js öğrenmek

[Immutable.js](https://facebook.github.io/immutable-js/), size React uygulamaları geliştirirken karşınıza çıkabilecek performans sorunlarında yardımcı olacak veri yapıları (data structures) veriyor. Oldukça güzel bir kütüphane ve React projelerindeki kullanımı da kesinlikle artacak. Ancak uygulamanızın performans sorunlarını tam anlamıyla anladıktan sonra bu konuya bakın.

## Relay, Falcor, vb.

Bu teknolojiler, AJAX sorgularınızı azaltmanızı sağlar.  Halen oldukça yeniler. AJAX sorgularınızın yönetimleri zor bir noktaya gelene kadar Relay ya da Falcor'a ihtiyacınız yok.
