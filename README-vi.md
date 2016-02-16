# react-howto

Nếu bạn mới làm quen với React (hoặc phần front-end nói chung) thì bạn sẽ thấy hệ sinh thái tương đối khó hiểu. Có một vài lí do giải thích cho việc đó.

* Trước đây, React mục tiêu hướng tới nhóm đối tượng tiếp cận sớm và các chuyên gia
* Facebook chỉ thực hiện chuyển thành mã nguồn mở khi mà React được thực tế sử dụng, do đó mà không có sự quan tâm vào việc phát triển công cụ cho các dự án nhỏ hơn Facebook.
* Có quá nhiều marketing ảo giả tạo dưới dạng các hướng dẫn về React.

Trong suốt tài liệu này, tôi sẽ giả sư là bạn đã từng có kinh nghiệm xây dựng web với HTML, CSS và Javascript.

## Tại sao bạn nên nghe theo tôi?

Có hàng tấn lời khuyên mâu thuẫn về React bên ngoài; vậy tại sao phải nghe theo tôi nhỉ?

Tôi là một trong những thành viên đầu tiên của nhóm Facebook tham gia xây dựng và triển khai mã nguồn mở thư viện React này. Thêm cả, vì tôi không còn làm ở Facebook nữa, nên tôi có được cái nhìn khách quan không phụ thuộc Facebook nữa.

## Làm thế nào để tương tác với hệ sinh thái của React

Tất cả các phần mềm đều được xây dựng dựa trên một tập hợp các nền tảng công nghệ, và bạn cần phải hiểu rõ về chúng đủ để xây dựng ứng dụng. Nguyên nhân khiến cho công cụ trong hệ sinh thái của React trở nên phức tạp là vì luôn bị giải thích sai thứ tự.

Bạn nền học, theo thứ tự này, **không cần bỏ qua phía trước hoặc học đồng thời**:

* [Thư viện React](#learning-react-itself)
* [`npm`](#learning-npm)
* [JavaScript “bundlers”](#learning-javascript-bundlers)
* [ES6](#learning-es6)
* [Routing](#learning-routing)
* [Flux](#learning-flux)

**Bạn không cần phải học tất cả những thứ này để có thể làm việc hiệu quả với React.** Chỉ nên chuyển sang bước tiếp theo nếu như bạn thấy có vấn đề cần được giải quyết.

Thêm nữa, có vài chủ đề thường được nhắc đến trong cộng đồng React mà khá "nóng hổi". Những chủ đề dưới đây khá là thú vị nhưng khó để có thể hiểu được và ít phổ biến hơn so với các chủ đề trên và **không cần thiết khi xây dựng ứng dụng**.

* [Inline styles](#learning-inline-styles)
* [Server rendering](#learning-server-rendering)
* [Immutable.js](#learning-immutablejs)
* [Relay, Falcor, etc](#learning-relay-falcor-etc)

## Học về React

Có một điều hay bị hiểu nhầm đó là bạn sẽ phí phạm nhiều thời gian trong việc thiết lập công cụ để bắt đầu học React. Trong tài liệu chính thống bạn sẽ thấy [copy-paste HTML template](https://facebook.github.io/react/docs/getting-started.html#quick-start-without-npm) là bạn chỉ cần lưu lại một file định dang `.html` và có thể bắt đầu ngay được. **Không cần bất cứ công cụ nào ở bước này, và đừng bắt đầu học các công cụ bổ sung cho tới khi nào bạn cảm thấy thoải mái với React một cách cơ bản.**

Tôi vẫn nghĩ cách học React đơn giản nhất đó là [tài liệu chính thống](https://facebook.github.io/react/docs/tutorial.html).

## Học về `npm`

`npm` là công cụ quản lý package của Node.js và là phương pháp phổ biến nhất để các lập trình viên front-end và các nhà thiết kế chia sẻ mã nguồn Javascript. Nó bao gồm một hệ thống quản lý module gọi là `CommonJS` và cho phép bạn cài đặt bất cứ công cụ command-line nào được viết bằng Javascript. Hãy đọc [bài này](http://0fps.net/2013/01/22/commonjs-why-and-how/) để biết vì sao `CommonJS` là cần thiết với các trình duyệt, hoặc [CommonJS Spec Wiki](http://wiki.commonjs.org/wiki/Introduction) để biết thêm về `CommonJS` API.

Hầu hết các components, thư viện và công cụ tái sử dụng trong hệ sinh thái của React đều được triển khai như là thành các module `CommonJS` và có thể cài đặt thông qua `npm`.

## Học về các công cụ đóng gói Javascript

Vì một vài lí do kĩ thuật mà module `CommonJS` (ví dụ, các thư viện trên `npm`) không thể sử dụng native trên trình duyệt. Bạn cần có một "công cụ đóng gói" Javascript để "đóng gói" các modules này thành các files `.js` mà có thể include được trên trang web qua thẻ `<script>`.

Một số ví dụ về công cụ đóng gói Javascript bao gồm `webpack` và `browserify`. Cả hai đều là sự lựa chọn tốt, nhưng tôi thích `webpack` hơn vì nó có nhiều tính năng hỗ trợ tốt cho việc xây dựng lớn một cách dễ dàng hơn. Vì tài liệu của nó khá khó hiểu, tôi có tạo ra [template để bắt đầu ngay](https://github.com/petehunt/react-webpack-template) và tôi có viết [hướng dẫn về webpack](https://github.com/petehunt/webpack-howto) với các use cases phức tạp hơn.

Một điều nên nhớ là `CommonJS` sử dụng hàm `require()` để nhập liên kết các modules, vì thế nhiều người trỏ nên thắc mắc và nghĩ nó có liên quan gì đó tới một project khác có tên là `require.js`. Vì nhiều lý do kĩ thuật, tôi khuyên bạn nên tránh sử dụng `require.js`. Nó cũng không được sử dụng phổ biến trong môi trường của React.

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

## Learning server rendering

Server rendering is often called "universal" or "isomorphic" JS. It means that you can take your React components and render them to static HTML on the server. This improves initial startup performance because the user does not need to wait for JS to download in order to see the initial UI, and React can re-use the server-rendered HTML so it doesn't need to generate it client-side.

You need server rendering if you notice that your initial render is too slow or if you want to improve your search engine ranking. While it's true that Google now indexes client-rendered content, as of January 2016 every time it's been measured it's been shown to negatively affect ranking, potentially because of the performance penalty of client-side rendering.

Server rendering still requires a lot of tooling to get right. Since it transparently supports React components written without server rendering in mind, you should build your app first and worry about server rendering later. You won't need to rewrite all of your components to support it.

## Learning Immutable.js

[Immutable.js](https://facebook.github.io/immutable-js/) provides a set of data structures that can help to solve certain performance issues when building React apps. It's a great library, and you'll probably use it a lot in your apps moving forward, but it's completely unnecessary until you have an appreciation of the performance implications.

## Learning Relay, Falcor etc

These are technologies that help you reduce the number of AJAX requests. They’re still very cutting-edge, so if you don’t have a problem with too many AJAX requests, you don’t need Relay or Falcor.
