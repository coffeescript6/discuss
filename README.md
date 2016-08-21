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

This repo intends to serve as a place to discuss a new, community-driven CoffeeScript built on ES2015+. 

[Open an issue](https://github.com/coffeescript6/discuss/issues/new) to propose an idea or raise a question!

You can also drop by this [Gitter Chatroom](https://gitter.im/csnext/Lobby).

## Background

CoffeeScript is a beloved language, but [has languished](https://github.com/jashkenas/coffeescript/issues/4078#issuecomment-231246672) while ES2015 (ES6) has grown. @jashkenas [encouraged es6 contributions](https://github.com/jashkenas/coffeescript/issues/4078#issuecomment-177468643) but little has been forthcoming, possibly because there just isn't enough juice left in CoffeeScript as we know it today. 

Frankly, the leadership of CoffeeScript seems (understandably) burnt-out. Rather than asking reticent maintainers to build this for us, let's push forward ourselves. This may be a rewrite, a fork, or some combination – possibly building on [CoffeeScriptRedux](https://github.com/michaelficarra/CoffeeScriptRedux), [Decaf](https://github.com/rainforestapp/decaf/), or others.

## The Problem

First, let’s explictly define the problem we’re trying to solve: CoffeeScript is losing marketshare. It becomes harder to choose CoffeeScript for a project when fewer people use it, and when there isn’t public support for the language and a community committed to supporting it as the JavaScript ecosystem evolves. Choosing CoffeeScript for a project can also be stymied if another essential piece of the project, especially its framework, is incompatible with CoffeeScript in some way.

Many people were drawn to CoffeeScript because it offered features that JavaScript once lacked: classes, destructuring, fat-arrow functions, etc. Once ES2015 arrived and JavaScript (mostly) caught up, those people abandoned CoffeeScript back for the JavaScript they were more familiar with. Those people aren’t coming back, nor should we pursue them. With ECMAScript proposals and development proceeding at a rapid pace, we stand no chance of out-innovating the JavaScript community in inventing new language features.

Many other people, however, came to CoffeeScript for the clean, readable syntax and the many ways that the language itself helps prevent bugs, such as significant whitespace and the existential operator. CoffeeScript still has these advantages over all versions of JavaScript, and will retain them so long as ECMAScript strives for backward compatibility. But for CoffeeScript to remain a viable choice for developers, it must keep pace with the JavaScript community. At the very least it must be compatible with most popular frameworks and build tools; ideally it will also be current with the latest approved standard. The mantra of CoffeeScript is that “It’s just JavaScript”—but right now, JavaScript is ES2015.

# Proposal for the Future of CoffeeScript

## Goals

**ES2015 features that modern frameworks require, like modules and classes, must be supported in CoffeeScript ASAP.** We can’t expect developers to continue using CoffeeScript if they must choose between CoffeeScript and whatever hot new framework they want to use for their project. Support for modules is [in progress](https://github.com/GeoffreyBooth/coffeescript/pull/2).

**CoffeeScript should support as many features of ES2015+ as possible.** There is very little that ES2015 offers that CoffeeScript lacks; but whatever can be supported in a reasonable way, like `const` or `async`/`await`, should be supported. We don’t want developers to feel like choosing CoffeeScript means they’re giving up features they had in ES2015. Please refer to the [issues](https://github.com/coffeescript6/discuss/issues) of this repo for discussion around which ES2015+ features to add, and how they should be defined and implemented in CoffeeScript.

**CoffeeScript should output as much ES2015+ syntax as possible, *as ES2015+*.** With the advent of Babel, there’s no need for CoffeeScript to reinvent the wheel in finding ways to convert ES2015 features into ES5 code. CoffeeScript should simply output modern ES2015+ JavaScript, and let downstream tools convert and polyfill for compatibility. The advantage of this is that CoffeeScript will always remain modern—as more and more runtimes support more and more ES2015+ features natively, and Babel adjusts to let more native code through to the final output, nothing is required on CoffeeScript’s part to take advantage of the shifting landscape. Debugging will also be easier, for example if a CoffeeScript fat arrow shows up in DevTools as an ES2015 fat arrow. And the CoffeeScript codebase itself will be simpler; compiling `class` to `class`, for example, will require far less code than the complicated constructs the compiler creates now. And of course, our mantra: “It’s just JavaScript.”

**While adding ES2015+ features, we should maintain as much backward compatibility as possible.** There’s a lot of code out there already written in CoffeeScript. We would do our community a disservice by introducing unnecessary breaking changes. New features that are so important that adoption is essential, like classes, may require a breaking change; but features that are optional, like `let`, should only be implemented if we can do so in a backward-compatible way. Whatever one may think of the CoffeeScript syntax for existing features, that ship has sailed; there are millions of lines of code written in that syntax, and we owe it to our users to force as little refactoring as possible.

**CoffeeScript “is just JavaScript,” but it has a core tenet of its own: elegant, concise syntax.** Now that ECMAScript has more-or-less feature parity with CoffeeScript, the CoffeeScript language’s primary selling point is its clean, spare syntax that eschews unnecessary code whenever possible. As we add new features, whether based on ES2015+ or original, we must strive to maintain CoffeeScript’s simple elegance.

## The Way Forward

Here are our proposals for how to solve these problems and achieve our goals:

### Public Roadmap

The [coffeescript6 repo](https://github.com/coffeescript6) is a big step in the right direction toward remedying the issue defining CoffeeScript’s currently unclear future. When we reach a consensus, our plan should be posted on [coffeescript.org](http://coffeescript.org/) and the [README for the coffee-script repo](https://github.com/jashkenas/coffeescript).

### Leadership

We also should come up with a defined leadership structure and formal process for approving features and syntax. As great as @jashkenas is, a language that so many people depend on should not be subject to the whims of one person. [The leadership question is one that needs to be worked out.](https://github.com/coffeescript6/discuss/issues/3)

### Framework Incompatibilities: Supporting Essential ES2015 Features

CoffeeScript is hemorrhaging marketshare the longer that incompatibilities with popular frameworks and build tools go unaddressed. We must support modules and classes ASAP, and that means building them in the current compiler. In the case of classes, that probably means a flag to opt-in to new ES2015 class syntax and output. Any other missing ES2015 features that preclude CoffeeScript’s selection for a project must also be addressed immediately, as patches to the current compiler.

### Developer Happiness: Supporting Optional ES2015+ Features

Features that developers enjoy in ES2015 that are appropriate to implement in CoffeeScript, like `const`, should be implemented as time permits. These features should be implemented in a new compiler, assuming we build one; and possibly also in the old compiler too if such an implementation is easy and doesn’t break backward compatibility. Any feature implemented in both compilers should have identical syntax.

### Modernizing Output

Lastly, CoffeeScript’s output should be modernized as much as possible. Fat arrows should output as fat arrows, destructuring should output as destructuring, etc. But this should be the **last priority**—it makes our source code cleaner, and debugging eventually easier when ES2015 features are supported natively in runtimes, but otherwise ES2015 output has little benefit for developers. That said, *new* features, especially ES2015+ ones, should definitely be output as ES2015+ code.

## A New Compiler

The current CoffeeScript 1.x compiler is extremely well commented, but it really needs those comments. Understanding it will bend your brain into knots. The original goal of [CoffeeScript Redux](https://github.com/michaelficarra/CoffeeScriptRedux) was to refactor CoffeeScript’s codebase, not to add new features.

Don’t underestimate how hard it is to write your own language compiler. If it were easy, CoffeeScript Redux would have been finished; as it stands, that project was essentially abandoned a year ago.

Also don’t underestimate how hard it is to add new features to the CoffeeScript 1.x compiler. If that were easy, someone else would’ve added modules and classes to it by now.

The CoffeeScript community suffers from too many people with a lot of passion but little time to invest in development. For that reason, we consider a new-from-scratch compiler to be off the table. We’ll just end up with another Redux.

So we have only two options for starting points for our new compiler:

* The current CoffeeScript 1.x compiler.
	* Pros: already supports all existing CoffeeScript code.
	* Cons: complicated, difficult-to-understand codebase.
* The CoffeeScript Redux compiler, probably from [this PR](https://github.com/michaelficarra/CoffeeScriptRedux/pull/344).
	* Pros: better codebase, and the PR already supports many ES2015 features.
	* Cons: we inherit Redux’s issues and unfinished work, including any incompatibilities with existing CoffeeScript code.

We have until modules and classes are supported in the current compiler before we need to [choose which compiler to use as a starting point for the next phase](https://github.com/coffeescript6/discuss/issues/25).

As to where we should put our new compiler and develop it, here are two ideas: 

* Inside the current main [coffee-script repo](https://github.com/jashkenas/coffeescript), especially if we’re updating the old compiler. Currently the repo is structured such that the code in `src` is compiled and output into `lib/coffee-script`. If we want to avoid merge conflicts with any pending PRs against the repo, we should leave those folders as they are. But we could add new folders, for example `source` and `lib/coffeescript`, that contain the new compiler source code and compiled output. A flag like `output: 'modern'` would cause the new compiler (i.e. the code in `lib/coffeescript`) to be used instead of the old one. Both compilers, modern and legacy, would live on in the same repo. Bugfixes and improvements could be submitted against either.
* In a new “coffeescript” repo, inside the [coffeescript organization](https://github.com/coffeescript). We should claim the `coffeescript` name on NPM, and point it to a new repo at [https://github.com/coffeescript/coffeescript](https://github.com/coffeescript/coffeescript). This new repo would either be a fork of the original CoffeeScript repo or a migration of the CoffeeScript Redux repo (in order to preserve the old repo’s history of issues and pull requests). No opt-in flag would be necessary; by doing `npm install coffeescript` instead of `npm install coffee-script`, developers would be choosing this compiler (though we would need some way to warn them in case they intended to choose `coffee-script`).

## Name

The “CoffeeScript 6.0” name was chosen as a name for the discussion of how to modernize CoffeeScript in response to ES6. It is not intended as the name of any new compiler.

There’s no need for something fancy or new. We already have considerable recognition under the name “CoffeeScript,” so we should keep it. Let’s refer to the soon-to-be-old compiler as the Legacy CoffeeScript compiler, and the new one—well, “it’s just CoffeeScript.”

## Open Questions

Besides the [leadership](https://github.com/coffeescript6/discuss/issues/3) and [compiler starting point](https://github.com/coffeescript6/discuss/issues/25) issues mentioned above, the [Issues](https://github.com/coffeescript6/discuss/issues) for this repo covers the various ES2015+ features and discussions regarding how to implement them. If you don’t see your favorite ES2015+ feature there, or want to propose your own new feature for the language, please [open an issue](https://github.com/coffeescript6/discuss/issues/new). That’s also the place to discuss the specifics of how to move this project forward.

If you disagree with any part of this document, please [open a pull request](https://github.com/coffeescript6/discuss/pulls) with a suggested revision and we can discuss it.

## Relevant Discussions
- https://github.com/jashkenas/coffeescript/issues/4078
- https://github.com/jashkenas/coffeescript/issues/3162
- https://github.com/jashkenas/coffeescript/issues/4228
- https://github.com/jashkenas/coffeescript/issues/3832
- (might as well scroll through https://github.com/jashkenas/coffeescript/issues?utf8=%E2%9C%93&q=is%3Aissue%20is%3Aopen%20es6 )
- https://github.com/michaelficarra/CoffeeScriptRedux/issues/336
- https://github.com/michaelficarra/CoffeeScriptRedux/issues/338
