# CoffeeScript 6.0
*CoffeeScript is dead – long live CoffeeScript!*

This repo intends to serve as a place to discuss a new, community-driven CoffeeScript built on ES6+. 

[Open an issue](https://github.com/coffeescript6/discuss/issues/new) to propose an idea or raise a question!

You can also drop by this [Gitter Chatroom](https://gitter.im/csnext/Lobby).

## Project Direction

We are splitting this effort into two parts: 

1. PR's to [jashkenas/coffeescript](http://github.com/jashkenas/coffeescript) to provide support for ES6 classes and modules (aka `import`/`export`) – e.g.; [this work](https://github.com/jashkenas/coffeescript/compare/master...GeoffreyBooth:import-export?expand=1).
2. Separate repo's, optionally under this github organization, for efforts to modernize CoffeeScript – be it through a fork of jashkenas/coffeescript, a fork of coffeescriptredux, or a new codebase entirely. 

If you would like to propose/lead an effort with a broader suite of changes than can be handled with individual PR's to jashkenas/coffeescript, and are interested in the benefits of a `coffeescript6` organization and community, please:

1. Submit a PR adding a markdown file to the `proposals` dir on this repo, describing your vision.
2. We will create a repo under this organization for you, and link to it from this readme.
3. You may use this `discuss` repo and the gitter chatroom for discussion. 

If a clear leader emerges, the hope is that we'll all rally around that.

## Background

CoffeeScript is a beloved language, but [has languished](https://github.com/jashkenas/coffeescript/issues/4078#issuecomment-231246672) while ES6 has grown. 
@jashkenas [encouraged es6 contributions](https://github.com/jashkenas/coffeescript/issues/4078#issuecomment-177468643) but little has been forthcoming, possibly because there just isn't enough juice left in CoffeeScript as we know it today. 

Frankly, the leadership of CoffeeScript seems (understandably) burnt-out. Rather than asking reticent maintainers to build this for us, let's push forward ourselves. This may be a rewrite, a fork, or some combination – possibly building on [CoffeeScriptRedux](https://github.com/michaelficarra/CoffeeScriptRedux), [Decaf](https://github.com/rainforestapp/decaf/), or others.


## Goals

One clear goal of CS6 would be adoption of ES6+ features, either overwriting CoffeeScript features or adding new ones where missing. 

A possible second goal would be to take this opportunity to rethink certain aspects of CoffeeScript. This might include new features that push the JavaScript ecosystem forward, modified syntax to help CS6 be more welcoming to newcomers, and the removal from (or modification of) less-useful/confusing features.


## The name
Given that this project has no official blessing from @jashkenas and co – and may never receive it – the name "CoffeeScript 6.0" should be thought of as a placeholder. 


## Possible Alternatives
There are a number of interesting new languages that have sprung up, some of them listed below. None seem to capture the essence of "unfancy JavaScript" accomplished in CoffeeScript, but may be sources of inspiration nonetheless:

- [LiveScript](http://livescript.net/) – Extremely feature-rich, closest to CoffeeScript I've seen, functional-oriented
- [Earl Grey](http://www.earl-grey.io/) – Python-ish with macros
- [PureScript](http://www.purescript.org/) – Haskell-based, recommended by @michaelficarra (author of CoffeeScriptRedux)
- [Elm](http://elm-lang.org/) – Haskell-based, only works in the browser.
- [Frappe](https://github.com/lydell/frappe) (just an idea)
- [TacoScript](https://github.com/forivall/tacoscript) (in the early stages)


## Relevant Discussions
- https://github.com/jashkenas/coffeescript/issues/4078
- https://github.com/jashkenas/coffeescript/issues/3162
- https://github.com/jashkenas/coffeescript/issues/4228
- https://github.com/jashkenas/coffeescript/issues/3832
- (might as well scroll through https://github.com/jashkenas/coffeescript/issues?utf8=%E2%9C%93&q=is%3Aissue%20is%3Aopen%20es6 )
- https://github.com/michaelficarra/CoffeeScriptRedux/issues/336
- https://github.com/michaelficarra/CoffeeScriptRedux/issues/338
