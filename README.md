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

This repo intends to serve as a place to discuss the future of CoffeeScript, especially as it relates to ES2015+ (ES6).

[Open an issue](https://github.com/coffeescript6/discuss/issues/new) to propose an idea or raise a question! This is also where proposals for adding features to CoffeeScript or updating current features’ output can be discussed. As proposals reach consensus, the feature will be added [below](features-implemented) and to the [project board](https://github.com/coffeescript6/discuss/projects/1). No code will be developed here; the “CoffeeScript 6” project is one of discussion, directed at updating CoffeeScript itself. You can also drop by this [Gitter chat room](https://gitter.im/csnext/Lobby).

## Background

CoffeeScript is losing marketshare. That matters because it becomes harder to choose CoffeeScript for a project when fewer people use it, and when there isn’t public support for the language and a community committed to supporting it as the JavaScript ecosystem evolves. Choosing CoffeeScript for a project can also be stymied if another essential piece of the project, especially its framework, is incompatible with CoffeeScript in some way.

Many people were drawn to CoffeeScript because it offered features that JavaScript once lacked: classes, destructuring, fat-arrow functions, etc. Once ES2015 arrived and JavaScript (mostly) caught up, those people abandoned CoffeeScript back for the JavaScript they were more familiar with. Those people aren’t coming back, nor should we pursue them. With ECMAScript proposals and development proceeding at a rapid pace, we stand no chance of out-innovating the JavaScript community in inventing new language features.

Many other people, however, came to CoffeeScript for the clean, readable syntax and the many ways that the language itself helps prevent bugs, such as significant whitespace and the existential operator. CoffeeScript still has these advantages over all versions of JavaScript, and will retain them so long as ECMAScript strives for backward compatibility. But for CoffeeScript to remain a viable choice for developers, it must keep pace with the JavaScript community. At the very least it must be compatible with most popular frameworks and build tools; ideally it will also be current with the latest approved standard. The mantra of CoffeeScript is that “It’s just JavaScript”—but right now, JavaScript is ES2015.

## Goals

**ES2015 features that modern frameworks require, like modules and classes, must be supported in CoffeeScript ASAP.** We can’t expect developers to continue using CoffeeScript if they must choose between CoffeeScript and whatever hot new framework they want to use for their project. Support for modules is [has been released in CoffeeScript 1.11](https://github.com/jashkenas/coffeescript/pull/4300) and support for classes [has been merged into the `2` branch](https://github.com/jashkenas/coffeescript/pull/4354).

**CoffeeScript should support other ES2015+ features on a case-by-case basis.** There is very little that ES2015 offers that CoffeeScript lacks; but whatever new features that make sense within the constraints of CoffeeScript’s design principles, and can be implemented in a reasonable way, should be supported. We don’t want developers to feel like choosing CoffeeScript means they’re giving up features they had in ES2015. Please refer to the [issues](https://github.com/coffeescript6/discuss/issues) of this repo for discussion around which ES2015+ features to add, and how they should be defined and implemented in CoffeeScript.

**CoffeeScript should output as much ES2015+ syntax as possible, *as ES2015+*.** With the advent of Babel, there’s no need for CoffeeScript to reinvent the wheel in finding ways to convert ES2015 features into ES5 code. CoffeeScript should simply output modern ES2015+ JavaScript, and let downstream tools convert and polyfill for compatibility. The advantage of this is that CoffeeScript will always remain modern—as more and more runtimes support more and more ES2015+ features natively, and Babel adjusts to let more native code through to the final output, nothing is required on CoffeeScript’s part to take advantage of the shifting landscape. Debugging will also be easier, for example if a CoffeeScript fat arrow shows up in DevTools as an ES2015 fat arrow. And the CoffeeScript codebase itself will be simpler; compiling `=>` to `=>`, for example, will require far less code than the constructs the compiler creates now. And of course, our mantra: “It’s just JavaScript.”

**While adding ES2015+ features, we should maintain as much backward compatibility as possible.** There’s a lot of code out there already written in CoffeeScript. We would do our community a disservice by introducing unnecessary breaking changes. Whatever one may think of the CoffeeScript syntax for existing features, that ship has sailed; there are millions of lines of code written in that syntax, and we owe it to our users to force as little refactoring as possible.

**CoffeeScript “is just JavaScript,” but it has a core tenet of its own: elegant, concise syntax.** Now that ECMAScript has more-or-less feature parity with CoffeeScript, the CoffeeScript language’s primary selling point is its clean, spare syntax that eschews unnecessary code whenever possible. As we add new features, whether based on ES2015+ or original, we must strive to maintain CoffeeScript’s simple elegance.

## The Plan

### CoffeeScript 1.x

New ES2015+ features that can be opt-in by using them and that don’t break backward compatibility, like modules, have been added to CoffeeScript in the current `master` branch and released. These features aren’t shimmed or polyfilled down to ES5; they are output as ES2015.

### [CoffeeScript 2](https://github.com/coffeescript6/discuss/projects/1)

New ES2015+ features that cannot be added without causing breaking changes, like classes, [are implemented on a `2` branch](https://github.com/coffeescript6/discuss/issues/36) for a future CoffeeScript 2.0.0 release. This new release will break backward compatibility, but as minimally as possible. Also in 2.0.0, we will modernize the output of as many features as possible and remove as many shims and polyfills as possible. CoffeeScript 2.0.0 will go through several rounds of alpha releases like 2.0.0-alpha1, 2.0.0-alpha2 etc. so that we can add features gradually and avoid committing to a final set of breaking changes before we’re ready. You can also read [draft documentation for CoffeeScript 2](https://rawgit.com/GeoffreyBooth/coffeescript/2-docs/docs/v2/index.html).

## Implemented Features

#### Modules: `import` and `export` [(#7)](https://github.com/coffeescript6/discuss/issues/7)

> CoffeeScript 1.x and 2

[This has been merged](https://github.com/jashkenas/coffeescript/pull/4300) and released as part of CoffeeScript 1.11.

#### Classes: Extend ES Classes, Idiomatic Methods [(#22)](https://github.com/coffeescript6/discuss/issues/22)

> CoffeeScript 2 only

[This has been merged](https://github.com/jashkenas/coffeescript/pull/4354) into the `2` branch.

#### Tagged template literals [(#28)](https://github.com/coffeescript6/discuss/issues/28)

> CoffeeScript 1.x and 2

[This has been merged](https://github.com/jashkenas/coffeescript/pull/4352) and released as part of CoffeeScript 1.12.

#### `async`/`await` [(#10)](https://github.com/coffeescript6/discuss/issues/10)

> CoffeeScript 2

[This has been merged](https://github.com/jashkenas/coffeescript/pull/3757) into the `2` branch.

#### Backticked blocks [(#42)](https://github.com/coffeescript6/discuss/issues/42)

> CoffeeScript 1.x and 2

[This has been merged](https://github.com/jashkenas/coffeescript/pull/4357) and released as part of CoffeeScript 1.12.

#### Template literals [(#41)](https://github.com/coffeescript6/discuss/issues/41)

> CoffeeScript 2 only

[This has been merged](https://github.com/jashkenas/coffeescript/pull/4365) into the `2` branch.

#### Fat arrows `=>` output as `=>` [(#8)](https://github.com/coffeescript6/discuss/issues/8)

> CoffeeScript 2 only

[This has been merged](https://github.com/jashkenas/coffeescript/pull/4311) into the `2` branch.

#### `for … of` [(#11)](https://github.com/coffeescript6/discuss/issues/11)

> CoffeeScript 1.x and 2

[This has been merged](https://github.com/jashkenas/coffeescript/pull/4306) and released as part of CoffeeScript 1.12.

## Features to Implement

#### Classes: Idiomatic `super` [(#22)](https://github.com/coffeescript6/discuss/issues/22)

> CoffeeScript 2 only

CoffeeScript’s `super` should always be compiled to ES2015’s `super`. This is in progress at [jashkenas/coffeescript #4424](https://github.com/jashkenas/coffeescript/pull/4424).

#### Classes: `static`, `get` and `set` keywords [(#17)](https://github.com/coffeescript6/discuss/issues/17)

> CoffeeScript 2 only

Classes should support getters and setters [(#17)](https://github.com/coffeescript6/discuss/issues/17) and the `static` keyword.

#### Destructuring: Idiomatic output [(#69)](https://github.com/coffeescript6/discuss/issues/69)

> CoffeeScript 2 only

CoffeeScript 1.x already supports destructuring; this task would be to change CoffeeScript’s output from ES3 plain variable assignment into ES2015 destructuring syntax.

## Not in Scope

These are other features that have been discussed, but the consensus at the moment is that no action should be taken to implement them:

#### Block assignment `let` and `const` assignment operators [(#31)](https://github.com/coffeescript6/discuss/issues/31) or [(#35)](https://github.com/coffeescript6/discuss/issues/35)

#### Inferred `let` assignment [(#1)](https://github.com/coffeescript6/discuss/issues/1)

#### Decorators [(#9)](https://github.com/coffeescript6/discuss/issues/9)

#### Type annotations [(#12)](https://github.com/coffeescript6/discuss/issues/12)

## Open Questions

The [Issues](https://github.com/coffeescript6/discuss/issues) for this repo covers the various ES2015+ features and discussions regarding how to implement them. If you don’t see your favorite ES2015+ feature there, or want to propose your own new feature for the language, please [open an issue](https://github.com/coffeescript6/discuss/issues/new). That’s also the place to discuss the specifics of how to move this project forward.

If you disagree with any part of this document, please [open a pull request](https://github.com/coffeescript6/discuss/pulls) with a suggested revision and we can discuss it.
