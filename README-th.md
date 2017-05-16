# react-howto

If you’re new to React (or frontend in general) you may find the ecosystem confusing. There are a few reasons for this.
สำหรับผู้เริ่มต้นศึกษาและนำ React มาพัฒนาระบบนั้น มักจะมีความสับสนอย่างมากกับภาพรวมของ React เนื่องด้วยเหตุผลดังนี้

* เป้าหมายของ React นั้นสำหรับนักพัฒนาที่ชอบลองของใหม่ ๆ และผู้เชี่ยวชาญ

* นี่คือสิ่งที่ Facebook ใช้งาน ดังนั้นไม่ได้สนใจว่าจะนำไปใช้กับระบบที่เล็กกว่าอย่างไร

* มีเอกสารต่าง ๆ ที่แย่เอามาก ๆ เช่น React guide เป็นต้น


Throughout this document, I’ll assume you’ve built a web page with HTML, CSS and JavaScript.
คาดหวังว่าทุกคนที่เข้ามาอ่านเอกสารนี้ ต้องมีความรู้และเข้าใจเกี่ยวกับการพัฒนาระบบเว็บด้วย HTML, CSS และ JavaScript

## Why should you listen to me?

There’s a ton of conflicting advice about React out there; why listen to me?
ในปัจจุบันมีความแนะนำต่าง ๆ มากมายแถมขัดแย้งกันเกี่ยวกับ React

I was one of the original members of the Facebook team that built and open-sourced React. I’m no longer at Facebook and I’m now at a small startup, so I have a non-Facebook perspective as well.
ผู้เขียนเอกสารฉบับนี้เคยร่วมทีมพัฒนา React ที่ Facebook แต่ตอนนี้ออกมาทำบริษัท Startup เอง ดังนั้นสิ่งต่าง ๆ ในเอกสารนี้จึงเป็นมุมมองจากภายนอก

## How to tackle the React ecosystem

All software is built on a stack of technologies, and you need to understand enough of that stack to build your app. The reason why the React ecosystem of tooling seems overwhelming is because it’s always explained in the wrong order.

ระบบงานต่าง ๆ สร้างอยู่ในเทคโนโลยีมากมาย ดังนั้นผู้พัฒนาจะต้องรู้และเข้าใจในเทคโนโลยีต่าง ๆ ที่ใช้ในการพัฒนาเป็นอย่างดี เมื่อกลับมาดู React พบว่ามีเครื่องมือและชุดของ library ต่าง ๆ จำนวนมากมาย ซึ่งทำให้เกิดความสับสนในการศึกษาและนำไปใช้งานอย่างมาก เหตุผลหลัก ๆ มาจากลำดับการอธิบายที่ผิดพลาด

You should learn, in this order, **without skipping ahead or learning concurrently**:

ดังนั้นต้องทำการศึกษาตามลำดับนี้ **อย่าข้ามโดยเด็ดขาด**

* [ศึกษา React ด้วยตนเอง](#learning-react-itself)
* [ศึกษา`npm`](#learning-npm)
* [ศึกษา JavaScript “bundlers”](#learning-javascript-bundlers)
* [ศึกษา ES6](#learning-es6)
* [ศึกษา Routing](#learning-routing)
* [ศึกษา Flux](#learning-flux)

**You don't need to learn all of these to be productive with React.** Only move to the next step if you have a problem that needs to be solved.
**ไม่จำเป็นต้องเรียนรู้ทุกสิ่งทุกอย่างในแต่ละหัวข้อ** เรียนรู้เท่าที่จะสามารถแก้ไขปัญหาของเราได้ จากนั้นไปยังข้ออื่นต่อไป

Additionally, there are a few topics that are often mentioned in the React community that are "bleeding edge". The topics below are interesting, but they're difficult to understand, are far less popular than the above topics and **aren't required for most apps**.

ใน community ของ React นั้นมีหัวข้อหรือเรื่องใหม่ ๆ เกิดขึ้นอยู่เป็นประจำ แถมยากต่อการทำความเข้าใจ โดยมีความข้อที่น่าสนใจดังนี้ *** บางระบบไม่จำเป็นต้องใช้ ***
* [Inline styles](#learning-inline-styles)
* [Server rendering](#learning-server-rendering)
* [Immutable.js](#learning-immutablejs)
* [Relay, Falcor, etc](#learning-relay-falcor-etc)


## Learning React itself

It’s a common misconception that you need to waste a lot of time setting up tooling to start to learn React. In the official documentation you’ll find a [copy-paste HTML template](https://facebook.github.io/react/docs/getting-started.html#quick-start-without-npm) that you can save in an `.html` file and get started right away. **No tooling is required for this step, and don’t start learning extra tooling until you’re comfortable with React basics.**

ความเข้าใจผิดในการเริ่มเรียนรู้ React คือการเสียเวลามากมายไปกับการติดตั้งเครื่องมือ และ configuration ระบบงาน สามารถหาได้จากเอกสารของ React เอง โดยทำการ [copy-paste HTML template](https://facebook.github.io/react/docs/getting-started.html#quick-start-without-npm) และบันทึกไฟล์ด้วยนามสกุล `.html` นี่คือการเริ่มต้นศึกษาที่ถูกต้อง **ในขั้นตอนนี้ไม่ต้องการเครื่องมือใด ๆ ทั้งสิ้น เป็นเพียงการศึกษาพื้นฐานของ React เท่านั้น จนกว่าเราจะพร้อมและเข้าใจจึงเริ่มต้นศึกษาเครื่องมืออื่น ๆ ต่อไป**

เส้นทางการเรียนรู้ React ที่ง่ายที่สุดอยู่ที่ [the official tutorial](https://facebook.github.io/react/docs/tutorial.html)

## Learning `npm`

`npm` is the Node.js package manager and is the most popular way front-end engineers and designers share JavaScript code. It includes a module system called `CommonJS` and lets you install command-line tools written in JavaScript. Read [this post](http://0fps.net/2013/01/22/commonjs-why-and-how/) for background on why `CommonJS` is necessary for browsers, or the [CommonJS Spec Wiki](http://wiki.commonjs.org/wiki/Introduction) for more on the `CommonJS` API.

`npm` เป็นเครื่องมือในการจัดการ package ต่าง ๆ ของ Node.js ซึ่งได้รับความนิยมจากนักพัฒนาและนักออกแบบ ซึ่งจะมี module สำคัญชื่อว่า `CommonJS` และทำการติดตั้ง commad-line tool ต่าง ๆ ที่เขียนด้วยภาษา JavaScript สามารถอ่านเรื่อง `CommonJS` เพิ่มเติมได้จาก [this post](http://0fps.net/2013/01/22/commonjs-why-and-how/) ว่าทำไมจึงมีความสำคัญ หรืออ่านเพิ่มเติมเกี่ยวกับ `CommonJS` API ได้จาก [CommonJS Spec Wiki](http://wiki.commonjs.org/wiki/Introduction)

Most reusable components, libraries and tools in the React ecosystem are available as `CommonJS` modules and are installed with `npm`.
Reusable component, library และเครื่องมือต่าง ๆ ของ React นั้นจะมาจาก module `CommonJS` ซึ่งสามารถติดตั้งผ่าน `npm`

## Learning JavaScript bundlers

For a number of good technical reasons `CommonJS` modules (i.e. everything in `npm`) cannot be used natively in the browser. You need a JavaScript “bundler” to “bundle” these modules into `.js` files that you can include in your web page with a `<script>` tag.
ในเชิงเทคนิคแล้วสิ่งต่าง ๆ ใน module `CommonJS` นั้นไม่สามารถใช้งานใน browser ได้ ดังนั้นจำเป็นต้องใช้งาน JavaScript “bundler” เพื่อทำการ “bundle” สิ่งต่างของ module นี้ไปเป็นไฟล์ `.js` ซึ่งถูกเรียกใช้จาก web page ด้วย tag `<script>`

Examples of JavaScript bundlers include `webpack` and `browserify`. Both are good choices, but I prefer `webpack` since it has a lot of features that make development of large apps easier. Since its documentation can be confusing, I have a [plug-and-play template for getting started](https://github.com/petehunt/react-webpack-template) and I wrote a [how-to guide for webpack](https://github.com/petehunt/webpack-howto) for more complex use cases.
ตัวอย่างของ JavaScript bundlers เช่น `webpack` และ `browserify` โดยทั้งสองเป็นตัวเลือกที่ดี แต่ทางผู้เขียนแนะนำให้ใช้ `webpack` เพราะว่ามีความสามารถมากมายและง่ายต่อการพัฒนาระบบที่มีขนาดใหญ่ แต่ข้อเสียคือ เอกสารมันแย่มาก ๆ ทำให้เกิดความสับสนได้ จึงได้เขียนเอกสารอธิบายไว้ประกอบไปด้วย [plug-and-play template for getting started](https://github.com/petehunt/react-webpack-template) สำหรับการเริ่มต้น และ [how-to guide for webpack](https://github.com/petehunt/webpack-howto) สำหรับระบบที่มีความซับซ้อน

React also now offers [an officially supported CLI tool called Create React App](https://github.com/facebookincubator/create-react-app). It lets you create React projects powered by `webpack` without any configuration. It has its limitations, but it can serve as a great starting point, and its updates will add more features over time. It also offers an "ejection" feature that copies all configs and dependencies into your project so you have full control over them.
ทีมพัฒนาของ React มี CLI tool ชื่อว่า [Create React App] (https://github.com/facebookincubator/create-react-app) ให้ใช้งาน ช่วยทำให้สามารถสร้าง React project ที่มาพร้อมกับ `webpack` โดยที่ไม่ต้องทำการ configuration อะไรเลย แน่นอนว่าย่อมมีข้อจำกัด แต่ว่าเป็นจุดเริ่มต้นที่ดีมาก ๆ ที่สำคัญเครื่องมือนี้มีการเพิ่มเติมและปรับปรุงแก้ไขความสามารถต่าง ๆ อยู่เป็นประจำ เช่น "ejection" ทำให้สามารถ copy พวก configuration และ dependency/library ต่าง ๆ เข้ามายัง project ได้

One thing to keep in mind: `CommonJS` uses the `require()` function to import modules, so a lot of people get confused and think that it has something to do with a project called `require.js`. For a number of technical reasons, I would suggest that you avoid `require.js`. It’s also not very popular in the React ecosystem.
มีสิ่งหนึ่งที่ต้องเข้าใจคือ ใน module `CommonJS` นั้นจะใช้งาน function `require()` เพื่อ import หรือเรียกใช้งาน module อื่น ๆ ซึ่งเรื่องนี้ทำให้นักพัฒนาจำนวนมากเข้าใจผิดหรือสับสนกับ project `require.js` ซึ่งมันเป็นคนละเรื่องกันเลย  ที่สำคัญทางผู้เขียนยังแนะนำให้หลีกเลี่ยงการใช้งาน `require.js` อีกด้วยเนื่องจากไม่ค่อยได้รับความนิยมใน React มากนัก

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
