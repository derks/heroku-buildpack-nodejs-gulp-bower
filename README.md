Heroku Buildpack for node/bower/gulp
====================================

IMPORTANT: This is a fork of https://github.com/krry/heroku-buildpack-nodejs-gulp-bower.git. Heroku's s3pository was deprecated and no longers exists... and this fork was a bandaid to get things fixed quickly.

DO NOT USE THIS BUILDPACK.... it will not be maintained. 


Setup
-----
1. Install the [Heroku Toolbelt](https://toolbelt.heroku.com/).
2. On the command line, set your app's buildpack URL to target this repository:

  ```
  heroku config:set BUILDPACK_URL=https://github.com/krry/heroku-buildpack-nodejs-gulp-bower.git
  ```
3. Set the `NODE_ENV` to an environment name of your choice:

  ```
  heroku config:set NODE_ENV={{env}} // I like to keep my `env` names short, e.g., "prod", "stage", "test", "int", "dev"
  ```
4. Allow the Heroku instance to install `devDependencies` stored in your `package.json` [as heroku recommends](https://devcenter.heroku.com/articles/nodejs-support#customizing-the-build-process).

  ```
  heroku config:set NPM_CONFIG_PRODUCTION=false
  ```
5. For each environment name, add a Gulp task named `heroku:{{env}}` that builds the app for that environment.

  ```
  var gulp = require('gulp');

  gulp.tasks('heroku:prod', [default]);
  ```


Credits
-------
* Thanks to [artmees](https://github.com/artmees) for getting things environment-sensitive.
* Forked from [heroku-buildpack-nodejs](https://github.com/heroku/heroku-buildpack-nodejs).
* Incorporated bower check and install from [heroku-buildpack-nodejs-gulp-bower](https://github.com/davidmfoley/heroku-buildpack-nodejs-gulp-bower)
* Heavily based on [heroku-buildpack-nodejs-grunt](https://github.com/mbuchetics/heroku-buildpack-nodejs-grunt).
