# Heroku Buildpack Subdir

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)


Allows you to compose multiple buildpacks with apps in multiple directories. For information regarding adding multiple buildpacks, check out the official docs [here](https://devcenter.heroku.com/articles/using-multiple-buildpacks-for-an-app#adding-a-buildpack).

This buildpack must be at index 1 and all buildpacks following should be at index 2 through N.

## Usage

    $ heroku buildpacks:set https://github.com/negativetwelve/heroku-buildpack-subdir

Example `.buildpacks` file:

    $ cat .buildpacks
    https://github.com/heroku/heroku-buildpack-nginx
    api=https://github.com/heroku/heroku-buildpack-ruby
    web=https://github.com/heroku/heroku-buildpack-nodejs
    web=https://github.com/heroku/heroku-buildpack-pgbouncer
    https://github.com/heroku/heroku-buildpack-go

This would run:

* The first buildpack would be in the root directory use use the `ngin` buildpack.
* The second buildpack would `cd` into an `api` directory and use a `ruby` buildpack.
* The third would `cd` into a `web` directory and use a `nodejs` buildpack.
* The fourth would `cd` into a `web` directory and use a `pgbouncer` buildpack.
* The firth would be in the root directory and use a `go` buildpack.

Buildpacks are executed in the order they are declared.
