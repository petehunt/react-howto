# react-howto

Sekiranya anda baru kepada React (atau `frontend` secara am) anda mungkin mendapati ekosistemnya bercelaru. 

Berikut adalah beberapa sebab kenapa ianya berlaku:

* React dari segi sejarahnya disasarkan kepada para `early-adopters` dan para pakar.
* Facebook hanya open-source apa yang mereka sendiri guna, jadi ia tidak memberi fokus kepada tooling untuk projek yang lebih kecil dari Facebook.
* Terdapat banyak bahan marketing yang disalahgambarkan sebagai paduan kepada React

Sepanjang dokumen ini, saya akan menganggap anda pernah membina laman web menggunakan HTML, CSS dan Javascript.

## Kenapa anda perlu percaya pada saya?

Terdapat terlalu banyak nasihat yang bercelaru mengenai React di luar sana: kenapa percayakan saya?

Saya adalah salah seorang ahli asal pasukan Facebook yang membina dan open-source React. Saya tidak lagi di Facebook dan sekarang berada di sebuah syarikat startup yang kecil, jadi saya juga mempunyai perspektif yang diluar perspektif Facebook. 

## Bagaimana mahu bermula dengan ekosistem React

Semua perisian adalah dibina di atas susunan beberapa teknologi, dan anda mesti memahami secukupnya susunan tersebut untuk membangunkan perisian anda.  Sebab utama megapa ekosistem React nampak terlalu sukar untuk difahami ialah kerana ianya selalu dijelaskan di dalam susunan yang tidak tepat.  

Anda sepatutya belajar, di dalam susunan ini, **tanpa melangkau ke hadapan atau belajar secara selari**:

* [React](#belajar-react)
* [`npm`](#belajar-npm)
* [JavaScript “bundlers”](#belajar-javascript-bundlers)
* [ES6](#belajar-es6)
* [Routing](#belajar-routing)
* [Flux](#belajar-flux)

**Anda tidak perlu mempelajari semua ini untuk menjadi produktif menggunakan React.** Anda hanya perlu melangkah ke hadapan sekiranya ada masalah yang memerlukan langkah tersebut sebagai penyelesaian.

Sebagai tambahan, terdapat beberapa topik yang selalu dibincangkan di dalam komuniti React adalah tergolong di dalam "bleeding edge".  Topik-topik di bawah adalah menarik, tetapi mereka selalunya susah untuk difahami, tidak sebegitu popular sebagaimana topik-topik di atas dan **tidak semestinya digunakan oleh kebanyakan perisian**.

* [Inline styles](#belajar-inline-styles)
* [Server rendering](#belajar-server-rendering)
* [Immutable.js](#belajar-immutablejs)
* [Relay, Falcor, dan lain-lain](#belajar-relay-falcor-dan-lain-lain)

## Belajar React

Silapfaham yang paling biasa adalah anda perlu membuang banyak masa membuat `tooling setup` untuk mula belajar React.  Di dalam dokumentasi rasmi anda akan menjumpai [copy-paste HTML template](https://facebook.github.io/react/docs/getting-started.html#quick-start-without-npm) yang anda boleh simpan di dalam fail '.html' dan terus bermula. 

Saya masih berpendapat cara paling mudah untuk belajar React adalah melalui [tutorial rasmi](https://facebook.github.io/react/docs/tutorial.html).

## Belajar `npm`

`npm` ialah `package manager` untuk Node.js dan merupakan cara paling popular untuk `front-end engineer` dan `designer` berkongsi kod Javascript.  Baca [artikel ini](http://0fps.net/2013/01/22/commonjs-why-and-how/) untuk mengetahui latarbelakang kenapa `CommonJS` menjadi keperluan kepada browser, atau baca [CommonJS Spec Wiki](http://wiki.commonjs.org/wiki/Introduction) untuk maklumat lanjut mengenai `CommonJS` API.

Banyak komponen, `libraries` dan `tools` di dalam ekosistem React adalah tersedia sebagai modul `CommonJS` dan boleh dipasang menggunakan `npm`. 

## Belajar `Javascript bundlers`

Untuk beberapa sebab teknikal, modul-modul `CommonJS` (iaitu kesemua di dalam `npm`) tidak dapat digunakan secara `native` di dalam `browser`.  Anda memerlukan `Javascript bundler` untuk mem-bundle kesemua modul tersebut ke dalam fail `.js` yang kemudiannya disertakan di dalam `web page` dengan menggunakan tag `<script>`.

Antara contoh `Javascript bundler` termasuklah `webpack` dan `browserify`.  Keduanya ada pilihan yag bagus, tetapi saya memilih `webpack` kerana ia mengandungi banyak `feature` yang memudahkan pembangunan perisian skala besar.  Oleh kerana dokumentasi rasminya boleh mengelirukan, saya menyediakan [plug-and-play template for getting started](https://github.com/petehunt/react-webpack-template) dan menulis [panduan kepada webpack](https://github.com/petehunt/webpack-howto) untuk penggunaan yang lebih kompleks. 

Satu perkara yang perlu diberi perhatian: `CommonJS` menggunakan function `require()` untuk `import modules`, menyebabkan kekeliruan dan ramai yang menyangka ianya berkaitan dengan projek `require.js`.  Untuk beberapa sebab teknikal, saya cadangkan anda untuk menghindari dari menggunakan `require.js`.  Ianya juga tidak begitu popular di dalam ekosistem React.

## Belajar ES6

Selain daripada JSX (yang anda pelajari di dalam tutorial React), anda mungkin akan menemui beberapa sintaks yang agak pelik di dalam contoh-contoh aplikasi React.  Ini dipanggil ES6, dan ianya adalah versi terbaharu Javascript, jadi mungkin anda masih belum belajar mengenainya.  Oleh sebab ianya masih baharu, ianya masih belum disokong penggunaanya di dalam `browser`, tetapi `bundler` anda akan membuat penyesuian yang diperlukan.

Sekiranya anda cuma mahu menghasilkan sesuatu hanya dengan React, **anda boleh abaikan belajar ES6**, atau ambil masa belajar sedikit demi sedikit.

Anda mungkin telah menonton beberapa ceramah yang mengatakan penggunaan `ES6 classes` adalah cara yang sepatutnya digunakan untuk membina komponen React. Ini tidak benar.  Kebanyakan pengguna (termasuk Facebook) menggunakan kaedah `React.createClass()`.

## Belajar `routing`

“Single-page applications” adalah hangat diperkatakan hari ini.  Mereka adalah `web page` yang di-load sekali sahaja, dan apabila pengguna memetik `link` atau `button`, `address bar` pada `browser` akan di-update oleh aplikasi Javascript dan tidak memerlukan `web page` tersebut untuk `refresh`.  Perubahan pada `address bar` tersebut diuruskan oleh apa yang dikenali sebagai **router**.

`Router` yang paling popular di dalam ekosistem React adalah [react-router](https://github.com/rackt/react-router).  Sekiranya anda mebangunkan aplikasi berbentuk `single-page application`, penggunaannya adalah disarankan, kecuali jika anda mempuyai alasan untuk menghindarinya.

**Jangan gunakan `router` sekiranya anda bukan membina aplikasi berbentuk `single-page application`**.  Lagipun, kebanyakan projek bermula sebagai komponen di dalam satu aplikasi yang lebih besar.

## Belajar Flux

Anda mungkin pernah dengar mengenai Flux.  Terdapat *terlalu banyak* maklumat yang tidak tepat mengenai Flux di luar sana.

Ramai yang apabila mula membangunkan aplikasi dan mahu membina `data model`, mereka berpendapat Flux adalah diperlukan untuk tujuan tersebut.  **Ini adalah cara yang salah untuk menggunakan Flux.  Flux sepatutnya digunakan hanya setelah banyak komponen dibina.**

Komponen React disusun di dalam hierarki.  Kebanyakan masa, `data model` anda juga disusun mengikut hierarki.  Di dalam situasi begini, Flux tidak memberikan banyak manafaat.  Cuma kadang-kadang `data model` anda tidak disusun di dalam hierarki.  Apabila komponen React anda mula menerima `props` yang dirasakan agak pelik, atau beberapa komponen kecil anda mula menjadi kompleks, itulah masa untuk anda mula menggunakan Flux.

**Anda akan tahu bila masa Flux diperlukan. Jika anda tidak pasti anda perlukannya, anda tidak memerlukannya.**

Sekiranya anda telah memutuskan untuk menggunakan Flux, `library` yang paling popular dan mempunyai dokumentasi yang lengkap adalah [Redux](http://redux.js.org/).  Terdapat *banyak* pilihan lain, dan anda mungkin mahu mengkaji kebanyakan mereka, tetapi nasihat saya ialah supaya anda cuma memilih yang popular sahaja. 

## Belajar `inline styles`

Sebelum kewujudan React, ramai yang menggunakan `CSS styles` yag dihasilkan oleh `CSS pre-processors` seperti SASS.  Oleh kerana React telah memudahkan pembangunan `reusable components`, `stylesheet` anda sepatutnya tidak lagi kompleks.  Ramai di dalam komuniti (termasuk saya) sedang membuat kajian untuk tidak langsung menggunakan `stylesheet`.

Ini adalah idea yang agak gila jika diambilkira beberapa sebab. Ianya membuatkan `media queries` lebih susah, dan berkemungkinan terdapat kekangan pada prestasi jika teknik ini digunapakai.  **Apabila bermula dengan React, gunakan kaedah `style` yang biasa anda gunakan.**

Apabila anda mula membiasakan diri dengan bagaimana React berfungsi, anda boleh mula mencari alternatif lain. Satu yang popular adalah [BEM](https://en.bem.info/).  Saya sarankan anda mula mengurangkan penggunaan `CSS preprocessor`, oleh kerana React memberikan anda cara yang lebih baik untuk mengulang-guna `styles` ( dengan menggunakan komponen) dan melalui `Javascript bundler` anda dapat menjana `stylesheet` yang lebih efisien (saya telah memberikan [ceramah mengenai isu ini di OSCON](https://www.youtube.com/watch?v=VkTCL6Nqm6Y)).  Walaupun begitu, React, sebagaimana `Javascript library` yang lain, akan berfungsi seperti biasa biarpun dengan penggunaan `CSS preprocessor`.

Sebagai alternatif, anda juga boleh menggunakan [CSS Modules](http://glenmaddern.com/articles/css-modules), atau lebih spesifik [react-css-modules](https://github.com/gajus/react-css-modules).  Dengan CSS Modules, anda masih lagi menulis CSS (atau SASS/LESS/Stylus), tetapi anda boleh mengurus dan mencipta fail-fail CSS anda sebagaimana anda menggunakan kaedah `inline styles` melalui React. Dan anda tidak perlu runsing tentang pengurusan `class names` melalui metodologi seperti BEM, memandangkan ianya diuruskan untuk anda oleh `module system`.

## Belajar `server rendering`

`Server rendering` juga dikenali sebagai "universal" atau "isomorphic" JS. Ianya bermakna anda boleh mengambil komponen React dan `render` komponen tersebut ke dalam bentuk HTML statik di `server`.  Ini meningkatkan prestasi `startup` oleh kerana pengguna tidak perlu untuk menunggu untuk JS di-download untuk melihat UI awal, dan React dapat menggunakan komponen dari HTML di server supaya tidak perlu menjana UI tersebut di bahagian `client`.

Anda memerlukan `server rendering` apabila anda mendapati prestasi `render` awal anda terlalu perlahan atau and ingin membaiki `search engine ranking`.  Walaupun sekarang Google mengindeks kandungan yang disediakan melalui `client-render`, bermula pada Januari 2016, setiap kali pemantauan dijalankan, didapati kadungan tersebut memberikan impak negatif kemungkinan disebabkan oleh kekangan prestasi pada `client-side rendering`.

`Server rendering` masih memerlukan banyak `tooling` untuk dilaksanakan dengan betul. Anda sepatutnya membina aplikasi anda dahulu dan mengambil tahu mengenai `server rendering` kemudian.  Anda tidak akan perlu untuk menulis semula semua komponen anda untuk menggunakannya.

## Belajar Immutable.js

[Immutable.js](https://facebook.github.io/immutable-js/) menyediakan satu set `data structure` yang akan membantu untuk menyelesaikan beberapa isu prestasi ketika membina aplikasi React.  Ianya satu `library` yang hebat, dan anda mungkin akan banyak menggunakannya, tetapi ianya lansung bukan satu keperluan sehingga anda dapat memahami masalah kekangan prestasi pada aplikasi.

## Belajar Relay, Falcor dan lain-lain

Ini adalah teknologi yang membantu anda mengurangkan jumlah `AJAX requests`.  Mereka masih lagi di peringkat terlalu awal, jadi sekiranya anda tidak mempunyai masalah dengan terlalu banyak `AJAX requests`, anda tidak perlukan Relay atau Falcor.