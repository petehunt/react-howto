# react-howto

jika kamu Newbie dengan istilah React (atau istilah frontend secara umum), kamu akan sedikit kebingungan dengan ekosistem yang digunakan dalam teknologi React ini. Inilah alasannya:

* React Teknologi hanya ditujukan untuk early-adopters(Pengadopsi awal) dan para ahli dibidangnya.
* Facebook hanya meng-open-source teknologinya saja, sehingga tidak fokus dalam menyediakan alat untuk men-develop project yang lebih-kecil-dari-facebook
* Marketing yang digunakan seperti React Guide tidak cukup mudah dicerna orang awam

Di Tulisan ini, saya mengasumsikan kamu pernah membuat webpage menggukan HTML, CSS, dan JavaScript.

## Kenapa mempercayai saya?

Banyak sekali saran yang kontradiktif dalam penggunaan React diluar sana; kenapa mempercayai saya?

Saya merupakan salah satu anggota dari tim Facebook yang membangun teknologi React. Saat ini saya tidak lagi dalam tim Facebook, sekarang saya sedang membangun startup kecil, sehingga saya mempunyai perspective dari luar facebook juga.

## Bagaimana Mengatasi Masalah Ekosistem teknologi React

Semua Software yang ada dibuat menggunakan berbagai teknologi, dan kamu harus cukup paham dalam mengaplikasikan berbagai teknologi tersebut dalam aplikasi yang kamu buat, Alasannya karena alat yang digunakan dalam ekosistem teknologi React ini terlihat sangat banyak, dan selalu dijelaskan dengan urutan yang salah.

Kamu harus memahami sesuai dengan urutan dibawah ini, **tanpa melewati ataupun memahaminya secara acak**:

* [Teknologi React](#teknologi-react)
* [`npm`](#learning-npm)
* [JavaScript “bundlers”](#learning-javascript-bundlers)
* [ES6](#learning-es6)
* [Routing](#learning-routing)
* [Flux](#learning-flux)

**Kamu tidak perlu untuk memahami semua teknologi ini untuk produktif dengan React.** Berpindalah ke langkah selanjutnya jika memiliki masalah yang perlu untuk dipecahkan.

Sebagai tambahan, terdapat beberapa topik yang sering disebut dalam Komunitas React, termasuk "Approach terbaru". Topik dibawah ini sangat menarik, tapi cukup sulit untuk dipahami orang awam, dan tidak cukup populer dibandingkan topik diatas, serta **tidak selalu dibutuhkan untuk kebanyakan aplikasi.**
* [Inline styles](#learning-inline-styles)
* [Server rendering](#learning-server-rendering)
* [Immutable.js](#learning-immutablejs)
* [Relay, Falcor, etc](#learning-relay-falcor-etc)

## Teknologi React

Sudah menjadi miskonsepsi umum jika kamu perlu membuang banyak waktu dalam menyiapkan kebutuhan (IDE, ataupun dependensi) untuk memulai memahami React. Di dokumentasi resminya, kamu akan menemukan [copy-paste HTML template](https://facebook.github.io/react/docs/getting-started.html#quick-start-without-npm) yang dapat disimpan dalam bentuk `.html` file dan dapat langsung digunakan. **Tidak perlu IDE yang siap ataupun dependensi lain yang dibutuhkan dalam langkah ini, dan jangan mulai mempelajari teknologi tersebut sampai kamu nyaman dengan dasar penggunaan React**

saya pikir bahwa cara termudah dalam mempelajari React yaitu dengan berdasarkan [tutorial resmi](https://facebook.github.io/react/docs/tutorial.html).

## Learning `npm`

`npm` merupakan Node.js package manager dan merupakan cara paling populer yang digunakan orang front-end dan designer dalam membagikan JavaScript code mereka. termasuk system modul yang disebut `CommonJS` dan sehingga memungkinkan untuk menginstall command-line tools yang ditulis dalam JavaScript. Baca [post ini](http://0fps.net/2013/01/22/commonjs-why-and-how/) untuk dasar kenapa `CommonJS` dibutuhkan untuk browser, atau [CommonJS Wiki](http://wiki.commonjs.org/wiki/Introduction) untuk memahami lebih lanjut tentang `CommonJS` API.

Component, library, dan modul lain yang paling sering digunakan dan terkait dengan ekosistem React juga tersedia seperti modul `CommonJS` dan dapat di install dengan `npm`.

## Learning JavaScript bundlers

Untuk beberapa alasan teknikal yang baik modul `CommonJS` (dan semua yang ada di `npm`) tidak dapat digunakan secara native (di implementasikan secara spesifik) di dalam browser. kamu perlu JavaScript “bundler” untuk mem-“bundle” modul tersebut ke `.js` file yang nantinya di include ke dalam webpage dengan tag `<script>` .

Contoh dari JavaScript bundlers adalah `webpack` and `browserify`. Keduanya merupakan pilihan yang bagus, tetapi saya lebih memilih `webpack` karena mempunyai banyak fitur yang membuat proses development dari aplikasi yang besar dan kompleks menjadi lebih mudah. karena dokumentasinya cukup rumit, saya punya [plug-and-play template untuk memulai](https://github.com/petehunt/react-webpack-template) dam saya juga menulis [panduan untuk webpack](https://github.com/petehunt/webpack-howto) untuk study kasus yang kompleks.

React juga menawarkan [secara resmi CLI tool yang disebut Create React App](https://github.com/facebookincubator/create-react-app). hal tersebut membuat kamu dapat membuat React project yang didukung oleh `webpack` tanpa configurasi. Tool tersebut terdapat batasan, tetapi dapat memberikanmu titik mulai yang bagus, dan Pembaruannya akan memberikan fitur tambahan. dan terdapat sebuah fitur "ejection" yang membuat semua konfigurasi dan dependensi yang ada di salin ke project mu, sehingga kamu punya kontrol penuh terhadap konfigurasi tersebut.

Perlu diingat: `CommonJS` menggunakan `require()` untuk import modul yang ada, sehingga banyak orang bingung dan berfikir bahwa perlu dependensi/modul dari `require.js`. Untuk beberapa alasan teknikal, saya menyarankan untuk menghindari modul `require.js`. dan modul tersebut tidak populer di Ekositem React.

## Learning ES6

Terlepas dari JSX (yang telah kamu pelajari di tutorial React), kamu mungkin menemukan beberapa syntax yang aneh dalam contohnya. Hal ini disebut ES6, dan merupakan versi terbaru dari JavaScript sehingga kamu belum mempelajarinya. Karena hal baru, teknologi tersebut belum di support oleh browser, tetapi modul “bundler” dapat menerjemahkannya untuk kamu dengan configurasi yang benar.

jika kamu ingin menyelesaikan sesuatu dengan React secara cepat, **kamu dapat melewati ES6**, atau mencoba memahaminya dengan mengaplikasikannya langsung.

kamu mungkin mendengar bahwa ES6 class menjadi pilihan utama dalam membuat React component. hal ini salah. Kebanyakan orang (termasuk tim Facebook) menggunakan `React.createClass()`.

## Learning routing

Istilah “Single-page applications” sedang booming belakangan ini. SPA merupakan web pages yang di load sekali, dan ketika pengguna meng-click sebuah link atau tombol, JavaScript yang berjalan pada halaman tersebut meng-update address bar, tetapi web page tidak di refresh. Pengaturan dari address bar diatur oleh **router**.

Router paling populer di Ekosistem React adalah [react-router](https://github.com/rackt/react-router). jika kamu membuat SPA, gunakan react-router kecuali kamu memiliki alasan yang bagus untuk tidak menggunakannya.

**jangan menggunakan router jika tidak membuat single-page application**. lagipula, Kebanyakan project dimulai dari komponen yang kecil yang nantinya membentuk aplikasi yang kompleks.

## Learning Flux

Kamu mungkin telah mengenal Flux. Terdapat *banyak sekali* misinformasi tentang Flux diluar sana.

Banyak orang membuat aplikasi dan ingin mendefinisikan data model mereka, dan mereka berfikir untuk harus menggunakan Flux untuk melakukannya **Ini merupkan cara berfikir yang salah dalam mengadopsi teknologi Flux. Flux hanya harus ditambahkan saat telah terdapat banyak komponen.**

React komponen disusun sesuai hirarki. Kebanyakan, data model kamu juga tersusun dalam hirarki. didalam situasi seperti ini Flux tidak terlalu berguna. Terkadang, bagaimanapun data model kamu tidak tersusun secara hirarki. Ketika React komponen memulai menerima `props` yang besar, atau kamu memiliki beberapa komponen yang nantinya akan menjadi lebih kompleks, saat itulah kamu perlu menggunakan Flux.

**Kamu akan tahu kapan membutuhkan Flux. Jika kamu tidak yakin untuk memerlukannya, kamu tidak perlu menggunakan Flux**

jika kamu memutuskan untuk menggunakan Flux, librari yang sangat populer dan terdokumentasi secara baik adalah [Redux](http://redux.js.org/). Terdapat *banyak sekali* alternatif yang ada diluar sana, dan kamu akan kebingungan untuk mengevaluasinya, tetapi saran saya, pilihlah librari yang paling populer.

## Learning inline styles

Pre-React, a lot of people reused CSS styles with complicated style sheets built by preprocessors like SASS. Since React makes writing reusable components easy, your stylesheets can be less complicated. Many in the community (including myself) are experimenting with getting rid of stylesheets altogether.

This is a fairly crazy idea for a number of reasons. It makes media queries more difficult, and it's possible that there are  performance limitations using this technique. **When starting out with React, just style things the way you normally would.**

Once you've got a feel for how React works, you can look at alternate techniques. One popular one is [BEM](https://en.bem.info/). I recommend phasing out your CSS preprocessor, since React gives you a more powerful way to reuse styles (by reusing components) and your JavaScript bundler can generate more efficient stylesheets for you (I gave [a talk about this at OSCON](https://www.youtube.com/watch?v=VkTCL6Nqm6Y)). With that said, React, like any other JavaScript library, will work just fine with a CSS preprocessor.

Alternatively, you can also use [CSS Modules](http://glenmaddern.com/articles/css-modules), more specifically [react-css-modules](https://github.com/gajus/react-css-modules). With CSS Modules you'll still write CSS (or SASS/LESS/Stylus), but you can manage and compose your CSS files like you'd do with inline styles in React. And you don't need to worry about managing your class names using methodologies like BEM, as this will be handled for you under the hood by the module system.

## Learning server rendering

Server rendering is often called "universal" or "isomorphic" JS. It means that you can take your React components and render them to static HTML on the server. This improves initial startup performance because the user does not need to wait for JS to download in order to see the initial UI, and React can re-use the server-rendered HTML so it doesn't need to generate it client-side.

You need server rendering if you notice that your initial render is too slow or if you want to improve your search engine ranking. While it's true that Google now indexes client-rendered content, as of January 2016 every time it's been measured it's been shown to negatively affect ranking, potentially because of the performance penalty of client-side rendering.

Server rendering still requires a lot of tooling to get right. Since it transparently supports React components written without server rendering in mind, you should build your app first and worry about server rendering later. You won't need to rewrite all of your components to support it.

## Learning Immutable.js

[Immutable.js](https://facebook.github.io/immutable-js/) provides a set of data structures that can help to solve certain performance issues when building React apps. It's a great library, and you'll probably use it a lot in your apps moving forward, but it's completely unnecessary until you have an appreciation of the performance implications. 

## Learning Relay, Falcor etc

These are technologies that help you reduce the number of AJAX requests. They’re still very cutting-edge, so if you don’t have a problem with too many AJAX requests, you don’t need Relay or Falcor.
