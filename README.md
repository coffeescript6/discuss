# CoffeeScript 6.0
*CoffeeScript is dead – long live CoffeeScript!*
```
                                              ,--.
                                             /  .'
                                            .  / -.
        _____       __  __                  | .-.  '
      / ____|     / _|/ _|                  ' \  |  |
     | |     ___ | |_| |_ ___  ___     .-`` \  `'  / '-.
     | |    / _ \|  _|  _/ _ \/ _ \   (      `----'     )
     | |___| (_) | | | ||  __/  __/   |`-..________ ..-'|
      \_____\___/|_| |_| \___|\___|   |                 |
                                      |                 ;--.
       _____           _       _      |                (__  \
      / ____|         (_)     | |     |                 | )  )
     | (___   ___ _ __ _ _ __ | |_    |                 |/  /
     \___ \ / __| '__| | '_ \| __|    |                 (  /
     ____) | (__| |  | | |_) | |_     |                 |/
    |_____/ \___|_|  |_| .__/ \__|    |                 |
                       | |             `-.._________..-'
                       |_|

```
This repo intends to serve as a place to discuss a new, community-driven CoffeeScript built on ES6+. 

[Open an issue](https://github.com/coffeescript6/discuss/issues/new) to propose an idea or raise a question!


## Background

CoffeeScript is a beloved language, but [has languished](https://github.com/jashkenas/coffeescript/issues/4078#issuecomment-231246672) while ES6 has grown. 
@jashkenas [encouraged es6 contributions](https://github.com/jashkenas/coffeescript/issues/4078#issuecomment-177468643) but little has been forthcoming, possibly because there just isn't enough juice left in CoffeeScript as we know it today. 

Frankly, the leadership of CoffeeScript seems (understandably) burnt-out. Rather than asking reticent maintainers to build this for us, let's push forward ourselves. This may be a rewrite, a fork, or some combination – possibly building on [CoffeeScriptRedux](https://github.com/michaelficarra/CoffeeScriptRedux), [Decaf](https://github.com/rainforestapp/decaf/), or others.


## Goals

One clear goal of CS6 would be adoption of ES6+ features, either overwriting CoffeeScript features or adding new ones where missing. 

A possible second goal would be to take this opportunity to rethink certain aspects of CoffeeScript. This might include new features that push the JavaScript ecosystem forward, modified syntax to help CS6 be more welcoming to newcomers, and the removal from (or modification of) less-useful/confusing features.


## Open Questions

There are a number of questions to answer about a modern successor to CoffeeScript, such as: 

- ES6 Compatibility
  - How to handle...
  - let/const/var?
  - async/await? 
  - getters/setters? 
  - static properties, methods, etc?
  - for in/for of?
  - decorators (and their possible clash with @properties)?
- Should types (eg; via Flow) be supported? If so, how?
- What should the compiler look like? 
- What level of backwards-compatibility with CoffeeScript should be targeted?
- Should new features be added? Which ones? What should the bar for new features be?
- What are the biggest warts in CoffeeScript that ought to be removed or patched?

... and surely many more. Kindly [open an issue](https://github.com/coffeescript6/discuss/issues/new) to open a discussion on any of the above, or similar, topics!


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
