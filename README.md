# grunt-backstop

> BackstopJs Shim for Grunt

## Getting Started
This plugin requires Grunt `~0.4.5`

If you haven't used [Grunt](http://gruntjs.com/) before, be sure to check out the [Getting Started](http://gruntjs.com/getting-started) guide, as it explains how to create a [Gruntfile](http://gruntjs.com/sample-gruntfile) as well as install and use Grunt plugins. Once you're familiar with that process, you may install this plugin with this command:

```shell
npm install grunt-backstop --save-dev
```

Once the plugin has been installed, it may be enabled inside your Gruntfile with this line of JavaScript:

```js
grunt.loadNpmTasks('grunt-backstop');
```

## Overview

* Provides a way to setup [BackstopJS](https://github.com/garris/BackstopJS) off of an initial npm or bower install without needing to access `node_modules` or `bower_components`

* Mirrors tests and reference files to a separate, user defined `tests` folder, which can easily be check into the repository.

* Run backstop commands from the project root using grunt

* Allows you to easily integrate BackstopJS tests into build or CI workflows.


## Setup

In your project's Gruntfile, add a section named `backstop` to the data object passed into `grunt.initConfig()`.

```js
grunt.initConfig({
  backstop: {
    your_target: {
      backstop_path: './bower_components/backstopjs',
      test_path: './tests',
      setup: true,
      configure: true,
      create_references: true,
      run_tests: true
    },
  },
});
```


#### target.backstop_path
Type: `String`

Identifies the location of the BackstopJs module (usually `bower_components` or `node_modules`)

#### target.test_path
Type: `String`  

Identifies the location of the directory that will contain your tests

#### target.configure
Type: `Boolean`

When true, the target will trigger an npm install inside of the `backstop_path`.


#### target.setup
Type: `Boolean`

When true, the target will copy the checked in reference files in your `test_path` into the `backstop_path`

#### target.create_references
Type: `Boolean`

When true, the target will create new backstopJS references and mirror them to the `test_path`

#### target.run_tests
Type: `Boolean`

When true, the target will run the css regression tests


## Usage Notes

You may configure your targets to run as many of the available options, and in any combination you like. However, they are setup to be run in a series as such:

  1. `setup`
  2. `configure`
  3. `create references`
  4. `test`

## TODO

* Fix the options. I don't think that I setup the options right. It looks like there is a dedicated options property on the target that would be a more apporpriate place to put the options, and then also provides a good mechanism to provide defaults.

* Create a stop command (The server has a 15 minute time out when you run the tests)

* Add tests
