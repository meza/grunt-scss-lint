# grunt-scss-lint
[![Build Status](https://travis-ci.org/ahmednuaman/grunt-scss-lint.png?branch=master)](https://travis-ci.org/ahmednuaman/grunt-scss-lint) [![Code Climate](https://codeclimate.com/github/ahmednuaman/grunt-scss-lint.png)](https://codeclimate.com/github/ahmednuaman/grunt-scss-lint) [![NPM version](https://badge.fury.io/js/grunt-scss-lint.png)](http://badge.fury.io/js/grunt-scss-lint)

> Lint your `.scss` files

## Getting Started
This plugin requires Grunt `>= 0.4.0` and [scss-lint](https://github.com/causes/scss-lint) `>= 0.18.0`.

If you haven't used [Grunt](http://gruntjs.com/) before, be sure to check out the [Getting Started](http://gruntjs.com/getting-started) guide, as it explains how to create a [Gruntfile](http://gruntjs.com/sample-gruntfile) as well as install and use Grunt plugins. Once you're familiar with that process, you may install this plugin with this command:

```shell
npm install grunt-scss-lint --save-dev
```

Once the plugin has been installed, it may be enabled inside your Gruntfile with this line of JavaScript:

```js
grunt.loadNpmTasks('grunt-scss-lint');
```

## Scss-lint task
_Run this task with the `grunt scsslint` command._

[scss-lint](https://github.com/causes/scss-lint) is a Ruby gem written by [The Causes Engineering Team](https://github.com/causes), this plugin is simply a grunt wrapper for the gem.

This task requires you to have [Ruby](http://www.ruby-lang.org/en/downloads/), and [scss-lint](https://github.com/causes/scss-lint#installation) installed. If you're on OS X or Linux you probably already have Ruby installed; test with `ruby -v` in your terminal. When you've confirmed you have Ruby installed, run `gem update --system && gem install scss-lint` to install the `scss-lint` gem.

### Options

#### bundleExec

- Type: `Boolean`
- Default: `false`

You can choose to have your gems installed via [bundler](http://bundler.io) and if so, set this option to `true` to use the local gems.

#### colorizeOutput

- Type: `Boolean`
- Default: `true`

Get some nice looking output.

For colors to work on Windows, you first need to install 2 extra gems. This is because  of [Rainbow](https://github.com/sickill/rainbow#windows-support), a dependency of [scss-lint](https://github.com/causes/scss-lint).

    gem install windows-pr win32console

#### compact

- Type: `Boolean`
- Default: `false`

Group related linted files for more easier error review. XML output will still be default from scss-lint.

#### ~~config~~

You can't control the config location of scss-lint anymore.
Use `scss-lint`'s [default config file](https://github.com/causes/scss-lint/blob/master/config/default.yml)
as ```.scss-lint.yml```

#### reporterOutput

- Type: `String`
- Default: `null`

The jUnit XML file to save the output to. If you don't want this then set the option as `null`.

### Usage Examples

#### Example config

```javascript
grunt.initConfig({
  scsslint: {
    allFiles: [
      'test/fixtures/*.scss',
    ],
    options: {
      bundleExec: true,
      reporterOutput: 'scss-lint-report.xml',
      colorizeOutput: true
    },
  }
});

grunt.loadNpmTasks('grunt-scss-lint');

grunt.registerTask('default', ['scsslint']);
```

### Exit error codes
If you're having problems with the task exiting with an error code, then have a look here: [https://github.com/causes/scss-lint/blob/master/lib/scss_lint/cli.rb](https://github.com/causes/scss-lint/blob/master/lib/scss_lint/cli.rb)
