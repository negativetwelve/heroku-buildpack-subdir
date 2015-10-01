# Heroku Buildpack Subdir

Allows you to compose multiple buildpacks with apps in multiple directories. For information regarding adding multiple buildpacks, check out the official docs [here](https://devcenter.heroku.com/articles/using-multiple-buildpacks-for-an-app#adding-a-buildpack).

This buildpack must be at index 1 and all buildpacks following should be at index 2 through N.

## Usage

    $ heroku buildpacks:set https://github.com/negativetwelve/heroku-buildpack-subdir

Example `.buildpacks` file:

    $ cat .buildpacks
    api=https://github.com/heroku/heroku-buildpack-ruby.git
    web=https://github.com/heroku/heroku-buildpack-nodejs.git
    https://github.com/emk/heroku-buildpack-go

This would run:

* The first buildpack would `cd` into an `api` directory and use a `ruby` buildpack.
* The second would `cd` into a `web` directory and use a `node.js` buildpack.
* The third would be in the root directory and use a `go` buildpack.
