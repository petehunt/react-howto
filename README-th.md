# react-howto

สำหรับผู้เริ่มต้นศึกษาและนำ React มาพัฒนาระบบนั้น มักจะมีความสับสนอย่างมากกับภาพรวมของ React เนื่องด้วยเหตุผลดังนี้

* เป้าหมายของ React นั้นสำหรับนักพัฒนาที่ชอบลองของใหม่ ๆ และผู้เชี่ยวชาญ

* นี่คือสิ่งที่ Facebook ใช้งาน ดังนั้นไม่ได้สนใจว่าจะนำไปใช้กับระบบที่เล็กกว่าอย่างไร

* มีเอกสารต่าง ๆ ที่แย่เอามาก ๆ เช่น React guide เป็นต้น

คาดหวังว่าทุกคนที่เข้ามาอ่านเอกสารนี้ ต้องมีความรู้และเข้าใจเกี่ยวกับการพัฒนาระบบเว็บด้วย HTML, CSS และ JavaScript

## Why should you listen to me?

ในปัจจุบันมีความแนะนำต่าง ๆ มากมายแถมขัดแย้งกันเกี่ยวกับ React

ผู้เขียนเอกสารฉบับนี้เคยร่วมทีมพัฒนา React ที่ Facebook แต่ตอนนี้ออกมาทำบริษัท Startup เอง ดังนั้นสิ่งต่าง ๆ ในเอกสารนี้จึงเป็นมุมมองจากภายนอก

## How to tackle the React ecosystem

ระบบงานต่าง ๆ สร้างอยู่ในเทคโนโลยีมากมาย ดังนั้นผู้พัฒนาจะต้องรู้และเข้าใจในเทคโนโลยีต่าง ๆ ที่ใช้ในการพัฒนาเป็นอย่างดี เมื่อกลับมาดู React พบว่ามีเครื่องมือและชุดของ library ต่าง ๆ จำนวนมากมาย ซึ่งทำให้เกิดความสับสนในการศึกษาและนำไปใช้งานอย่างมาก เหตุผลหลัก ๆ มาจากลำดับการอธิบายที่ผิดพลาด

ดังนั้นต้องทำการศึกษาตามลำดับนี้ **อย่าข้ามโดยเด็ดขาด**

* [เรียนรู้ React ด้วยตนเอง](#learning-react-itself)
* [เรียนรู้`npm`](#learning-npm)
* [เรียนรู้ JavaScript “bundlers”](#learning-javascript-bundlers)
* [เรียนรู้ ES6](#learning-es6)
* [เรียนรู้ Routing](#learning-routing)
* [เรียนรู้ Flux](#learning-flux)

**ไม่จำเป็นต้องเรียนรู้ทุกสิ่งทุกอย่างในแต่ละหัวข้อ** เรียนรู้เท่าที่จะสามารถแก้ไขปัญหาของเราได้ จากนั้นไปยังข้ออื่นต่อไป

ใน community ของ React นั้นมีหัวข้อหรือเรื่องใหม่ ๆ เกิดขึ้นอยู่เป็นประจำ แถมยากต่อการทำความเข้าใจ โดยมีความข้อที่น่าสนใจดังนี้ ***บางระบบไม่จำเป็นต้องใช้***
* [เรียนรู้ Inline styles](#learning-inline-styles)
* [เรียนรู้ Server rendering](#learning-server-rendering)
* [เรียนรู้ Immutable.js](#learning-immutablejs)
* [เรียนรู้ Relay, Falcor, etc](#learning-relay-falcor-etc)


## เรียนรู้ React ด้วยตนเอง

ความเข้าใจผิดในการเริ่มเรียนรู้ React คือการเสียเวลามากมายไปกับการติดตั้งเครื่องมือ และ configuration ระบบงาน สามารถหาได้จากเอกสารของ React เอง โดยทำการ [copy-paste HTML template](https://facebook.github.io/react/docs/getting-started.html#quick-start-without-npm) และบันทึกไฟล์ด้วยนามสกุล `.html` นี่คือการเริ่มต้นศึกษาที่ถูกต้อง **ในขั้นตอนนี้ไม่ต้องการเครื่องมือใด ๆ ทั้งสิ้น เป็นเพียงการศึกษาพื้นฐานของ React เท่านั้น จนกว่าเราจะพร้อมและเข้าใจจึงเริ่มต้นศึกษาเครื่องมืออื่น ๆ ต่อไป**

เส้นทางการเรียนรู้ React ที่ง่ายที่สุดอยู่ที่ [the official tutorial](https://facebook.github.io/react/docs/tutorial.html)

## เรียนรู้ `npm`

`npm` เป็นเครื่องมือในการจัดการ package ต่าง ๆ ของ Node.js ซึ่งได้รับความนิยมจากนักพัฒนาและนักออกแบบ ซึ่งจะมี module สำคัญชื่อว่า `CommonJS` และทำการติดตั้ง commad-line tool ต่าง ๆ ที่เขียนด้วยภาษา JavaScript สามารถอ่านเรื่อง `CommonJS` เพิ่มเติมได้จาก [this post](http://0fps.net/2013/01/22/commonjs-why-and-how/) ว่าทำไมจึงมีความสำคัญ หรืออ่านเพิ่มเติมเกี่ยวกับ `CommonJS` API ได้จาก [CommonJS Spec Wiki](http://wiki.commonjs.org/wiki/Introduction)

Reusable component, library และเครื่องมือต่าง ๆ ของ React นั้นจะมาจาก module `CommonJS` ซึ่งสามารถติดตั้งผ่าน `npm`

## เรียนรู้ JavaScript bundlers

ในเชิงเทคนิคแล้วสิ่งต่าง ๆ ใน module `CommonJS` นั้นไม่สามารถใช้งานใน browser ได้ ดังนั้นจำเป็นต้องใช้งาน JavaScript “bundler” เพื่อทำการ “bundle” สิ่งต่างของ module นี้ไปเป็นไฟล์ `.js` ซึ่งถูกเรียกใช้จาก web page ด้วย tag `<script>`

ตัวอย่างของ JavaScript bundlers เช่น `webpack` และ `browserify` โดยทั้งสองเป็นตัวเลือกที่ดี แต่ทางผู้เขียนแนะนำให้ใช้ `webpack` เพราะว่ามีความสามารถมากมายและง่ายต่อการพัฒนาระบบที่มีขนาดใหญ่ แต่ข้อเสียคือ เอกสารมันแย่มาก ๆ ทำให้เกิดความสับสนได้ จึงได้เขียนเอกสารอธิบายไว้ประกอบไปด้วย [plug-and-play template for getting started](https://github.com/petehunt/react-webpack-template) สำหรับการเริ่มต้น และ [how-to guide for webpack](https://github.com/petehunt/webpack-howto) สำหรับระบบที่มีความซับซ้อน

ทีมพัฒนาของ React มี CLI tool ชื่อว่า [Create React App](https://github.com/facebookincubator/create-react-app) ให้ใช้งาน ช่วยทำให้สามารถสร้าง React project ที่มาพร้อมกับ `webpack` โดยที่ไม่ต้องทำการ configuration อะไรเลย แน่นอนว่าย่อมมีข้อจำกัด แต่ว่าเป็นจุดเริ่มต้นที่ดีมาก ๆ ที่สำคัญเครื่องมือนี้มีการเพิ่มเติมและปรับปรุงแก้ไขความสามารถต่าง ๆ อยู่เป็นประจำ เช่น "ejection" ทำให้สามารถ copy พวก configuration และ dependency/library ต่าง ๆ เข้ามายัง project ได้

มีสิ่งหนึ่งที่ต้องเข้าใจคือ ใน module `CommonJS` นั้นจะใช้งาน function `require()` เพื่อ import หรือเรียกใช้งาน module อื่น ๆ ซึ่งเรื่องนี้ทำให้นักพัฒนาจำนวนมากเข้าใจผิดหรือสับสนกับ project `require.js` ซึ่งมันเป็นคนละเรื่องกันเลย  ที่สำคัญทางผู้เขียนยังแนะนำให้หลีกเลี่ยงการใช้งาน `require.js` อีกด้วยเนื่องจากไม่ค่อยได้รับความนิยมใน React มากนัก

## เรียนรู้ ES6

นอกเหนือจาก JSX ซึ่งเรียนรู้มาจาก React tutorial แล้ว อาจะพบเจอรูปแบบของ code ที่แปลกตาจากตัวอย่างต่าง ๆ ของ React โดยรูปแบบ code เหล่านั้นเรียกว่า ES6 ซึ่งเป็นภาษา JavaScript เวอร์ชันล่าสุด ที่ไม่จำเป็นต้องเรียนรู้ในตอนนี้ก็ได้ เนื่องจากว่ายังใหม่มาก ๆ แถม broser ต่าง ๆ ก็ยังไม่รองรับ แต่ที่สามารถใช้งานได้เนื่องจาก bundler ทำการแปลงให้นั่นเอง

ถ้าผู้ศึกษาเพียงต้องการศึกษาเพียง React เท่านั้น **สามารถข้ามหัวข้อนี้ไปได้เลย** หรือลองศึกษาเพิ่มเติมได้

อาจจะเคยดูและฟังมาว่า แนะนำให้สร้าง React component ด้วย ES6 แต่ว่ามันไม่จริงเลย เนื่องจากคนส่วนใหญ่รวมทั้ง Facebook ด้วยยังใช้ `React.createClass()` อยู่เลย

## เรียนรู้ routing

“Single-page applications”  นั้นได้รับความนิยมอย่างมาก โดยที่หน้า web ทำการโหลดเพียงครั้งเดียวเท่านั้น จากนั้นเมื่อเกิดเหตุการณ์ต่าง ๆ จากผู้ใช้งาน เช่น กดปุ่ม กด link แล้ว JavaScript จะทำเปลี่ยนแปลงและ update สิ่งต่าง ๆ บน browser โดยไม่ refresh หน้า web เลย ส่วนการจัดการ url ต่าง ๆ บน address bar ใน browser นั้น ถูกจัดการด้วยสิ่งที่เรียกว่า **router**

โดยที่ router ที่ได้รับความนิยมใน React คือ [react-router](https://github.com/rackt/react-router)

***อย่าใช้ router ถ้าไม่ได้สร้าง single-page applications*** โดยที่ระบบส่วนใหญ่เริ่มจาก component เล็ก ๆ ซึ่งอยู่ภายในระบบใหญ่นั่นเอง

## เรียนรู้ Flux

You’ve probably heard of Flux. There’s a *ton* of misinformation about Flux out there.
อาจจะเคยได้ยินคำว่า Flux มาบ้าง ซึ่งมีข้อมูลที่ผิดจำนวนมากมาย !!

A lot of people sit down to build an app and want to define their data model, and they think they need to use Flux to do it. **This is the wrong way to adopt Flux. Flux should only be added once many components have already been built.**
มีนักพัฒนาจำนวนมากคิดว่า ถ้าต้องการสร้างระบบงานและทำการกำหนด data model ต่าง ๆ ขึ้นมา จากนั้นก็นำ Flux มาใช้งานเพื่อสร้างระบบงานขึ้นมาเลย **เป็นความคิดที่ผิดมาก ๆ สำหรับการนำ Flux มาใช้**

React component นั้นจะถูกจัดเรียงเป็นลำดับชั้น ดังนั้น data model จึงอยู่ในรูปแบบเดียวกัน ซึ่งในกรณีนี้ Flux อาจจะไม่เหมาะสมเท่าไร แต่ในบางครั้ง data model อาจจะไม่เป็นลำดับชั้นก็ได้ มาดูการทำงานของ React กัน เริ่มจาก React component รับข้อมูลผ่าน `props` ซึ่งดูแล้วไม่มีอะไรถ้าจำนวน component ไม่เยอะ แต่ถ้าระบบงานเริ่มซับซ้อน จำนวน component และลำดับชั้นเริ่มเยอะ การส่งข้อมูลผ่าน props น่าจะไม่เหมาะสมเท่าไร ดังนั้นถึงเวลาที่ต้องนำ Flux มาใช้งาน

**คนใช้งานต้องรู้ว่าเมื่อไรต้องใช้ Flux ถ้ายังไม่แน่ใจยังไม่เข้าใจ แสดงว่ายังไม่จไเป็นต้องใช้งาน**

แต่ถ้าตัดสินใจแล้วว่าต้องใช้งาน Flux แนะนำให้ใช้งาน library ที่ชื่อว่า [Redux](http://redux.js.org/) แถมยังมีทางเลือกอื่น ๆ อีกมากมาย แต่แนะนำให้ใช้ library ที่ได้รับความนิยมจะดีกว่า

## เรียนรู้ inline styles

ก่อนที่ React จะถูกสร้างมานั้น นักพัฒนาจำนวนมากจะทำการเขียน CSS style เพื่อให้สามารถ reuse ได้ง่ายด้วยวิธีการที่ซับซ้อนเช่น SASS !! แต่เมื่อมี React ขึ้นมาก็ทำให้การเขียน reuse component ง่ายขึ้น และช่วยทำให้การเขียน stylesheet ซับซ้อนน้อยลง

**สำหรับการเริ่มต้นกับ React นั้นให้เริ่มจากสิ่งที่เรียบง่ายก่อน**

เมื่อเรารู้สึกว่าการนำ React มาใช้แล้วดีมีประโยชน์แล้ว แนะนำให้หาเทคนิทและวิธีการอื่นๆ มาใช้ เช่น [BEM](https://en.bem.info/) เป็นต้น คำแนะนำคือ ให้ ลด ละ เลิกการใช้งาน CSS processor ลง เนื่องจาก React นั้นทำให้การ reuse stylesheet ง่ายขึ้น ที่สำคัญ JavaScript bundler จะทำการแปลง stylesheet ที่เขียนให้อยู่ในรูปแบบที่มีประสิทธิภาพมากยิ่งขึ้นให้อีกด้วย สามารถดู VDO เพิ่มเติมได้จากงาน [OSCON](https://www.youtube.com/watch?v=VkTCL6Nqm6Y)

ไม่เพียงแค่นี้ ยังมีทางเครื่องมืออื่น ๆ อีก เช่น [CSS Modules](http://glenmaddern.com/articles/css-modules) และ [react-css-modules](https://github.com/gajus/react-css-modules) โดยที่ CSS module นั้นยังสามารถเขียน CSS/SASS/LESS/Stylus ได้อีกด้วย

## เรียนรู้ server rendering

Server rendering นั้นมักจะถูกเรียกว่า "universal" หรือ "isomorphic" คือการที่ render React component ไปอยู่ในรูปแบบของ static HTML เพื่อปรับปรุงประสิทธิภาพของระบบงาน เนื่องจากไม่ต้องทำการ download JavaScript มาเพื่อทำงาน อีกทั้ง React สามารถ reuse static HTML เหล่านี้มาใช้ได้อีกด้วย

Server rendering จะมีประโยชน์เมื่อการ render ของระบบช้า หรือต้องการปรับปรุง search ranking จาก Google

โดยที่ Server rendering นั้นต้องการเครื่องมือจำนวนมาก ดังนั้นสำหรับผู้เริ่มต้นให้สนใจกับการพัฒนาระบบก่อน จากนั้นค่อยมาดูเรื่อง server rendering ต่อไป เนื่องจากหลาย ๆ  component อาจจะไม่ต้องการก็ได้

## เรียนรู้ Immutable.js

[Immutable.js](https://facebook.github.io/immutable-js/) เตรียมชุดของโครงสร้างข้อมูลสำหรับช่วยแก้ไขปัญหาเรื่องประสิทธิภาพการทำงานของระบบที่พัฒนาด้วย React ไว้ให้ เป็นชุด library ที่ดีมาก ๆ ช่วยทำให้การพัฒนารวดเร็วขึ้น แต่สิ่งที่ควรจำไว้คือ ใช้เมื่อเจอปัญหาเรื่องประสิทธิภาพการทำงานของระบบ (ใช้เมื่อจำเป็นจริง ๆ เท่านั้น)

## เรียนรู้ Relay, Falcor etc

สิ่งต่าง ๆ เหล่านี้คือเทคโนโลยีที่ช่วยลดจำนวนการส่ง AJAX request ไปยังฝั่ง server แน่นอนว่า ถ้าระบบงานที่พัฒนาจะยังมีปัญหาเรื่องจำนวน request ที่ส่งไปยัง server มากจนเกินไปก็ยังไม่จำเป็นต้องใช้งาน
