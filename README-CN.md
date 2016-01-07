这是一篇很好的指导和学习React的介绍文章, 原文在[这里](https://github.com/petehunt/react-howto).

# react-howto

如果你是一个React的初学者（或者是前端的初学者）你可能会对React的生态系统感到疑惑.原因是因为以下.

* 因为历史原因, React最初的目的是给有经验的开发者或者专家使用
* React只会提供给facebook这种大型的项目使用, 并且facebook也是一直很好的使用React, 所以它不会专注解决“比facebook更小”的项目
* 然后网络上到处充斥着各种React的劣质教程

这篇文章的阅读者适合有经验的web前端开发工程师

## 为什么要相信我

网上有成千上万的关于React的建议的文章; 为什么要相信我的建议?

因为我曾经是Facebook的React开源团队的其中一个成员, 我已离开Facebook并在一家创业公司任职, 所以我不会以facebook公司的员工名义和观点来评论和分享.

## 如何理解React生态系统

所有的软件都是建立在某些技术栈, 你需要理解这些技术栈然后去创建你的应用. 之所以围绕React生态系统的工具或者技术栈混乱的原因, 是因为总是没有被按照先后或者轻重顺序来学习.

你需要按照这个顺序去学习React, **不能跳过前面或者同时学习**

* React本身
* `npm`
* JavaScript “bundlers”
* ES6
* Routing
* Flux
* Immutable.js
* Relay, Falcor, etc

然而: **并不是以上技术栈都要学习才能成为一个高效的React开发者** 只有当你遇到问题无法解决的时候, 你才需要继续看下一个技术栈

## 学习React

有一个常见的学习React的误解, 你可能以为当使用React时候需要浪费很多时间去使用或者配置工具或者环境, 在官方的文档里面, 你会发现快速使用React的例子[copy-paste HTML template](https://facebook.github.io/react/docs/getting-started.html#quick-start-without-npm), 你可以将该页面保存成`.html`文件, 然后便可以立即打开运行React. **不需要任何额外的工具, 并且在你很熟悉的使用React之前, 建议你不需要其他工具来辅助开发**

我还是觉得学习React最好的方式还是通过官方教程[the official tutorial](https://facebook.github.io/react/docs/tutorial.html)学习


## 学习 `npm`

`npm` 是node.js的包管理工具, 并且也是当前前端开发工程师和设计师最喜欢的方式来分享他们的javascript代码. 它是基于`CommonJS`的模块化系统（如果你还不了解可以google或者baidu搜索一下 -- 这个很重要哦）还可以让你安装和使用javascript写的命令行工具.

大多数React生态系统里面的组件,库,或者工具都是以`CommonJS`的规范发布并且可以通过`npm`安装

## 学习 JavaScript bundlers

对于大部分的使用`CommonJS`规范的模块（或者说npm的库）都不能直接在浏览器上面原生使用. 你必须使用一个叫“bundler”的工具去“bundle”模块, 从而成为一个个`.js`文件, 并且最终可以在页面的`<script>`标签引用.

`bundler`的工具可以使用`webpack`或者`browserify`. 它们都是很好的工具, 但是我更喜欢`webpack`, 因为可以使用它很方便开发大型的应用. 但是它的文档可能阅读起来有点费解, 你可以通过[plug-and-play template for getting started](https://github.com/petehunt/react-webpack-template) 或者看我写的这篇专门为复杂的React用例写的[how-to guide for webpack](https://github.com/petehunt/webpack-howto)

记住一点:`CommonJS` 使用 `require()` 函数来引用一个模块, 所以有些同学会觉得奇怪, 并且可能认为需要一个`require.js`的库提供这个函数来调用. 因为一些技术上的原因, 我建议避免使用`require.js`. 而且在一般React项目中很少会使用它.

## 学习 ES6

除了JSX（这个你会在第一部分React基础学习到）, 你会在React的例子里面看到一些有趣的javascript语法. 这些都是ES6的语法, 因为它是最新的javascript版本, 所以你可能没有学过. 因为ES6是全新的javascript, 所以可能浏览器不支持, 所以“bundler”会将他们翻译成浏览器认识的javascript.

如果你只是想使用React来实现并不打算使用ES6, **你完全可以忽略ES6**, 或者什么时候需要再去学习.


## 学习 routing

“Single-page applications”（单页面应用）在现在已经很常见. 只需要刷新一次, 当用户点击一个链接或者按钮, Javascript会更新地址栏的URL, 但是页面不会重新刷新. 地址栏的管理是由一个叫 **router** 的工具实现的. 

React生态系统最流行的router是[react-router](https://github.com/rackt/react-router). 如果你要创建一个单页面应用, 你没有理由不使用它.

**如果你不是创建一个单页面应用,千万不要使用它**. 

## 学习 Flux

你应该听说过Flux. 网上有铺天盖地的关于Flux的误传.

很多人开始创建一个React应用并且需要设计数据model, 然后他们认为需要使用Flux来完成. **这是一个错误的方法使用Flux. Flux使用的时机必须是当你已经完成大量的Component组件的时候才开始使用**

React组件按照一定的层级设计和整理. 大多数情况下, 你的数据model结构也是按照这种层级组合. 这种情况下, Flux不台适合你, 但是有些时候, 你的数据model结构并不是按照一定的层级组合. 当你的组件接受外来的`props`数据时, 或者你的组件开始变得复杂时, 这个时候, 你可以考虑使用Flux.

**你会知道你是否需要使用Flux. 如果你不确定, 那意味着你暂时还不需要使用到它**

如果你决定要使用Flux, 那么你可以使用最流行并且良好的文档的Flux库[Redux](http://redux.js.org/), 当然还有其他很多Flux, 你可以尝试评估它们再决定使用哪个, 不过我建议你选择最流行那个就可以了.

## 学习 Immutable.js

当你创建React应用时, [Immutable.js](https://facebook.github.io/immutable-js/) 提供一系列的数据结构可以让你更好解决性能问题. 它是一个很棒的库, 在开发你的应用过程中你会喜欢上使用它, 但是这并不是必须的, 除非你发现需要进行性能上的提升.

## 学习 Relay, Falcor 等

这些技术和技巧可以减少Ajax请求的次数, 当然如果你没有大量Ajax请求的烦恼的话, 你不必依赖Relay 或者Falcor这些前沿的技术.
