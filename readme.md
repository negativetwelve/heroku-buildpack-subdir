# Heroku Buildpack Subdir

Allows you to compose multiple buildpacks with apps in multiple directories. For information regarding adding multiple buildpacks, check out the official docs [here](https://devcenter.heroku.com/articles/using-multiple-buildpacks-for-an-app#adding-a-buildpack).

This buildpack must be at index 1 and all buildpacks following should be at index 2 through N.
