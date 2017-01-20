# ESNext Features to Support in CoffeeScript

Per the [README](./README.md), we have two main goals for the future of CoffeeScript: adding support for important ES2015+ (ESNext) features that CoffeeScript currently lacks, and changing CoffeeScript’s output to be ESNext code. See also the [project board for CoffeeScript 2.0.0](https://github.com/coffeescript6/discuss/projects/1).

Features are ordered by priority, which is determined (subjectively) by how important each feature is to the CoffeeScript community. The most important criterion is whether the lack of specific feature affects CoffeeScript’s viability for a potential project: if a developer must choose between CoffeeScript and a particular library or framework, whatever missing feature is causing that choice to need to be made is a top priority for us to fix. This list is based on the [issues](https://github.com/coffeescript6/discuss/issues) for this repo and the discussion in [#8](https://github.com/coffeescript6/discuss/issues/8).

## Top Priority

These features affect interopability and should take priority over all other features. These should be implemented ASAP in the current compiler, in addition to any new compiler that gets created later.

### ~~Modules: `import` and `export` [(#7)](https://github.com/coffeescript6/discuss/issues/7)~~

> CoffeeScript 1.x and 2

[This has been merged](https://github.com/jashkenas/coffeescript/pull/4300) and released as part of CoffeeScript 1.11.

### ~~Classes: Extend ES Classes, Idiomatic Methods [(#22)](https://github.com/coffeescript6/discuss/issues/22)~~

> CoffeeScript 2 only

[This has been merged](https://github.com/jashkenas/coffeescript/pull/4354) into the `2` branch.

### ~~Tagged template literals [(#28)](https://github.com/coffeescript6/discuss/issues/28)~~

> CoffeeScript 1.x and 2

[This has been merged](https://github.com/jashkenas/coffeescript/pull/4352) and released as part of CoffeeScript 1.12.

## Medium Priority

These features aren’t required for CoffeeScript to be used in any project, but there’s great desire in the community for these to be added.

### Classes: Idiomatic `super` [(#22)](https://github.com/coffeescript6/discuss/issues/22)

> CoffeeScript 2 only

CoffeeScript’s `super` should always be compiled to ES2015’s `super`. This is in progress at [jashkenas/coffeescript #4424](https://github.com/jashkenas/coffeescript/pull/4424).

### Classes: `static`, `get` and `set` keywords [(#17)](https://github.com/coffeescript6/discuss/issues/17)

> CoffeeScript 2 only

Classes should support getters and setters [(#17)](https://github.com/coffeescript6/discuss/issues/17) and the `static` keyword.

### ~~`async`/`await` [(#10)](https://github.com/coffeescript6/discuss/issues/10)~~

> CoffeeScript 2

[This has been merged](https://github.com/jashkenas/coffeescript/pull/3757) into the `2` branch.

### ~~Backticked blocks [(#42)](https://github.com/coffeescript6/discuss/issues/42)~~

> CoffeeScript 1.x and 2

[This has been merged](https://github.com/jashkenas/coffeescript/pull/4357) and released as part of CoffeeScript 1.12.

## Low Priority

These are nice-to-have features that should be implemented as time permits, probably only in the “new” compiler if one gets created. Any change that causes ES2015 output and isn’t opt-in needs to either be enabled by a flag or only in the new, ESNext-outputting compiler.

### Destructuring assignment [(#18)](https://github.com/coffeescript6/discuss/issues/18)

> CoffeeScript 2 only

### ~~Template literals [(#41)](https://github.com/coffeescript6/discuss/issues/41)~~

> CoffeeScript 2 only

[This has been merged](https://github.com/jashkenas/coffeescript/pull/4365) into the `2` branch.

### ~~Fat arrows `=>` output as `=>` [(#8)](https://github.com/coffeescript6/discuss/issues/8)~~

> CoffeeScript 2 only

[This has been merged](https://github.com/jashkenas/coffeescript/pull/4311) into the `2` branch.

### ~~`for … of` [(#11)](https://github.com/coffeescript6/discuss/issues/11)~~

> CoffeeScript 1.x and 2

[This is has been merged](https://github.com/jashkenas/coffeescript/pull/4306) and released as part of CoffeeScript 1.12.

## No Action

These are other features that have been discussed, but the consensus at the moment is that no action should be taken to implement them.

### Block assignment `let` and `const` assignment operators [(#31)](https://github.com/coffeescript6/discuss/issues/31) or [(#35)](https://github.com/coffeescript6/discuss/issues/35)

### Inferred `let` assignment [(#1)](https://github.com/coffeescript6/discuss/issues/1)

### Decorators [(#9)](https://github.com/coffeescript6/discuss/issues/9)

### Type annotations [(#12)](https://github.com/coffeescript6/discuss/issues/12)
