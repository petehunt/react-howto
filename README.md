# react-roadmap

If you’re new to React (or frontend in general) you may find the ecosystem confusing. There are a few reasons for this.

* React has historically been targeted at early-adopters and experts
* Facebook only open-sources what it actually uses, so it doesn’t focus on tooling for smaller-than-Facebook projects
* There’s a lot of bad marketing masquerading as React guides

Throughout this document, I’ll assume you’ve built a web page with HTML, CSS and JavaScript.

## Why should you listen to me?

There’s a ton of conflicting advice about React out there; why listen to me?

I was one of the original members of the Facebook team that built and open-sourced React. I’m no longer at Facebook and I’m now at a small startup, so I have a non-Facebook perspective as well.

## How to tackle the React ecosystem

All software is built on a stack of technologies, and you need to understand enough of that stack to build your app. The reason why the React ecosystem of tooling seems overwhelming is because it’s always explained in the wrong order.

You should learn, in this order, **without skipping ahead or learning concurrently**:

* React itself
* `npm`
* JavaScript “bundlers”
* ES6
* Routing
* Flux
* Relay, Falcor, etc

Also: **you don't need to learn all of these to be productive with React.** Only move to the next step if you have a problem that needs to be solved.

## Learning React itself

It’s a common misconception that you need to waste a lot of time setting up tooling to start to learn React. In the official documentation you’ll find a [copy-paste HTML template](https://facebook.github.io/react/docs/getting-started.html#quick-start-without-npm) that you can save in an `.html` file and get started right away. **No tooling is required for this step, and don’t start learning extra tooling until you’re comfortable with React basics.**

I still think the easiest way to learn React is [the official tutorial](https://facebook.github.io/react/docs/tutorial.html).

## Learning `npm`

`npm` stands for *Node.js package manager* and is the most popular way front-end engineers and designers share JavaScript code. It includes a module system called `CommonJS` (Google it -- it’s important) and lets you install command-line tools written in JavaScript.

Most reusable components, libraries and tools in the React ecosystem are available as `CommonJS` modules and are installed with `npm`.

## Learning JavaScript bundlers

For a number of good technical reasons `CommonJS` modules (i.e. everything in `npm`) cannot be used natively in the browser. You need a JavaScript “bundler” to “bundle” these modules into `.js` files that you can include in your web page with a `<script>` tag.

Examples of JavaScript bundlers include `webpack` and `browserify`. Both are good choices, but I prefer `webpack` since it has a lot of features that make development of large apps easier. Since its documentation can be confusing, I have a [plug-and-play template for getting started](https://github.com/petehunt/react-webpack-template) and I wrote a [how-to guide for webpack](https://github.com/petehunt/webpack-howto) for more complex use cases.

One thing to keep in mind: `CommonJS` uses the `require()` function to import modules, so a lot of people get confused and think that it has something to do with a project called `require.js`. For a number of technical reasons, I would suggest that you avoid `require.js`. It’s also not very popular in the React ecosystem.

## Learning ES6

Outside of JSX (which you learned in the React tutorial), you may see some funny syntax in React examples. This is called ES6, and it’s the latest version of JavaScript so you may not have learned it yet. Since it’s so new, it’s not supported in browsers yet, but your bundler will translate it for you.

If you just want to get things done with React, **you can skip learning ES6**, or try to pick it up along the way.

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

## Learning Relay, Falcor etc

These are technologies that help you reduce the number of AJAX requests. They’re still very cutting-edge, so if you don’t have a problem with too many AJAX requests, you don’t need Relay or Falcor.
