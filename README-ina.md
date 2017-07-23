# react-howto

jika kamu Newbie dengan istilah React (atau istilah frontend secara umum), kamu akan sedikit kebingungan dengan ekosistem yang digunakan dalam teknologi React ini. Inilah alasannya:

* React Teknologi hanya ditujukan untuk early-adopters(Pengadopsi awal) dan para ahli dibidangnya.
* Facebook hanya meng-open-source teknologinya saja, sehingga tidak fokus dalam menyediakan alat untuk men-develop project yang lebih-kecil-dari-facebook.
* Marketing yang digunakan seperti React Guide tidak cukup mudah dicerna orang awam.

Di Tulisan ini, saya mengasumsikan kamu pernah membuat webpage menggunakan HTML, CSS, dan JavaScript.

## Kenapa kamu perlu untuk percaya dengan saya?

Banyak sekali saran yang kontradiktif dalam penggunaan React diluar sana; kenapa perlu percaya dengan saya?

Saya merupakan salah satu anggota dari tim Facebook yang membangun teknologi React. Saat ini saya tidak lagi dalam tim Facebook, sekarang saya sedang membangun startup kecil, sehingga saya mempunyai perspective dari luar facebook juga.

## Bagaimana Mengatasi Masalah Ekosistem Teknologi React

Semua Software yang ada dibuat menggunakan berbagai teknologi, dan kamu harus cukup paham dalam mengaplikasikan berbagai teknologi tersebut dalam aplikasi yang kamu buat, Alasannya karena alat yang digunakan dalam ekosistem teknologi React ini terlihat sangat banyak, dan selalu dijelaskan dengan urutan yang salah.

Kamu harus memahami sesuai dengan urutan dibawah ini, **tanpa melewati ataupun memahaminya secara acak**:

* [Teknologi React](#teknologi-react)
* [`npm`](#learning-npm)
* [JavaScript “bundlers”](#learning-javascript-bundlers)
* [ES6](#learning-es6)
* [Routing](#learning-routing)
* [Flux](#learning-flux)

**Kamu tidak perlu untuk memahami semua teknologi ini untuk produktif dengan React.** Berpindah lah ke langkah selanjutnya jika memiliki masalah yang perlu untuk dipecahkan.

Sebagai tambahan, terdapat beberapa topik yang sering disebut dalam Komunitas React, termasuk "Approach terbaru". Topik dibawah ini sangat menarik, tapi cukup sulit untuk dipahami orang awam, dan tidak cukup populer dibandingkan topik diatas, serta **tidak selalu dibutuhkan untuk kebanyakan aplikasi.**
* [Inline styles](#learning-inline-styles)
* [Server rendering](#learning-server-rendering)
* [Immutable.js](#learning-immutablejs)
* [Relay, Falcor, etc](#learning-relay-falcor-etc)

## Teknologi React

Sudah menjadi miskonsepsi umum jika kamu perlu membuang banyak waktu dalam menyiapkan kebutuhan (berbagai macam dependensi) untuk memulai memahami React. Di dokumentasi resminya, kamu akan menemukan [copy-paste HTML template](https://facebook.github.io/react/docs/getting-started.html#quick-start-without-npm) yang dapat disimpan dalam bentuk `.html` file dan dapat langsung digunakan. **Tidak perlu berbagai macam dependensi lain yang dibutuhkan dalam langkah ini, dan jangan mulai mempelajari teknologi dependensi tersebut sampai kamu nyaman dengan dasar penggunaan React**

saya pikir bahwa cara termudah dalam mempelajari React yaitu dengan berdasarkan [tutorial resmi](https://facebook.github.io/react/docs/tutorial.html).

## Learning `npm`

`npm` merupakan Node.js package manager dan merupakan cara paling populer yang digunakan orang front-end dan designer dalam membagikan JavaScript code mereka. termasuk sistem modul yang disebut `CommonJS` yang memungkinkan untuk menginstall command-line tools yang ditulis dalam JavaScript. Baca [postingan ini](http://0fps.net/2013/01/22/commonjs-why-and-how/) untuk dasar kenapa `CommonJS` dibutuhkan untuk browser, atau [CommonJS Wiki](http://wiki.commonjs.org/wiki/Introduction) untuk memahami lebih lanjut tentang `CommonJS` API.

Component, library, dan modul lain yang paling sering digunakan yang terkait dengan ekosistem React, juga tersedia di `npm` seperti modul `CommonJS` dan dapat di install dengan `npm`.

## Learning JavaScript bundlers

Untuk beberapa alasan teknikal yang baik, modul `CommonJS` (dan semua yang ada di `npm`) tidak dapat digunakan secara native (di implementasikan secara spesifik) di dalam browser. kamu perlu JavaScript “bundler” untuk mem-“bundle” modul tersebut ke `.js` file yang nantinya di include ke dalam webpage dengan tag `<script>` .

Contoh dari JavaScript bundlers adalah `webpack` and `browserify`. Keduanya merupakan pilihan yang bagus, tetapi saya lebih memilih `webpack` karena mempunyai banyak fitur yang membuat proses development dari aplikasi yang besar dan kompleks menjadi lebih mudah. Dikarenakan dokumentasinya cukup rumit, saya punya [plug-and-play template untuk memulai](https://github.com/petehunt/react-webpack-template) dan saya juga menulis [panduan untuk webpack](https://github.com/petehunt/webpack-howto) untuk study kasus yang kompleks.

React juga menawarkan [secara resmi CLI tool yang disebut Create React App](https://github.com/facebookincubator/create-react-app). hal tersebut memungkinkan kamu dapat membuat React project yang didukung oleh `webpack` tanpa perlu konfigurasi. Tool tersebut masih memiliki batasan, tetapi dapat memberikanmu titik mulai yang bagus, dan Pembaruannya akan memberikan fitur tambahan. Serta terdapat sebuah fitur "ejection" yang membuat semua konfigurasi dan dependensi yang ada di salin ke project mu, sehingga kamu mempunyai kontrol penuh terhadap konfigurasi tersebut.

Perlu diingat: `CommonJS` memiliki `require()` untuk import modul yang ada, sehingga banyak orang bingung dan berfikir bahwa perlu dependensi/modul dari `require.js`. Untuk beberapa alasan teknikal, saya menyarankan untuk menghindari penggunaan modul `require.js`. dan juga modul tersebut tidak telalu populer di Ekosistem React.

## Learning ES6

Terlepas dari JSX (yang telah kamu pelajari di tutorial React), kamu mungkin menemukan beberapa syntax yang aneh dalam contoh yang diberikan. Hal ini disebut ES6, yang merupakan versi terbaru dari JavaScript, sehingga kamu mungkin belum mempelajarinya. Karena merupakan hal baru, teknologi tersebut belum di support oleh browser, tetapi modul “bundler” dapat menerjemahkannya untuk kamu dengan konfigurasi yang benar.

jika kamu ingin menyelesaikan sesuatu dengan React secara cepat, **kamu dapat melewati ES6**, atau mencoba memahaminya saat mengaplikasikannya langsung.

kamu mungkin mendengar bahwa ES6 class menjadi pilihan utama dalam membuat React component. hal ini salah. Kebanyakan orang (termasuk tim Facebook) menggunakan `React.createClass()`.

## Learning routing

Istilah “Single-page applications” sedang populer belakangan ini. SPA merupakan web pages yang di load sekali, dan ketika pengguna meng-click sebuah link atau tombol, JavaScript yang berjalan pada halaman tersebut meng-update address bar, tetapi web page tidak di refresh. Pengaturan dari address bar diatur oleh **router**.

Router paling populer di Ekosistem React adalah [react-router](https://github.com/rackt/react-router). jika kamu membuat SPA, gunakan react-router kecuali kamu memiliki alasan yang bagus untuk tidak menggunakannya.

**jangan menggunakan router jika tidak membuat single-page application**. lagipula, Kebanyakan project dimulai dari komponen yang kecil yang nantinya membentuk aplikasi yang kompleks.

## Learning Flux

Kamu mungkin telah mengenal Flux. Terdapat *banyak sekali* mis-informasi tentang Flux diluar sana.

Banyak orang membuat aplikasi dan juga telah mendefinisikan data model mereka, lalu mereka berfikir harus menggunakan Flux untuk melakukannya **Ini merupkan cara berfikir yang salah dalam mengadopsi teknologi Flux. Flux hanya harus ditambahkan saat telah terdapat banyak komponen.**

React komponen disusun sesuai hirarki. Kebanyakan, data model kamu miliki juga tersusun dalam hirarki. didalam situasi seperti ini Flux tidak terlalu berguna. Terkadang, bagaimanapun data model kamu tidak tersusun secara hirarki. Ketika React komponen memulai menerima `props` yang besar/banyak, atau kamu memiliki beberapa komponen yang nantinya akan menjadi lebih kompleks, saat itulah kamu perlu menggunakan Flux.

**Kamu akan tau kapan membutuhkan Flux. Jika kamu tidak yakin untuk memerlukannya, kamu tidak perlu menggunakan Flux**

jika kamu memutuskan untuk menggunakan Flux, librari yang sangat populer dan terdokumentasi secara baik adalah [Redux](http://redux.js.org/). Terdapat *banyak sekali* alternatif yang ada diluar sana, dan kamu akan kebingungan untuk mengevaluasinya, tetapi saran saya, pilihlah librari yang paling populer saja.

## Learning inline styles

Pre-React, banyak orang memakai CSS style lagi dengan stylesheet yang kompleks yang di buat oleh preprocessor seperti SASS. Karena React memungkinkan membuat kembali komponen yang telah ada dengan mudah, stylesheet mu akan menjadi lebih simple. Di kebanyakan komunitas (termasuk saya) bereksperimen untuk dapat menghilangkan tool stylesheet.

Ini merupakan ide yang cukup gila karena beberapa alasan. hal ini membuat query media semakin sulit, dan ada kemungkinan terdapat beberapa batasan menggunakan teknik ini. **ketika memulai menggunakan React, lakukan styling yang biasa kamu lalukan saja.**

Ketika kamu telah terbiasa dengan bagaiman React bekerja, kamu dapat mencari teknik alternatif. Yang paling populer adalah [BEM](https://en.bem.info/). saya merekomendasikan untuk tidak menggunakan CSS preprocessor, karena React memberikanmu kebebasan untuk menggunakan kembali style yang ada (menggunakan kembali komponen) dan JavaScript bundler dapat membuat stylesheet yang lebih efisien untuk kamu (Aku pernah [berbicara tentang hal ini di OSCON](https://www.youtube.com/watch?v=VkTCL6Nqm6Y)). Dalam pembicaraan tersebut, React, seperti JavaScript librari lainnya, juga akan bekerja dengan normal saat menggunakan CSS preprocessor.

Alternatifnya, kamu juga dapat menggunakan [Modul CSS](http://glenmaddern.com/articles/css-modules), lebih spesifiknya [react-css-modules](https://github.com/gajus/react-css-modules). Dengan Modul CSS, kamu masih menulis CSS (atau SASS/LESS/Stylus), tetapi kamu juga dapat mengatur dan membuat file CSS seperti yang kamu lakukan dengan inline styles dalam React. Dan kamu tidak perlu khawatir dengan pengaturan nama kelas yang ada seperti menggunakan metodologi seperti BEM, seperti semuanya telah diatur dengan sistem modul yang ada.

## Learning server rendering

Server rendering sering dikenal sebagai "universal" atau "isomorphic" JS. ini berarti React komponen yang kamu miliki akan dirender ke static HTML di server. ini meningkatkan performa inisialisasi awal karena pengguna tidak perlu menunggu file JS untuk di download saat melihat inisialisasi UI, dan React dapat menggunakan kembali hasil render HTML dari server sehingga tidak perlu di buat di client-side.

Kamu membutuhkan server rendering jika kamu nyadari bahwa inisial rendering sangat lama atau jika kamu ingin meningkatkan rangking search engine dari webpage. Saat ini Google meng-index konten yang bersifat client-rendered, karena sejak January 2016 cara menghitung rangking webpage berubah dan berpengaruh terhadap rangking webpage, hal ini dikarenakan performa dari sisi render client-side di ikut sertakan dalam variable perhitungannya.

Server rendering membutuhkan banyak tool atau dependensi yang diperlukan. Karena React komponen dapat dibuat tanpa perlu server rendering, kamu hanya perlu membuat aplikasimu dulu dan mengimplementasikan server rendering nantinya. Kamu juga tidak perlu menulis ulang kode React komponen lagi untuk bisa digunakan di server rendering.

## Learning Immutable.js

[Immutable.js](https://facebook.github.io/immutable-js/) menyediakan struktur data yang membantumu dalam mengatasi masalah performa ketika membangun sebuah aplikasi React. Librari ini sangat bagus, dan kamu mungkin akan sering menggunakannya nanti, tetapi teknologi ini tidak dibutuhkan sampai kamu memperhatikan sisi performa aplikasi.

## Learning Relay, Falcor etc

Teknologi ini memungkinkan kamu untuk mengurangi permintaan AJAX. Teknologi ini sangat baru, jika kamu tidak punya masalah dengan permintaan AJAX yang banyak, kamu tidak membutuhkan Relay atau Falcor.
