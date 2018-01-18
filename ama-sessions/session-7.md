## AMA Technical Session #7

**Date**: Thursday, 18-01-2018 at 16pm-17pm CET<br>
**Mentors**: Paul and Faiz Malkani<br>
**Written down by**: [Vladi Stanchev](https://discussions.udacity.com/u/vladi.stanchev)

#### Besides SW, is there any tech stack we should learn in the future?
Mobile web is pretty much shaping the future, with more and more users coming online through handhelds. That said, the Javascript space is really expanding at the moment, so it’s definitely something to keep an eye on. The ideal advice is to keep an eye on trends through open source projects, publications, and get on board if you see anyone taking off tremendously.

#### If I haven’t started the course yet because I had overwhelming amounts of work to do, can I still finish it by the specified deadline?
Absolutely. You can begin now and finish it before the deadline!

#### I’m doing the basic android course. There are a lot of lessons on LinearLayout and RelativeLayout, but none of them is about the ConstraintLayout which is the layout used by Android Studio when it starts an application and that, from what I have understood, should be the most convenient layout for complex layouts. Is there a course that covers this topic? Why don’t you insert a lesson on this layout in the basic course?
This is the Mobile Web AMA, but let me quickly touch on your question since I’m an Android dev too. ConstraintLayout is still a relatively newer container layout, and the course focuses on solidifying concepts that have been around since years, like Relative, Linear and Recycler. That said, it IS taking off, so I’d recommend sending an email to Udacity, suggesting its addition.

#### Are social apps like facebook use service worker to save data ??
They definitely do - its the future! Head over to Twitter, Press F12, and navigate to Application > Service Worker to see it in action.

#### Where can I find service worker official icon to put in my diagrams?
Not sure if there’s an ‘official’ icon to represent a Service Worker. Chrome uses a Settings icon, so maybe that’s the closest you’ll get to an interpretation.

#### Registering service workers means opening another thread to download resources and cache them and so… What if the user has a humble network connection and/or memory, CPU, this thread will be an overload in consuming the resources while first opening the site which may lead to bad UX. Is it a good practice to wait until page load then start registering the SW or the ServiceWorker API can handle this point?
Since the whole registering process is event-based, it doesn’t create an issue in the end user experience. That said, the browser and the system are more than capable of handling CPU load.

#### Which one works better with service workers: angular or react?
Most of the work is done in the browser, and Angular and React are just the frameworks. Both work really well with SW, so choose based on project needs and personal preferences.

#### How big, and how permanent is indexedDB? How much data I can safely assume to be stored on clients disk space?
The limit is 5MB on mobile and 50MB on desktop, per site. The data is stored there safely until its cleared either through code or by the user clearing browser data.

#### When developing for mobile devices and tables. How do you usually debug the SW as the Developer Tools are not available? For example, I never know what is happening when I try to run my apps in an Ipad or Nexus tables. Is there a way to show the console. logs in such devices?
Remote Debugging is the way to go. You can connect your device to your computer through a USB cable and ask Chrome Developer Tool to debug on it. For more information, you can see here https://developers.google.com/web/tools/chrome-devtools/remote-debugging/

#### Ideas for websites?! How can I do something useful for humanity? (from my home)
The best ideas come from real problems. Look at your daily life, look at the lives of people around you. Visit areas where the less fortunate live, talk to people about challenges they face in life. Somewhere along the way, an idea will click :wink:

#### When designing an app to deal with data ( example dating sites or something similar), do you think that JavaScript is preferable to use in the back-end side to deal with the databases or Python has priority? and if JavaScript is able to do deal with this task, what database (PostgreSQL, MongoDB …etc) do you recommend in this case assuming the database is really big and JavaScript will be used in the back-end? Thanks in advance.
This question is best answered by you. Weigh the pros and cons - ask yourself questions like “Can JS do this?”, “Is the performance not taking a significant hit?” and “Will this help me achieve my task faster and more efficiently?” If you’re hearing a yes for most of those, then go for it :smile:

#### How will our feedback submitted at the end of each lesson be taken into account in the course (improvements, bug fixes, etc) and will we be notified and/or will you request more details in the future? Can we find what we submitted to share it, when relevant, on the forum? (I didn’t save what I wrote… ;))
The team at Udacity will definitely consider all the feedback submitted. As for will you be notified - I don’t think so, there are thousands of users submitting feedback and it’s beyond the team’s capacity. Can you find what you have submitted - I don’t think so either, your best option is to try to recall what you wrote to some degree and recreate it in the forum post.

#### Are Javascript Workers still in use today? As I’ve never seen a living example of it in any repos or courses I’ve read.
While I can’t manually list sites that do use them, I can say that they aren’t deprecated yet! However, due to the widespread popularity of SW and its adoption, its definitely the more popular choice.

#### Should I use full Babel preset for ES6 or just several plugins according to browsers ES6 features support? Or there is no difference in speed/code optimisations and other advantages?
This is mostly a matter of preference. Try both options, see what works better for your project and your team, and go with that.

#### Is Polymer deprecated? I have followed a Google Codelab to create this web app https://noteapp-7c134.firebaseapp.com/
Polymer hasn’t been deprecated, and it’s being actively maintained and worked on! Check out the GitHub for latest updates and upcoming plans.

#### What are the required feature for defining an App offline-first app? Only SW and cache before fetch data online?
Performing an Audit is basically the checklist to having a perfect offline-first app!

#### In lesson 8 (why we don’t use proxies all the time since they are better than getter and setter)?
The usage varies on a case to case basis. The overall pros and cons of Proxies are:<br><br>
**PROS** <br>
* Simpler (internal) binding code
* Ability to detect new properties (Vue.set would no longer be needed.)
* No modifications to the original object need to be made

**CONS** <br>
* There’s no way to simulate a consistent behavior in browsers that do not support it
* There’s no way to maintain reference consistency for observed objects.

#### Should we apply our knowledge from the course to vanilla javascript es6 project or use framework like Angular or other (knowing that appreciatively all of them added CLI for configuring SW automatically)?
I’d suggest getting the hang of both approaches, and then choosing one to deep dive into based on project needs, personal preference and employer priorities, while at the same time keeping yourself open to adaptation should the trends change.

#### In ES6, is there a way to simulate protocols/interfaces and abstract classes like other OOP languages?
While Javascript does support those features through Typescript, and transpilation, it wasn’t meant to be an object-oriented language. However, if personal preference demands it, you can use Typescript, and look at workarounds, such as this article on implementing classical Inheritance in JS: http://www.crockford.com/javascript/inheritance.html

#### In the famous 8.4 - iteration Quiz there is statement that the .next() method should return object with 2 properties (value and done), in the quiz itself 3 properties are needed (key, value, done), and in the MDN example there is line of code that returns only one property (done). Apparently, all three ways work. Is there any “right way”? I’m confused about that.
The difference lies in the direction of execution. next() returns two properties, done and value. However, you can provide a parameter to the next method to send a value to the generator.

#### Is there showcases and numbers that explain the impact of service worker … something like this?
I can’t list numbers off the bat, but this page does provide some metrics on the Google I/O PWA: https://developers.google.com/web/showcase/2016/service-worker-perf

#### What about Flow for static typing in JavaScript? Is something used or more of a prototype?
Flow is definitely more than a prototype and a perfectly valid option for static typing in JS!

#### Is the web “leaning” toward streaming apps and SW is opening the door for that?
The best I can do on this is an educated guess. Some large organizations are indeed learning towards streaming or partially downloading apps, but there’s no way to tell if the rest of the web will lean that way. However, SW is indeed helping this cause tremendously.

#### What is the purpose of hoisting? and will we still use it after releasing ES6 and ES2015? I see people say let is the new var what do you think?
let has limited use cases, and a scope limited to the block or expression, while var is more independent of the block. Both have their own pros and cons, here’s some good reading on that: https://scotch.io/tutorials/understanding-hoisting-in-javascript

#### In designing a logo to an app if the logo can be designed using canvas (API in HTML5), is it preferable to include its code in JavaScript file rather than including it as an image ? i.e. I will like to know your opinion about the idea of using logos made by codes rather than using  tags in html files.
Ultimately do what’s best for you and your team. My opinion is that if you’re going to spend 4-5 hours writing code to draw a logo, vs 4-5min for dropping in an image, all to save ~20-25KB, then the choice isn’t too difficult, is it?
