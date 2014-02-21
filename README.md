bundler_test
============

A really simple test repository for reproducing a Bundler bug

```
$ bundle
Updating git@github.com:magneland/bundler_test2.git
Fetching gem metadata from https://rubygems.org/..........
Fetching additional metadata from https://rubygems.org/..
Resolving dependencies...
Bundler could not find compatible versions for gem "activesupport":
  In Gemfile:
    bundler_test2 (>= 0) ruby depends on
      activesupport (< 4.0, >= 2.3.5) ruby

    factory_girl (>= 0) ruby depends on
      activesupport (4.0.3)
```
