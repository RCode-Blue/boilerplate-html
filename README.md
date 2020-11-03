# HTML from Scratch

## Contents

<br/><br/><br/>

# Part 1: Setup Node

### 1. Initialise NPM

<br/>

```bash
npm init
```

Answer all questions, or use `npm init --y` to take all defaults

It has config files for Editor Config, ESLint and Prettier
<br/><br/>


### 2. Install NPM dependencies

```bash
npm install --save-dev npm-run-all copyfiles
```
where:

| Library              | Description / Link                      |
| -------------------- | --------------------------------------- |
| npm-run-all:         | A CLI tool to run multiple npm-scripts in parallel or sequential. |
|                      | _[node](https://www.npmjs.com/package/npm-run-all)_ \|  _[github](https://github.com/mysticatea/npm-run-all)_ \| _[usage](https://github.com/mysticatea/npm-run-all/blob/HEAD/docs/npm-run-all.md)_        |
| copyfiles: | For copying files |
|  | _[node](https://www.npmjs.com/package/copyfiles)_ \| _[github](https://github.com/calvinmetcalf/copyfiles)_ |


### 3. Install CSS Dependencies

```bash
npm install --save-dev postcss-cli autoprefixer concat node-sass
```
where:

| Library              | Description / Link                      |
| -------------------- | --------------------------------------- |
| sass:                | SASS implementation for npm             |
|                      | _[node](https://www.npmjs.com/package/sass)_ \| _[github](https://github.com/sass/dart-sass)_ 
| postcss-cli:         | Tool for creating CSS pre-processors or post-processors  |
|                      | _[node](https://www.npmjs.com/package/postcss-cli)_ \| _[github](https://github.com/postcss/postcss-cli)_       |
| autoprefixer:        | PostCSS plugin to parse CSS and add vendor prefixes to CSS rules using values from [Can I Use](https://caniuse.com/). |                    |
|                      | _[node](https://www.npmjs.com/package/autoprefixer)_ \| _[github](https://github.com/postcss/autoprefixer#readme)_       |
| concat:              | Tool for concatenating multiple files |                             |
|                      | _[node](https://www.npmjs.com/package/concat)_ \| _[github](https://github.com/gko/concat)_       |
  
<br/><br/><br/>

# Part 2: Configure Node

```json
"scripts": {
  "watch:sass": "sass src/CSS/styles.scss src/CSS/styles.css — watch",
  "serve:dev": "npm-run-all --parallal live-server watch:sass",

  "compile:sass": "sass sass/main.scss css/style.comp.css",
  "concat:css": "concat -o css/style.concat.css css/icon-font.css css/style.comp.css",
  "prefix:css": "postcss --use autoprefixer -b 'last 5 versions' css/style.concat.css -o css/style.prefix.css",
  "compress:css": "node-sass css/style.prefix.css css/style.css --output-style compressed",
  
  "build": "npm-run-all compile:sass concat:css prefix:css compress:css"
}
```
