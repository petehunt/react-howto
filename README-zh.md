# 如何学习React

如果你是一个 React (或者前端) 新手, 出于以下的原因, 你可能会对这个生态圈感到困惑:

* React 的目标群体历来是喜欢尝试新事物的开发者和前端专家.
* Facebook 只开源了他们在实际使用的, 因此他们没有关注那些比 Facebook 小的工程需求.
* 现有的 React 指引水平层次不齐.

在本文中, 我会假设你已有使用 HTML, CSS 和 JavaScript 开发网页的基础.

## 为什么要听我的?

关于 React, 现在已经有大量的相互冲突的建议了, 为什么要听我的?

因为我是在 Facebook 构建并开源 React 的最初成员之一. 现在我离开了 Facebook 并加入了一家初创公司, 所以我也不会站在 Facebook 的立场上来表态.

## 如何踏入 React 生态圈

所有的软件都是建立在某个技术栈之上的, 你需要对整个技术栈有足够深入的理解, 才能建造你的应用. 为什么 React 生态圈的工具似乎总让人感觉压力山大呢, 因为它总是以错误的顺序被解释:

你应该按照以下的顺序进行学习, **而不是跳着学或者同时学习**:

* [React](#user-content-学习-react-本身)
* [`npm`](#user-content-学习-npm)
* [JavaScript “bundlers”](#user-content-学习-javascript-打包工具)
* [ES6](#user-content-学习-es6)
* [Routing](#user-content-学习路由-routing)
* [Flux](#user-content-学习-flux)
* [Immutable.js](#user-content-学习-immutablejs)
* [Relay, Falcor 等](#user-content-learning-relay-falcor-等)

并且: **你不需要把这些都学完才去使用 React.** 只需要在你遇到问题需要解决的时候, 才进入下一步的学习.

## 学习 React 本身

有一种常见的误解是: 你需要花费大量时间在配置工具上, 然后才开始学习 React. 在官方文档里, 你可以找到 [copy-paste HTML template](https://facebook.github.io/react/docs/getting-started.html#quick-start-without-npm). 只需要保存为 `.html` 文件, 你就可以马上开始学习了. **这个步骤不需要任何工具, 你也无需额外学习工具使用, 直到你能熟练掌握 React 基础.**

我依然觉得, 学习 React 最简单的方法是通过官方教程 [the official tutorial](https://facebook.github.io/react/docs/tutorial.html).

## 学习 `npm`

`npm` 是 Node.js 包管理工具, 也是前端工程师和设计师分享 JavaScript 代码最流行的方式. 它包含了名为 `CommonJS` (请 Google 一下 -- 它很重要) 的模块系统, 让你可以安装 JavaScript 写的命令行工具.

在 React 生态圈中, 大部分可重用的组件、库和工具遵循 `CommonJS` 模块规范, 可通过 `npm` 来安装.

## 学习 JavaScript 打包工具

出于若干技术原因, `CommonJS` 模块 (也就是 `npm` 里的所有内容) 不能直接用到浏览器. 你需要一个 JavaScript “打包工具(bundler)” 来把这些模块打包成 `.js` 文件, 使你可以在网页中通过 `<script>` 标签引入它们.

JavaScript 打包工具包括有 `webpack` 和 `browserify`. 它们都是好的选择, 但我个人更喜欢 `webpack` , 因为它有许多功能简化大型应用开发. 鉴于 webpack 文档可能令人感到困惑, 我也写了两篇文章: [plug-and-play template for getting started](https://github.com/petehunt/react-webpack-template) 和针对更复杂用例的 [how-to guide for webpack](https://github.com/petehunt/webpack-howto).

要记住的一点: `CommonJS` 使用了 `require()` 函数来引入模块, 因此许多人对此感到疑惑, 并认为需要导入 `require.js` 到工程里. 出于若干技术原因, 我建议你避免使用 `require.js`. 它在 React 生态圈并不流行.

## 学习 ES6

在 JSX (你会在 React tutorial 中学习到) 以外, 你可能会注意到 React 例子中一些有趣的语法. 这被称为 ECMAScript6, 是 JavaScript 的最新版本. 由于 ES6 很新, 你可能还没学习到, 浏览器也可能尚未兼容, 但别担心, 你的打包工具会为你自动转换成兼容代码.

如果你只想要使用 React 来把事情做完, **你可以跳过 ES6 的学习,** 或者留到以后再学习.

## 学习路由 (routing)

“单页面应用” 是时下的技术热点. 当网页加载完成, 用户点击链接或者按钮的时候, JavaScript 会更新页面和改变地址栏, 但网页不会刷新. 地址栏的管理就是通过 **路由(router)** 来完成的.

目前 React 生态圈最受欢迎的路由解决方案是 [react-router](https://github.com/rackt/react-router). 如果你正在创建一个单页面应用, 有什么理由不去使用它呢?

**如果你创建的并非单页面应用, 请不要使用路由.** 无论如何, 大部分项目都是从大型应用中的小组件开始的.

## 学习 Flux

你可能听过 Flux, 不过关于 Flux 有大量的错误资讯.

许多人一坐下来刚开始构建应用, 就认为需要用 Flux 来定义他们的数据模型. **这样采用 Flux 是不对的, Flux 应该在大量组件被建立完成以后才被引入.**

React 组件之间存在层级关系. 在很多时候, 你的数据模型也跟随这种层级. 这种情况下, Flux 不会给你很大帮助. 但有些时候, 你的数据模型没有层次, 当你的 React 组件开始接受没有关联的 `props` 的时候, 或者当小部分组件开始变得复杂的时候, 你才可能需要看看 Flux.

**你会知道什么时候需要用 Flux. 如果你不确定是否需要用它, 你就不需要它.**

如果你决定使用 Flux, 现在最流行的、文档最全的 Flux 库是 [Redux](http://redux.js.org/). 当然也有许多其他选择, 你或者会有兴趣尝试使用它们, 但我的建议是只需要用最流行的那一个就足够了.

## 学习 Immutable.js

[Immutable.js](https://facebook.github.io/immutable-js/) 提供了一系列的数据结构, 以帮助解决构造 React 应用时的某些性能问题. 这是一个很棒的库, 你可能会在应用发展的过程里大量用到它, 但直到你在意识到性能问题以前, 它是完全不必要的.

## Learning Relay, Falcor 等

这些技术可以帮你减少 AJAX 请求数, 它们仍然是非常前沿的, 所以如果你没有遇到过多 AJAX 请求的问题, 就不需要用到 Relay 或者 Falcor.