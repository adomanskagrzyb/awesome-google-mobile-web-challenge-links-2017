## AMA Technical Session #6

**Date**: Thursday, 11-01-2018 at 15pm-17pm CET<br>
**Mentors**: Paul and Faiz Malkani<br>
**Written down by**: [Dorijan Tomic](https://discussions.udacity.com/u/dorijan11lfpvv)

#### What would be a good example of practical usage of WeakMap and WeakSet?
Hey jesperzach, a WeakMap is typically used to store Weak references to any data. A weak reference isn’t strong enough to force an object to remain in memory. Weak references allow you to leverage the garbage collector’s ability to determine reachability for you, so you don’t have to do it yourself. Thus, you’d use a WeakMap can be used as a short-lived cache of keys to derived data. It can also be used to keep information about objects used else where and you don’t know when those objects are discarded. Additionally, if you need the data to be iterable, have a .size property, have unique keys have .delete and .clear for all its properties, you’d replace the WeakMap with a WeakSet

#### In SW install event we add the stuff to the cache, what if there’s not enough memory, the SW will never be Installed, and the client will lose the benefits of SW. Is it a good practice to check for available memory first? Is there any bad consequences to ask for more memory to store all what we want? Do u see that Storage Quota Estimate API is recommended more than Quota Management API, or there’s another better way?
Hey Asmaa, great question. your origin is given a certain amount of free space to do what it wants with. That free space is shared between all origin storage: LocalStorage, IndexedDB, Filesystem, and of course Caches. However, this isn’t fixed and will vary on certain conditions, thus checking for memory is a great idea. However, requesting more space isn’t a good practice because the typical limit is 5MB, and if you’re persisting more than that much then you need to revisit your code. estimate() is a great way, and the widely preferred method of checking storage, and can be read about in detail here: https://developers.google.com/web/updates/2017/08/estimating-available-storage-space

#### Is there any recommendation for a library helps generate ServiceWorker’s boilerplate (production - ready service worker ) when starting a new project, I read about WorkBox any advice is appreciated .
Hey Mzn09, WorkBox is typically the preferred choice for the web community, and thus has a high rate of maintenance, fixes, updates and PR merges. While there are a bunch of third-party options, WorkBox is a Google project and thus makes it the primary choice!

#### An idea to improve this course would be to have a little bit more text to read in the SW/IndexDB part like in the Es6 part. So you can re-read something instead of skipping to a specific part of a video.
Hey, Dennis Roth, that sounds handy. I’d suggest sending an email to the Udacity team outlining which sections need more text content, I’m sure they’ll look into it

#### Service worker and indexeddb it’s lot to take in. I have take lo lot of notes during the lessons. I was wonder if we will still get overall master piece of service worker and indexed with lot of comments for future reference?
Hey Zak, I personally am a big fan of learning through practice. Brush up on your notes, come up with a simple idea, and start building. Alternatively, if you don’t want to build an idea, do a codelab (https://codelabs.developers.google.com/codelabs/offline/1), and whenever you run into a bug or a problem, look it up. Perfection through practice is very real.

#### How would Google’s Engineers implement the Service Worker fallback for browsers such as Apple’s Safari browser – where the development of SW just began without a set deadline?
Hey Gawee, the largely accepted practice is if a browser supports service workers then the service worker caching will be used, instead of the appCache manifest. You can include the appCache manifest for legacy browsers like Safari and things will work the way they did in the past. Plus for modern browsers they will leverage service worker caching and act as if the appCache does not exist.

#### Does Google uses the SW to fetch better results to search ?
Hey Can, open the browser’s dev console, go to Application > Service Workers. You’d be surprised how much you can find out about a site through that handy panel. Do share your results with us.

#### (Ignore my question if it is not topic related for today’s session) Two students Hisham Abdelalem and Carlos Nogueira shared their handwritten notes and as a student myself I really respect and appreciate that as it is given other students an example on how to take the course. I myself take handwritten notes and I am asking it is advantageous vs taking notes on some app?
Hey Focus3D, while it isn’t on topic, I’d like to chime in that taking written notes is proven to provide a deeper understanding. Check this out: https://www.scientificamerican.com/article/a-learning-secret-don-t-take-notes-with-a-laptop/

#### Hey! Last year I’ve been working with AngularJS and I never used javascript “classes”. Now that I’ve seen them on ES6, the question comes to my mind. What do you use them for? Thanks!
Hey Pablo, JavaScript’s “classes” aren’t anything like classes in Java, Python, or . . . Really, any other object-oriented language you’re likely to have used. Which, by the way, I’ll refer to as class-oriented languages, as that’s more accurate. JavaScript’s class is (mostly) just syntactical sugar for prototypes. “Instantiating” a class in JavaScript does create a new object, but not one that is independent of its parent class. Rather, it creates an object that is linked to a prototype. Changes to that prototype propagate to the new object, even after instantiation.

#### The life time of a service worker is weird, as said by Jake in the videos. My question is if the lifetime of a SW can be somehow controlled and modified by our code?
Hey Luiz Carneiro, like George said, there are limits to what you can and cannot do in controlling the lifecycle, all detailed on https://developers.google.com/web/fundamentals/primers/service-workers/lifecycle

#### What do you think the best way to practice on Service Worker various features?
Hey Mostafa, like I said in an other answer, I personally am a big fan of learning through practice. Brush up on your notes, come up with a simple idea, and start building. Alternatively, if you don’t want to build an idea, do a codelab (https://codelabs.developers.google.com/codelabs/offline/1), and whenever you run into a bug or a problem, look it up. Perfection through practice is very real. Additionally, an awesome list of service worker resources is available at https://github.com/TalAter/awesome-service-workers.

#### Could you kindly name some example of using iterator of the iterable object ?
Hey Lesia Yevtushenko, an example is typically too technical to detail in this AMA, but I’d highly recommend reading this article since it clears everything up with examples, code samples and flowcharts http://www.dofactory.com/javascript/iterator-design-pattern

#### Due to the highly changing ES6 support, which bundling tool would you recommend right now to use (Webpack, Grunt, Gulp…) alongside with Babel?
Hey melocotonero, this is mostly a choice based on personal preference combined with project needs. Here’s a quick breakdown:

* grunt and gulp are task runners to automate everything that can be automated (i.e. compile CSS/Sass, optimize images, make a bundle and minify/transpile it).
* grunt vs. gulp (is like maven vs. gradle or configuration vs. code). Grunt is based on configuring separate independent tasks, each task opens/handles/closes file. Gulp requires less amount of code and is based on Node streams, which allows it to build pipe chains (w/o reopening the same file) and makes it faster.
* webpack (webpack-dev-server) - for me it’s a task runner with hot reloading of changes which allows you to forget about all JS/CSS watchers.

#### What I’ve got from the course (SW part), one can cache static resources from other origins (other than the application’s one). But does it make sense to cache frequently changing responses from other origins (like for example google maps API)? If it does, can you please provide some use-cases. Thank you in advance!
Hey Daria, the term ‘static’ refers to resources that don’t change, and it is only recommended to cache resources that aren’t expected to change. Jake has a fantastic article on best practices: https://jakearchibald.com/2016/caching-best-practices/1

#### How will you persuade your manager/ your team to start using/writing Offline first, can you share some of your experience?
Hey Tho Vo, that’s easy. Throttle your phone network to 2G from Settings, and ask your team to use a network heavy app. While they’re waiting for content to load, use that time to outline that this loading time wouldn’t exist in offline-first apps.

#### If we want to do a PWA using Angular framework, there are some tips to keep in mind for better using of service worker?
Hey Pamela Fracassa, I recommend that anyone who’s working with service workers have this bookmarked https://serviceworke.rs/2  Aside from that, some gotchas are outlined here - https://www.kollegorna.se/en/2017/06/service-worker-gotchas/

#### What is preferable for a mobile device in your opinion: make a PWA application or a hybrid one with some PWA features?
Hey Daria, the conversation around this is vast and somewhat inconclusive. I’d suggest keeping your use case in mind, evaluating factors like app store visibility, website discoverability, and what your company needs. This is also a great resource to help make this decision: https://blog.itnig.net/what-app-to-build-in-2017-native-hybrid-or-progressive-web-apps-e1dd31c11aa5

#### So in the course we associated SW with the sw.js file, but can I associate it with more that 1 file? split into 2 files? a whole another project?
Hey furetur, like George Karantanis said, one service worker per scope is the rule. However, intercommunication between service workers is completely possible and can be oneWay, twoWay or broadcast.

#### What’s the difference between iOS and Android in terms of PWA? as far as i know you can’t do some things on iOS, or should use some workarounds. Also is there any automatic testing tools for PWA on mobile.
Hey Ruslan D, Safari is somewhat lagging in modern web features, but that’s all set to change in the upcoming months. Safari’s latest Technology Preview supports Service Workers, and I’d suggest keeping an eye on https://caniuse.com/#feat=serviceworkers to come to know when it goes live. As far as I’m aware, there aren’t any mainstream automatic testing tools on mobile, but I’d love to know if you find any.

#### How I can integrate Babel into my project to automatically add polyfills in my projects … ?! I am confused with this point !!
Hey Tawfiek, here’s a handy guide to setting up Babel Polyfill https://babeljs.io/docs/usage/polyfill/

#### I’ve read a lot of good and bad things about ES6’s new class syntax - while some like it, a lot of people recommend not using it at all and say it’s bad because it can lead to a highly dependent code structure where a change in one class can easily break a lot of different other parts of your code. Now I’m quite uncertain whether I should actually use classes in my projects or not, what’s your take on that?
Hey Jonas, Numerous developers hate classes and assert that Javascript is a prototype based language. I personally believe that Javascript should not be considered a functional language, or an OOP language, but rather a language that has both functional and OOP elements. I also believe that getting the job done should be the main priority, while keeping the codebase maintainable - use classes and inheritance when they best model your problems, and use functional elements only when they’re the best fit.

#### Is there any scenarios where it’s preferable to bypass SW, fetching big videos for instance or so?, I noticed in your wittr project that there’s a probability to bypass the SW in (wittr/public/sw/preroll/readme & index.js)
Hey Asmaa, bypassing the service worker is a completely valid option, with some use cases being video from an origin that doesn’t support CORS, a frequently changing profile picture, segments of a 360 VR photo, etc.

#### Will SW be a must-have feature in almost application in the near future?
Hey Tho Vo, with offline web taking off at a tremendous pace, the service worker and offline-first approach to web apps are definitely going to be a must-have in most modern web apps, and with this course, you’ll be prepared to adapt to its spread in popularity!

#### I struggle to understand correctly how the various component grunt, npm, lint, babel work together in the development environment and how deployment process woks. Is there any guide that I could read about set up the development environment from scratch?
Hey enrico, I’d recommend reading the Hitchhiker’s Guide to Javascript Tooling, establishing your project needs, and then following the post that Konstantin.Shpikat linked. http://reactkungfu.com/2015/07/the-hitchhikers-guide-to-modern-javascript-tooling/

#### Any suggestions for PWA and SEO, and adding PWA concepts to WordPress site besides Surma video at https://www.youtube.com/watch?v=Di7RvMlk9io thank you
Hey Focus3D, here are some great resources:
* https://moz.com/blog/introducing-progressive-web-apps
* https://seo-hacker.com/improve-seo-indirectly-progressive-web-apps/
* https://wpmobilepack.com/blog/building-progressive-web-apps-top-wordpress/
* https://searchengineland.com/google-progressive-web-apps-mobile-experience-seo-259866

#### I’m awfully sorry, maybe someone asked about this before. But what’s the difference between “Google Developer Challenge Scholarship: Mobile Web” and Offline Web Applications course + ES6 course on Udacity? It seems same awesome free courses with same awesome content. But…what’s the catch?
Hey Igor Piskunov, no catch at all. However, completing the course through the Google Developer Challenge Scholarship gives you access to dedicated forums, quick mentor support, a dedicated Slack, and AMA sessions like this one :smile:

#### This is from wittr -> public/js/settings/tests/index.js - line 495 response is always undefined here and the test always shows “Photos aren’t appearing in the…” even if the task is solved and working. Task-cache-clean is surely solved here because this is the next branch: task-cache-avatars`
```['cache-clean']() {

return remoteEval(function() {

  return caches.open('wittr-content-imgs').then(cache => {

    const imageUrlMedium = '/photos/4-3087-2918949798-865f134ef3-640px.jpg';

    return fetch(imageUrlMedium).then(r => r.blob()).then(() => new Promise(r => setTimeout(r, 500))).then(() => {

      return cache.match('/photos/4-3087-2918949798-865f134ef3').then(response => {    
        if (!response) return ["Photos aren't appearing in the cache where we'd expect", 'not-quite.gif', false];
```
Hey Dan, this seems to be a valid issue at a glance. I’d suggest reporting the issue from the course dashboard so that the team can take a deeper look at it.

#### Is there any argument against using service workers with javascript framerworks? (Angular, vue, react etc.)
Hey Katarzyna, on the contrary, developers everywhere choose to combine service workers with Angular and React to form optimal, offline-first and modern webapps

#### if i grant service worker to send notification , and new version from it is out how can i control this from browser. I saw lately a mining threat through service worker
Hey abdoutelb, most browsers have a setting to control this. For example, here’s an article detailing how to do it on Chrome for Android: https://support.google.com/chrome/answer/3220216?co=GENIE.Platform%3DAndroid&hl=en

#### I’ve read somewhere, that if your browser support SW it’s support ES6 also, so you can cache to service worker not transpilled ES6 and for others you’ll send a transpilled version of your code. Have you had some experience with it ?
Hey mako, this is not completely true, just mostly true. For example, UC Browser on Android partially supports Service Workers, but doesn’t support ES6. However, the vast majority of browsers that support SW also support ES6, so yes, you can cache to service worker and send a transpiled version to others.

#### I have a question that is related to webpack and service workers. What is the best way of adding a service workers in a project that is bundled with web pack? Will the added boilerplate of webpack disrupt the service worker? and are there any concerns with big SW files(as web pack will bundle the required files)? and should I transpile SW files with babel, it feels unnecessary since SW is a new addition anyways?
Hey Samuel, the easiest way is to use a plugin to do the heavy lifting for you, such as something like this: https://github.com/oliviertassinari/serviceworker-webpack-plugin. Additionally, I’d suggest transpiling service workers even though SW is a new addition if you’re aiming for 100% coverage.

#### Is it possible to use a SW for making a PWA that displays a Google Map and POI’s (point’s of interest) on? For example lets say i have a business directory website (in wordpress), and for every listing i’m also displaying a location using Google Maps. 1)Is it possible to also cache the map tiles for a specified number of zoom levels? 2)Is it also possible to have routing functionality while offline? 3)Where can i find more about this, combining a SW and Google Maps?
Hey Teo D., while caching is primarily for static resources, you can cache Google Maps by including the logic in your fetch handler that examines event.request.url and takes whatever arbitrary action you’d like to return a Response from a cache, or even create a new Response on the fly. Here’s some reading on CORS and Google Maps: https://developers.google.com/api-client-library/javascript/features/cors#using-cors1
