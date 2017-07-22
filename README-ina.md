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

Component, libaray, dan modul lain yang paling sering digunakan dan terkait dengan ekosistem React juga tersedia seperti modul `CommonJS` dan dapat di install dengan `npm`.

## Learning JavaScript bundlers

For a number of good technical reasons `CommonJS` modules (i.e. everything in `npm`) cannot be used natively in the browser. You need a JavaScript “bundler” to “bundle” these modules into `.js` files that you can include in your web page with a `<script>` tag.

Examples of JavaScript bundlers include `webpack` and `browserify`. Both are good choices, but I prefer `webpack` since it has a lot of features that make development of large apps easier. Since its documentation can be confusing, I have a [plug-and-play template for getting started](https://github.com/petehunt/react-webpack-template) and I wrote a [how-to guide for webpack](https://github.com/petehunt/webpack-howto) for more complex use cases.

React also now offers [an officially supported CLI tool called Create React App](https://github.com/facebookincubator/create-react-app). It lets you create React projects powered by `webpack` without any configuration. It has its limitations, but it can serve as a great starting point, and its updates will add more features over time. It also offers an "ejection" feature that copies all configs and dependencies into your project so you have full control over them.

One thing to keep in mind: `CommonJS` uses the `require()` function to import modules, so a lot of people get confused and think that it has something to do with a project called `require.js`. For a number of technical reasons, I would suggest that you avoid `require.js`. It’s also not very popular in the React ecosystem.

## Learning ES6

Outside of JSX (which you learned in the React tutorial), you may see some funny syntax in React examples. This is called ES6, and it’s the latest version of JavaScript so you may not have learned it yet. Since it’s so new, it’s not supported in browsers yet, but your bundler can translate it for you with the proper configuration.

If you just want to get things done with React, **you can skip learning ES6**, or try to pick it up along the way.

You may see some talk about ES6 classes being the preferred way to create React components. This is untrue. Most people (including Facebook) are using `React.createClass()`.

## Learning routing

“Single-page applications” are all the rage these days. These are web pages that load once, and when the user clicks on a link or a button, JavaScript running on the page updates the address bar, but the web page is not refreshed. Management of the address bar is done by something called a **router**.

The most popular router in the React ecosystem is [react-router](https://github.com/rackt/react-router). If you’re building a single-page application, use it unless you have a good reason not to.

**Don’t use a router if you aren’t building a single-page application**. Most projects start out as smaller components inside of a larger application anyway.

## Learning Flux

You’ve probably heard of Flux. There’s a *ton* of misinformation about Flux out there.

A lot of people sit down to build an app and want to define their data model, and they think they need to use Flux to do it. **This is the wrong way to adopt Flux. Flux should only be added once many components have already been built.**

React components are arranged in a hierarchy. Most of the time, your data model also follows a hierarchy. In these situations Flux doesn’t buy you much. Sometimes, however, your data model is not hierarchical. When your React components start to receive `props` that feel extraneous, or you have a small number of components starting to get very complex, then you might want to look into Flux.

**You’ll know when you need Flux. If you aren’t sure if you need it, you don’t need it.**

If you have decided to use Flux, the most popular and well-documented Flux library is [Redux](http://redux.js.org/). There are *a lot* of alternatives out there, and you’ll be tempted to evaluate lots of them, but my advice is to just stick with the most popular one.

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
