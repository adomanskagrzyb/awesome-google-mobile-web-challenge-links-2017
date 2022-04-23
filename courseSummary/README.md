# Course cheat sheet / Summary

**Written down by**: [José Carlos Camposano](http://josecamposano.com/)

Hi everyone!

Since it was quite difficult to go through the various forum posts and communication channels, I have tried to summarize in a single post all my learning and experiences with the course. The information contained in here is related to both contents and practical matters. I hope this post gives a quick help to those who are still aiming to finish the course and becomes an interesting discussion point to those who already completed it. Any contributions to the sections below are greatly welcome!

## Course structure

The course is divided into two parts: The first one teaches you how to add offline-first “app-looking” features into a social network web site, mainly by combining the use of ServiceWorker, Cache API and Indexed DB. The second half of the course teaches you about the JavaScript syntax updates in ES6 and how to take advantage of them even in older web browsers that lack the support. (Personally I think part 2 of the course should be taken before part 1).

## Practical advice for the first part of the course:

* Setup your dev environment by installing Node.js, nvm, git
* Choose your favorite IDE with JavaScript support and auto-completion
* Have some understanding about HTTP requests, responses and promises in JavaScript
* If you have problems to install and run the Wittr app code, double-check which version of Node.js are you using. Newer versions may not be fully supported and downgrade may be required (In my case v4.2 worked)
* Watch out the compatibility requirements of Chrome Canary and the updated interface of the dev tools in newer versions, which differs from the one shown in the videos (alternatively you can use the latest stable version of Chrome which already includes the necessary dev tools - or any browser you prefer altogether, minding that it will not match the course videos)
* Chrome Canary is not available for Linux
* When you reset or check-out another git branch, it may be necessary to stop and execute again the test server launch script by using in the terminal `npm run serve`

## Course contents - In a nutshell

#### Lesson 2

* Connectivity issues that can be solved with an offline-first approach

#### Lesson 3

* ServiceWorker: Purpose, scoping and lifecycle
* Chrome Canary dev tools
* Registering ServiceWorker: `navigator.serviceWorker.register(…)`
* Difference between fetch and XMLHttpRequest
* Intercepting requests through the fetch event: `self.addEventListener('fetch', function(event) { event.respondWith(...); });`
* Responding with custom response object `new Response(...)` or fetching from the network `fetch(...)`
* Cache API: `caches.open()`, `caches.put()`, `caches.addAll()`, `caches.delete()`, `caches.keys()`
* Version handling of static files in cache
* Update notifications:
  1. ServiceWorker registration object: `reg.unregister()`, `reg.update()`, `reg.waiting` (update waiting), `reg.installing` (update in progress), `reg.active`, `reg.installing.state` ("installed", "activating", "activated", "redundant"), reg.installing "statechange" event, reg "updatefound" event
  2. Observing the ServiceWorker controlling the page: navigator.serviceWorker.controller
* Update workflow:
  1. Sending messages to ServiceWorker `reg.installing.postMessage(...)` and listening to them within the ServiceWorker `self.addEventListener('message', function(event) { ... });`
  2. Forcing ServiceWorker to take control and skip its normal lifecycle `self.skipWaiting()`
  3. Detecting when a new ServiceWorker has taken over the page `navigator.serviceWorker.addEventListener('controllerchange', function() { ... });` to signal that the page should be reloaded

#### Lesson 4

* IndexedDB Promised: Opening database `idb.open(...)` and reading from it `db.transaction(...).objectStore(...).get(...)`
* Creating indices during version upgrades `upgradeDb.transaction.objectStore(...).createIndex(..., ...)`
* Storing and preloading contents from IndexedDB
* Using cursors to iterate through IndexedDB entries
* Continuously update and delete old cached entries from IndexedDB
* Use the cache API for images (by cloning the response and sending it to a separate image cache)
* Combine IndexedDB and Cache API to clean old entries in the image cache

END OF PART 1

#### Lesson 6

* Declaring variables with `let` (can be reassgined but not redeclared in same scope) and `const` (must have initial value and cannot be reassigned or redeclared in same scope) instead of `var`
* Template literals `` `${expression}` ``
* Destructuring arrays and objects
* Object literal shorthand (initialize object properties with the same name as the variables used to assign their initial values, function keyword is not required in object method definition)
* What is iteration?
* Comparing the existing types of for loops (and the `forEach()` method of Array) with the "for… of" loop
* The spread operator and rest parameter `...`
* Using the rest parameter in variadic functions (i.e. functions with indefinite number of arguments)

#### Lesson 7

* Arrow functions with one `x => x.toUpperCase()`, zero `() => console.log("Hello world!")` or multiple parameters ``(x,y) => `Hello, ${x} ${y}!` ``
* Concise body syntax (one line) and block syntax (multiple lines wrapped in curly braces and return statement) for arrow functions
* The value of the this keyword in regular functions (depends on how the function is called)
* The value of the this keyword in arrow functions (depends where the arrow function is located, i.e. its surrounding context)
* Default function parameters
* JavaScript "classes": Coverting ES5 functions into ES6 "classes" (They still use prototype behind the scenes)
* Working with sub-classes (creating a subclass using extends and referencing the super class using super)

#### Lesson 8

* Symbols: Unique and immutable primitive data type that is used as unique identifier
* The iterator method: Function available as `Symbol.iterator` that contains zero arguments and returns an iterator object
* The iterator object: An object that implements a `next()` method, which has to return another object with two properties: `value` and `done`
* Sets: Collections of distinct items
* Modifying Sets with `.add()`, `.delete()` and `.clear()` methods
* Accesing Sets with `.size`, `.has()`, `.values()` and `.keys()`
* Looping through Set items one by one using `.next()` or the "for… of" loop
* WeakSets: Sets that can only contain objects, cannot be looped over and do not have clear() method, used for memory efficiency
* Maps vs Sets: Maps are collections of key-value pairs and Sets are collections of unique values. Maps::Objects like Sets::Arrays (but unlike Objects or Arrays, Maps and Sets are iterable)
* Working with Maps: `.set(key, value)`, `.get(key)`, `.has(key)`, `.delete(key)`, `.clear()`
* Looping through Maps: `.keys()` and `.values()`, "for…of" loop, `.forEach()`
* WeakMaps: Like WeakSets but can only contain Objects as keys
* Introduction to Promises: How to define them and what is their purpose (There is a separate course just for this topic)
* Proxies: Intercepting the code targeting another object to read { get(target, propName ) } or modify{ set(target, PropName, value) }. There are 13 traps
* Difference between Proxies and ES5 getter/setter methods: With the latter, the property names should be known in advance
* Generators: Pausable functions defined with function* that are not immediately executed but return an iterator. It can be advanced with .next() or .next(value) to send data into the function. It will stop at the point inside the function where the yield keyword is used (with or without an optional return value to send outside the function)

#### Lesson 9

* Lack of support for ES6 spec in older browsers
* Checking out browser compatibility
* Polyfill: A JavaScript file that patches a hole by replicating a native feature that the web browser does not support yet
* A Polyfill is just normal JS code, which must verify first that the features are not supported yet to avoid overriding the native implementation
* Difference between compiler and transpiler: A compiler takes a human-readable source language and turns it into a machine-readable target language, changing it into a lower level of abstraction. A transpiler works similarly, but both the source and target language are at the same level of abstraction.
* Babel: JavaScript transpiler that can turn ES6 into ES5 (adding the preset "es2015" in a .babelrc file located at the project root), it requires Node.JS ("babel-cli" and "babel-preset-es2015" are specified as devDependencies and "babel ES6 -d ES5" as build script inside a package.json file located at the project root)
