## AMA Technical Session #8

**Date**: Thursday, 24-01-2018 at 16pm-17pm CET<br>
**Mentors**: Paul and Faiz Malkani<br>
**Written down by**: [Dorijan Tomic](https://discussions.udacity.com/u/dorijan11lfpvv)

#### I don’t know whether this question was asked before or not, but I really like to know how to start with Node.js, Grunt/Gulp/Browserify/NPM Scripts and so on! There are really rare tutorials out there and most of them aren’t really up-to-date! A ressource would be awesome! My intense is to start a PWA from scratch with websockets, service worker(s), push notification and so on. Thanks in advance,
Hey Daniel, one of the best ways to start off is to use a Codelab from Google3 - those are up to date and easy to follow along. They guide you through all the steps needed to build a PWA, and are great ways to practice :slightly_smiling_face:

#### We know that this slack channel will still available one more month after the end of the course, but what about the forum? How long it will still available or maybe it will last long yet?
Hey Tatiana, forum access will cease once the scholarship is over

#### Hi, me again: what is the strategy to use in learning implementation of sw tools: sw-precache or sw-toolbox or workbox? Is it better to begin with sw-precache then sw-toolbox and finally using workbox?
Hey Focus3D, Workbox is the successor to sw-precache and sw-toolbox. It adds more tools, simplifies the process and expands the functionality, so you can dive right in to Workbox to get started :slightly_smiling_face:

#### But when using Set or Map in lesson 8 we always declare them as ‘const’ though their value change with .add or .delete … Should we not declare them with ‘let’? Is there a difference in memory management?
Hey Psam, the only difference between const and let is that const makes the contract that no rebinding will happen.

* use const by default
* only use let if rebinding is needed
* (var shouldn’t be used in ES6)

#### When we wrote the application for the scholarship, I remember there was a field asking for a github profile. is there any way to change or double check it?
Hey Adrian Dinca, I’d suggest sending an email to Udacity support, notifying them about the change

#### Is there any problem about SEO with Service Worker? By example, I knew FB robot will read the page at first and find the meta og, so can we consider it like a consumer or a client with browsers, will it get the update with the latest data through SW or not?
Hey Tho Vo, these robots usually take on a client behavior and user agent, so yes, they will use a service worker and get the latest updates using it!

#### I would like to know more about the entire process of making an app. Like maybe first it is an idea (or a discussion with the client - user story). Then maybe it should be a diagram with the process flow. Then some research about other apps like that. Then choosing the right tools and technologies… and so on until the final release day (…and even after: maintenance, updates)
Hey Dan, you’ve got the process almost nailed down. Ideation > Storyboarding and Flow > Competitor Research > Choosing stack > Design > Development > Testing is a typical flow with the added component of research. Include research at every stage of your product cycle, to save you from making wrong decisions further down the line

#### How can a JavaScript/ES6 solution compete with an JavaEE one in similar ways?
Hey Adrian, Javascript is typically used more on a client side, with JavaEE being a server-side option

#### What approach you take when start learning new technology ?
Hey abdoutelb, I’d suggest starting out with what the tech is about, why it was built and what problems it aims to solve, then diving into potential applications, before actually learning it, which will help you figure out if its worth your time. Once that’s done, start with the basics, and learn the advanced part on the go, practicing by building real projects

#### I’m having a hard time to find some balance between building and learning to build . Any advice ?
Hey Amanuel, I like Franz’s answer - balance both. Pick an idea you know you can’t solve with your current knowledge, then pick up the.

#### Is there a good guide about using Service Workers with React? The create-react-app module has its own Service Worker implementation but I find it somewhat hard to customize it the way we did in the course.
Hey alexander-luna, this series by none other than Addy Osmani is great at solving such issues CLICK ME1 for the link to the series.

#### What do you think the web still doesn’t do well enough? Customized video player? Scrollbars and scrolling? Etc
Hey Gilad Feder, this question is subjective, since all of us have our own nitpicks. I personally think that video playing on mobile can be improved, but that’s moreso a client problem than a web one

#### I just recently read an article about using C++ to write web, with the power of ES6, NodeJS, new technologies like SW, do you think in the future, we can use JS to write embedded software? We already had some desktop application written in pure JS
Hey Tho Vo, this could definitely be a viable option. If 10 years ago, people had said Java would be the least preferred option to write apps, nobody would have believed them :wink:

#### Why would we use polyfills when we have transpilers? what did I miss? I do understand that browser that support the newer way could then use it, but is there benefits in speed or something etc?
Hey Mika and Doki, while polyfills and transpilers serve the same purpose, they do vastly different things. A polyfill will try to emulate certain APIs, so can use them as if they were already implemented. A transpiler on the other hand will transform your code and replace the respective code section by other code, which can already be executed.

#### Is There is a way to use SW over HTTP?
Hey amanfrinati, service workers require HTTPS, with the reasoning being explained here

#### Regarding Mobile Web, how is the future of Google’s Flutter?

Hey jsoetens, I can’t say for sure since my crystal ball isn’t working correctly :wink:
However, Google is doing a tremendous push for it and it’s definitely a good skill to pick up. That said, I always suggest that don’t dive too deep into one topic until you’re sure you want to do it, and always keep yourself adaptable to change

**The cache size of service workers are limited and different for each browser. I’ve read Chrome and Opera have a limit of around 6% of hard disk space but the storage is per origin (rather than per API)… **

#### What does ‘per origin’ mean? (is it per domainname?)
Hey Jozzeh, you’re correct. It refers to the top level part of the url, not just the domain name. For example, localhost is an origin, google.com is an origin, but google.com/io and google.com/mail have the same origin

#### With Javascript ES6 and coming ES7, and CSS new features support, should we be used to abandon jquery in favor of native javascript and css transform … and is it better to use polyfills now to get rid of them later when all browser will support the new features?
Hey Focus3D, this question is best answered by your team and product managers. Ask yourself questions like:

* Will abandoning jQuery speed up my development, or will it increase time since people are familiar with it?
* Should I use polyfills now when the codebase is smaller and more manageable, or can I not afford to rewrite in future when uptime is important

This will typically help you reach a conclusion :wink:

#### For CORS, caching resources using cache.add, or cache.addAll, will fail (and then registering SW) if it’s not explicitly allowed in the header, but I think this is not always insured. Another solution is to fetch them and cache them manually using put() but in this case the response is (as they sometimes called) “opaque”. Which is better? or it depends ONLY on my app? any more guide
Hey Asmaa, this is a widely discussed topic and developers choose to work with what works best with the team and ecosystem. Here’s some reading to help you with this choice LINK 1, LINK 2.

#### Before this challenge, I haven’t heard about PWA and its inner features (like the Service Worker and so on). What do you think that’s gonna (or it’s being) be a hot subject for mobile-web development, like right now it’s PWA?
Hey melocotonero, the best way to stay updated is by following mobile web personalities on social media, and subscribing to repositories and reading lists. Some topics that are gaining traction are React and Flutter, which are old enough to have a firmly established adoption but new enough to have a high demand

#### What would you say is the one thing a Web Developer should learn or get to know in 2018
One thing for all developers to learn is that tech is a moving stream and one should always be adaptable to change. That said, some topics of note are AI through chatbots, CSS animations and SPAs

#### Is there any open source project with high number of contributor using SW we can join, contribute, and learn from?
Hey Tho Vo, here are some:

* https://github.com/w3c/ServiceWorker
* https://github.com/GoogleChromeLabs/application-shell
* https://github.com/mdn/sw-test
* Google I/O app repo

#### Talking about AI, Faiz Malkani, do you have any favorite resource for first introduction?
Hey elise.patrikainen, this fantastic series walks you through building a Google Action using Dialogflow (formerly api.ai), the most popular AI development platform for bots: [CLICK ME](https://rominirani.com/tutorial-getting-started-with-google-actions-with-api-ai-a3b79550a062)
