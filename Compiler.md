# A New CoffeeScript Compiler

The current CoffeeScript 1.x compiler is extremely well commented, but it really needs those comments. An entire project, [CoffeeScript Redux](https://github.com/michaelficarra/CoffeeScriptRedux), was created just to rewrite CoffeeScript’s codebase, not to add new features.

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