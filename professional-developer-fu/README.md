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

```
"babel-cli"
"babel-preset-es2015"
```

Inside your project you will also have to add a ".bablerc" file.
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