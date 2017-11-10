# lesson 8: professional developer-fu

If some of the professional developer-fu in lesson 8 was new to you, we hope the resource links here will help you:

[<= GO BACK ](../README.md)

## Resource Links

* [What is ECMA International ?](https://en.wikipedia.org/wiki/Ecma_International)
* [ECMA6 or ES6 Specs](http://www.ecma-international.org/ecma-262/6.0/index.html)
* [What is polyfill](https://remysharp.com/2010/10/08/what-is-a-polyfill)
* [List of polyfills](https://github.com/Modernizr/Modernizr/wiki/HTML5-Cross-Browser-Polyfills)
* [Wikipedia: Polyfill](https://en.wikipedia.org/wiki/Polyfill)
* [Transpiler vs Compiler](https://stackoverflow.com/questions/40605642/what-is-the-main-difference-between-compiler-and-transpiler)

* [Babel: Transpiler](https://babeljs.io/)
* [Babel: Try live transpiler](http://babeljs.io/repl/#?babili=false&evaluate=true&lineWrap=false&presets=es2015)
* [Babel: Plugin list](http://babeljs.io/docs/plugins/)
* [Babel: Preset (a group of plugins to convert ES6 to ES5)](http://babeljs.io/docs/plugins/preset-es2015/)

In order to transpile ES6 syntax to ES5 using Babel you will need Node and NPM.
Once you have both you will have to add these 2 packages to your project "package.json" file:

``
npm install babel-cli @babel/preset-env  --save-dev
``

Inside your project you will also have to add a ".bablerc" file.

```json
{
  "presets": ["@babel/env"]
}
```

The ``babel-preset-es20XX (15, 16, 17)`` presets include transforms needed to convert features added in that specific year to code that is compatible with the previous version.

The ``babel-preset-env`` includes transforms for all features that have landed in the spec, but only enables the ones needed to make the features work based on the set of environments you've provided to it.

If you pass no options to env it essentially works like es2015, es2016, es2017 all together.

You can also configure it to support specific browser version.

```json
{
  "presets": [
    ["@babel/env", {
      "targets": {
        "browsers": ["last 2 versions", "safari >= 7"]
      }
    }]
  ]
}
```

Finally to do the actual transpaling you have to add a build script in your "package.json" file:

```
"scripts": {
	"build": "babel ES6_Directory_Name -d ES5_Output_Directory"
},
```


## Browser feature support links:

* [Google Chrome](https://www.chromestatus.com/features#ES6)
* [Microsoft Edge](https://developer.microsoft.com/en-us/microsoft-edge/platform/status/?q=ES6)
* [Mozilla Firefox](https://platform-status.mozilla.org/)
* [ECMAScript Compatibility Table](https://kangax.github.io/compat-table/es6/)
* [Can I Use](https://caniuse.com/)