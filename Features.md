# ESNext Features to Support in CoffeeScript

Per the [README](./README.md), we have two main goals for the future of CoffeeScript: adding support for important ES2015+ (ESNext) features that CoffeeScript currently lacks, and changing CoffeeScript’s output to be ESNext code. This document covers the former; see [Compiler.md](./Compiler.md) for the latter.

Features are ordered by priority, which is determined (subjectively) by how important each feature is to the CoffeeScript community. The most important criterion is whether the lack of specific feature affects CoffeeScript’s viability for a potential project: if a developer must choose between CoffeeScript and a particular library or framework, whatever missing feature is causing that choice to need to be made is a top priority for us to fix. This list is based on the [issues](https://github.com/coffeescript6/discuss/issues) for this repo and the discussion in [#8](https://github.com/coffeescript6/discuss/issues/8).

## Top Priority

These features affect interopability and should take priority over all other features. These should be implemented ASAP in the current compiler, in addition to any new compiler that gets created later.

### Modules: `import` and `export` [(#7)](https://github.com/coffeescript6/discuss/issues/7)

This is in progress [here](https://github.com/jashkenas/coffeescript/pull/4300) as a pull request to the original CoffeeScript compiler.

### Classes [(#22)](https://github.com/coffeescript6/discuss/issues/22)

We have consensus that there needs to be some way for CoffeeScript to output ESNext native `class foo extends bar` syntax, in order to interoperate with libraries that use ECMAScript classes. Waiting on a consensus for the approach and syntax in [#22](https://github.com/coffeescript6/discuss/issues/22).

> **This is a breaking change for the current compiler.** Either the `class` keyword gets redefined, or we’re adding a new keyword to implement the new behavior (and old code that might have used that now-reserved keyword could break). We would need to choose whether the breaking change would be opt-in (the current behavior unless a flag was set) or opt-out (the new behavior unless a flag was set). If we go with the “new `esclass` keyword” proposal, the breaking change would likely be opt-*out*.

### Template literals [(#28)](https://github.com/coffeescript6/discuss/issues/28)

Some new libraries require support for ECMAScript template literals, which are incompatible with CoffeeScript’s backticks. Waiting on consensus for the approach and syntax in [#28](https://github.com/coffeescript6/discuss/issues/28).

## Medium Priority

These features aren’t required for CoffeeScript to be used in any project, but there’s great desire in the community for these to be added.

### `const` assignment operator [(#1)](https://github.com/coffeescript6/discuss/issues/1)

For whatever reason, `let` and `const` are among the most popular features introduced by ES2015. Per [#1](https://github.com/coffeescript6/discuss/issues/1), we have consensus that there should be some way to force variable assignment to use `const` instead of `var`. The syntax for such a “`const` assignment” shall be:

```coffee
foo := 42
```
which becomes:

```js
const foo = 42;
```

This has the advantage that it’s not a breaking change; currently `:=` fails to compile. `const` variables must be assigned and declared in the same operation, so such declarations would happen in JavaScript at the same place in your code (unlike `var` declarations which happen at the top of the scope). There is no need to support `?:=`, since by definition constants can’t be reassigned.

Nothing else would be changed by adding this new operator. Normal assignment is handled as it is today, with `var`. Even though using `:=` would cause `const` to be in the generated output, this feature is “opt in” like modules and the same warning would apply about transpiling CoffeeScript’s output.

### `async`/`await` [(#10)](https://github.com/coffeescript6/discuss/issues/10)

This isn’t even standardized yet; it’s not part of ES2015 or ES2016, though support has started appearing in browsers.

CoffeeScript’s version would add only the `await` keyword, which would automatically cause CoffeeScript to output an `async` keyword where needed. This behavior is similar to how generators are handled, where the presence of a `yield` keyword causes CoffeeScript to declare the function as `function*`: the presence of `await` would cause CoffeeScript to declare its associated function with `async`.

So to take the example from http://stackabuse.com/node-js-async-await-in-es7/, this JavaScript:

```js
var request = require('request-promise');

async function main() {  
  var body = await request.get('https://api.github.com/repos/scottwrobinson/camo');
  console.log('Body:', body);
}
main();
```

could be written in CoffeeScript as:

```coffee
request = require 'request-promise'

main = ->
  body = await request.get 'https://api.github.com/repos/scottwrobinson/camo'
  console.log 'Body:', body

main()
```

> **This is a breaking change for the current compiler.** The `await` keyword is not currently reserved, so adding it as a reserved word would break any code that currently uses `await` as a variable or function name. We would need to choose whether the breaking change would be opt-in (no `await` unless a flag is set) or opt-out (`await` is a reserved word unless a flag is set). This breaking change would likely be opt-*out*.

## Low Priority

These are nice-to-have features that should be implemented as time permits, probably only in the “new” compiler if one gets created. Any change that causes ES2015 output and isn’t opt-in needs to either be enabled by a flag or only in the new, ESNext-outputting compiler.

### Fat arrows `=>` output as `=>` [(#8)](https://github.com/coffeescript6/discuss/issues/8)

**Only for the new ESNext-outputting compiler, or the original compiler behind a flag.**

Fat arrows should be transpiled into ES2015 `=>`. They took our good idea, let’s celebrate by using it.

### Inferred `let` assignment [(#1)](https://github.com/coffeescript6/discuss/issues/1)

**Only for the new ESNext-outputting compiler, or the original compiler behind a flag.**

When a variable isn’t declared using the new `:=` operator that produces `const` (see above), CoffeeScript should automatically declare it with `let` whenever possible.

### `for … of` [(#11)](https://github.com/coffeescript6/discuss/issues/11)

**Only for the new ESNext-outputting compiler, or the original compiler behind a flag.**

There should be some way to output ESNext `for … of`, perhaps via a new `for` syntax. Awaiting consensus.

## TODO

These are ESNext features where a consensus has yet to be reached on whether CoffeeScript should support them.

### Getters and setters [(#17)](https://github.com/coffeescript6/discuss/issues/17)

## No Action

These are other features that have been discussed, but the consensus at the moment is that no action should be taken to implement them.

### Decorators [(#9)](https://github.com/coffeescript6/discuss/issues/9)

### Type annotations [(#12)](https://github.com/coffeescript6/discuss/issues/12)

### Destructuring assignment [(#18)](https://github.com/coffeescript6/discuss/issues/18)