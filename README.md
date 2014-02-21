bundler_test
============

A really simple test repository for reproducing a Bundler bug

In this Gemfile, the 'activesupport' gem has two requirements.
These two requirements should be compatible.
Currently, the first requirement is being satisfied "greedily", resulting in a fake version conflict.

```
$ export DEBUG_RESOLVER=1
$ bundle
Updating git@github.com:magneland/bundler_test2.git
Fetching gem metadata from https://rubygems.org/..........
Fetching additional metadata from https://rubygems.org/..
Resolving dependencies...
...
==== Iterating ====

Activated:
  bundler_test2 (0.0.0)
  factory_girl (4.4.0)
Requirements:
  activesupport (>= 3.0.0) ruby
  activesupport (< 4.0, >= 2.3.5) ruby
Attempting:
  activesupport (>= 3.0.0) ruby
  Activating: activesupport (4.0.3)
    * factory_girl (>= 0)
    * activesupport (>= 3.0.0)
    Dependencies
    * i18n (>= 0.6.4, ~> 0.6)
    * multi_json (~> 1.3)
    * tzinfo (~> 0.3.37)
    * minitest (~> 4.2)
    * thread_safe (~> 0.1)
...
==== Iterating ====

Activated:
  bundler_test2 (0.0.0)
  factory_girl (4.4.0)
  activesupport (4.0.3)
Requirements:
  activesupport (< 4.0, >= 2.3.5) ruby
  tzinfo (~> 0.3.37) ruby
  thread_safe (~> 0.1) ruby
  i18n (>= 0.6.4, ~> 0.6) ruby
  minitest (~> 4.2) ruby
  multi_json (~> 1.3) ruby
Attempting:
  activesupport (< 4.0, >= 2.3.5) ruby
    * [FAIL] Already activated
      * bundler_test2 (>= 0)
    -> Jumping to: bundler_test2

Bundler could not find compatible versions for gem "activesupport":
  In Gemfile:
    bundler_test2 (>= 0) ruby depends on
      activesupport (< 4.0, >= 2.3.5) ruby

    factory_girl (>= 0) ruby depends on
      activesupport (4.0.3)
```
