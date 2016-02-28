<p align="center">
  <a href="http://gulpjs.com">
    <img height="257" width="114" src="https://raw.githubusercontent.com/gulpjs/artwork/master/gulp-2x.png">
  </a>
</p>
# gulp.js starter for single page apps
A clean and simple starter ES6 boilerplate for single page applications using gulp.js.

[![License](https://img.shields.io/github/license/mashape/apistatus.svg)](https://github.com/antonsamper/gulp-boilerplate/blob/master/LICENSE)
[![Travis](https://img.shields.io/travis/rust-lang/rust/master.svg)](https://travis-ci.org/antonsamper/gulp-boilerplate)
[![devDependency Status](https://david-dm.org/antonsamper/gulp-boilerplate/dev-status.svg)](https://david-dm.org/antonsamper/gulp-boilerplate#info=devDependencies)

###### Boilerplate variations
- [Boilerplate with AngularJS](https://github.com/antonsamper/gulp-boilerplate-with-angular)


## Boilerplate used by
<p>
  <a href="http://signagerocket.com/">
    <img height="100" width="100" src="https://raw.githubusercontent.com/antonsamper/gulp-boilerplate/master/src/images/logo-signagerocket.png">
  </a>
  <a href="http://www.nowtv.com/">
    <img height="100" width="100" src="https://raw.githubusercontent.com/antonsamper/gulp-boilerplate/master/src/images/logo-nowtv.png">
  </a>
</p>

## Installation and Usage
To start using the boilerplate, first install all the dependencies and then run one of the gulp tasks, for example:

 ```
 $ npm i (bower components installed automatically)
 $ npm start
 ```

## Npm Tasks

###### Bundle Tasks

Task Name         | Description
----------------- | ---------------------------------------------------------------------
`npm start`       | Generate a development environment with watch and browsersync
`npm run dev`     | Same as `npm start`
`npm run prod`    | Outputs minified production code, asset revisions and run unit tests
`npm test`        | Run unit tests

## Gulp Tasks

###### Bundle Tasks

Task Name         | Description
----------------- | ---------------------------------------------------------------------
`gulp`            | Generate a development environment with watch and browsersync
`gulp prod`       | Outputs minified production code, asset revisions and run unit tests

###### Individual Tasks

Task Name         | Description
----------------- | ----------------------------------------------------
`gulp clean`      | Delete the output directory
`gulp eslint`     | Detect js syntax and style errors
`gulp iconfont`   | Compile icon font and the corresponding Sass
`gulp imagemin`   | Minify images and svg files
`gulp karma`      | Run unit tests
`gulp minifyHtml` | Inject assets into and compress the main index.html
`gulp move`       | Move source files to output directory
`gulp revReplace` | Rewrite occurrences of file names changed by gulp-rev
`gulp scripts`    | Concatenate and compress js files
`gulp server`     | Initialise a local server
`gulp styles`     | Compile Sass to CSS


## File Structure
The default working directory for development is `src/`. This directory contains all the styles, scripts, fonts and images used to create the front-end of the website.

```
bower_components/
dist/
src/
|- fonts/
	|- examplefont.eot
	|- examplefont.svg
	|- examplefont.ttf
	|- examplefont.woff
	|- iconfont/
		|- iconfont01.svg
		|- iconfont02.svg
		|- iconfont03.svg
|- images/ 
|- js/
	|- components/
		|- helloWorld/
			|- helloWorld.js
			|- helloWorld.spec.js
	|- app.js
|- sass/
	|- components/
	|- _variables.scss
	|- main.scss
|- index.html 
```

### Fonts
The `src/fonts/` folder should contain the self hosted fonts for the site. All the fonts directly inside this folder will be copied to the `dist/fonts/` folder automatically.

In order to generate a custom icon font, place your svg files inside the `src/fonts/iconfont/` folder and when the `iconfont` task runs, all the svgs inside this folder will be combined to create a custom icon font. Running this task will also generate a sass template file exported to `src/sass/components/_iconfont.scss` with the `@font-face` declaration and the font classes, for example:

```
&--iconfont01:before { content: '\e001'; }
&--iconfont02:before { content: '\e002'; }
&--iconfont03:before { content: '\e003'; }
```
This auto generated file is explicitly included in the Sass manifest.

### Images
All images should be placed inside the `src/images/` folder. This is for consistency as opposed to a limitation enforced by the `imagemin` task as this task will look for and minify all images inside the `src/` folder that have any of the following extensions: `.jpg` `.png` `.gif` `.svg`

### JS
All the scripts should be placed inside the `src/js/` folder. These files will all be linted and then injected into `index.html`. The current setup assumes a modular approach when adding new features so that everything that is require for a module is inside of its own folder - this can include tests, templates and specific styles if needed. For example:

```
|- js/
	|- components/
		|- helloWorld/
			|- helloWorld.js
			|- helloWorld.spec.js
			|- helloWorld.e2e.js
			|- helloWorld.html
			|- helloWorld.css
```

### Bower
The boilerplate supports bower components. The components are installed in the `bower_components/` folder and are automatically injected into `index.html` either at the top if it's a CSS component or at the bottom if it's JS. The gulp task used to make this work assumes that the Bower component contains the `main` property inside of `bower.json` that points the final asset. For example: `"main": "jquery.js",`

### SASS
This workflow uses the `scss` format for Sass. All `scss` files should be placed in the `src/sass/` folder. The styles manifest is `main.scss`.

### Releases
The three main functions of `release-it` have been mapped as custom npm scripts. When creating a release all you have to do is run any of the following:
 *  `npm run release-patch`
 *  `npm run release-minor`
 *  `npm run release-major`
