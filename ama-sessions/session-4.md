## AMA Technical Session #4

**Date**: Tuesday, 21-12-2017 at 15pm-16pm CET <br>
**Mentors**: Paul and Faiz Malkani


#### It would be nice to have code challenges about the lessons just to have others opportunity to understand better the concepts besides the examples in the lessons or even to have more exercises or examples to help us memorize the new concepts. Have you ever thought of creating something like this?
Hey Udacity is about preparing you to build your career in Mobile Web, and as such the lessons, quizzes and projects in the course itself are a generic set of problems to best start you off on the journey. There’s a bunch of more specific readily available problems out there, and the course prepares your base so you can solve them. Of course, if you think it’d be a valuable addition to the course, you can always suggest it as course content :grimacing:

#### Why is the service worker’s lifecycle so weird? is it possible for a service worker to take total control of my browser across all pages?
It is weird, isn’t it? :confused: Fortunately, it’s the most complex part of building a mobile web app. Once you have that figured out, the rest should be a breeze. Google has a fantastic diagram of the lifecycle, which you can find easily by searching service worker lifecycle, and that explains the process in a precise and easy to understand manner. As for your concern, the server worker does not take control of your browser across all pages, but only works with your web app

#### I guess this question is technical somehow, so let me ask: Did you log all the visits to each lesson and the corresponding times, or only the last visit is logged? just to be sure :slightly_smiling_face:
Hey if you’re asking whether Udacity logs all your lesson visits, I guess that’s for Udacity to know, and you to wonder? :thinking_face:

#### The course basically requires some basic knowledge about node.js and the relevant frameworks, but the framework for using Service Worker is not explained clearly in the course. It resulted in doing all of the quizzes but not knowing where to begin when one really wants to start developing from the beginning. Is it because we are expected to have this level of understanding? What web frameworks should we be familiar with if we intend to implement SW in our websites?
The only prerequisites for implementing service worker are HTML, CSS and JavaScript. Some approaches might choose to use frameworks to simplify certain tasks, but you need only the basic three to begin, with a heavier focus on JavaScript. However, if you think the course results in confusion, I’d definitely recommend you send an improvement suggestion

#### Could you suggest any app ideas to practice PWA’s development skills? And do you plan any events like online hackathons or live coding sessions? I’ve almost finished studying course materials and I’d like to get more practice sessions if it is possible.
This repository https://github.com/code-kotis/awesome-pwa-ideas3 and http://pwa.rocks4 have a fantastic set of practice ideas you can use to boost your skills. As for hackathons and live coding, I can’t talk about future plans, so I’d suggest using Udacity as primarily a learning resource, and then building ideas into actual web apps for practice

#### Introducing the Service Worker course and IndexedDB and Caching course should have some appendix with schemas and functions calls.
Sounds like a great idea. I’d highly recommend submitting it as a course suggestion so that the team at Udacity can look into it

#### A lot of relevant people from the webdev world, as @jaffathecake for example, posted yesterday about the inclusion of service worker by default in Safari. Can we hear more how it changes the user experience when having SW by default?
Having the service worker by default in Safari is going to significantly improve user experience as well as development experience. PWAs can now be implemented smoothly on all major platforms, which means less development efforts, and less user bugs

#### In regards to service workers, what update strategy would you recommend? I have read quite a bit on this topic but I’m still unsure, it seems that once an update is detected a user needs to refresh their browser to see the update, can we avoid this refresh?
Service worker updates are triggered if the new service worker has a different file hash (even if one byte is changed) and ignores a browser cache over 24 hours old. It can be avoided by not changing your remote service worker too often and only pushing incremental updates rather than small, frequent updates

#### As far as I understand, the service worker lives on the client code, so anyone can inject malicious service worker code into any website without the user’s knowledge, this is why it forces https. This means if https is compromised we’re doomed right? What about https attack, KRACK for instance, is there any defence mechanism for the service worker?
Security is always important, good thinking. This classifies as a bit too technical, but I’ll say this, your service worker is secure with https encryption

#### How to best utilise this course and can we get one to one support from the course instructors, if so how can we get in touch? Thanks.
The best way you can utilize this course is by completing all the tasks on time, and putting your knowledge into action when your schedule permits. Coding is best learned by doing. As for mentor help, the discussion forums are the best place to look

#### The 2nd part of the course will cover even how to build a web app?
The second part has a three stage app building process and is super exciting :smile:

#### Which versions of node and npm are optimal for course tasks?
The latest stable versions should be good to go. I wouldn’t suggest using a beta or unstable version, since those tend to have a few bugs occasionally

#### My second question is, most of putting so much effort and time learning about google dev tool and service worker and indexDB and es5&6. how is it going to come in handy?
PWAs are spreading fast, and are quickly becoming the new trend for products that don’t require an entire native app download. Learning how the entire ecosystem of mobile web apps works will allow you to fortify your base in the field and thus prep you to build a career in it with a strong foundation and understanding of the process

#### When is the right time to use a sw helper library like workbox?
Once you have a good understanding of what the library does and how it does it, you can use a library to reduce the boilerplate code you write and focus on building the actual app. I’d suggest you use libraries to simplify and speed up your work, not replace the gaps in your knowledge

#### Although the scholarship says Mobile Web Challenge, to what extent can we implement the knowledge in building a "mobile app" (meaning iOS and android apps)?
What you learn in the course doesn’t count towards developing pure native apps other than basic concepts like caching and updating, but the material will significantly boost your learning process of building hybrid apps, ie, web apps in a native wrapper. Frameworks like Ionic and ReactNative are taking off, and in recent times, can provide a purely native experience to the end user

#### I’m building mobile apps using ionic framework and angular , to what extent this course will be useful to me ? is it really applicable and easy to use for mobile apps in ionic framework?
Angular does a lot of the heavy lifting for you when you’re using it to build native apps with Ionic. The course will most certainly help, by teaching you the foundation of what angular is built on, giving you a better understanding of how things work and allowing you to debug issues faster and easier

#### The course is basically divided in two parts: first IDB + SW and the second ES6. Second phase will bring both together? or there is no link.
The second part of the course is about applying your knowledge from the first part to building a three stage restaurant app. It’s super exciting too :blush:

#### Is there anything in specific I need to think about when implementing a PWA with offline first in a isomorphic React app? Or is there no real difference
No real difference, all the techs like service worker, cache and indexedDB will work since you’re wrapping the PWA in a container that doesn’t affect it

#### Why is indexedDB being taught to use in conjunction with the service worker, although the course says it’s apis are bad? Is there a recommended alternative?
i wouldn’t say IndexedDB is bad, just that it’s needs improvement. The idb library that was linked (https://github.com/jakearchibald/idb) adds promises, a much needed feature, and is a good option to use

#### I have a question about IndexedDB is there a way to know what is the size limit that can be stored in it or to get total size of your indexedDB?
Storage isn’t unlimited, and while there aren’t any widespread APIs to check the size of IndexedDB, Chrome and Firefox do have it in the pipeline. Until then, I’d suggest reading this fantastic post about manually calculating the size: http://www.andygup.net/calculate-size-of-indexeddb-database/

#### Hi guys, I have a question about offline first. If i want do a Offline First Mobile Application, not a PWA but a hybrid application using Ionic, can i use service worker, cache and indexedDB? or is only for PWA ? And what’s happen when the app became mobile native application? Thanks all!
Of course, you can use service worker, indexedDB and cache. Ionic is purely a wrapper for a web app in a native container, and wrapping it changes nothing about your web app

#### In the industry a big important metric is performance and start up speed, is there any audit testing like Lighthouse that you recommend to test & improve our applications?
Lighthouse is the best and most comprehensive web app testing tool, but you can try out more mainstream ones like JMeter, Capybara and Selenium

#### Promises are like other new stuff that might not be supported in some browsers. Does idb library handle this issue or should I always use some transpiler?
idb only adds promise functionality to indexedDB and you should definitely use a transpiler

#### Have question relevant to SPA. Now it’s popular to do server side rendering of the pages. How it’s works with service workers ? It’s look like sw should have control of all requests. But in SSR instead of making some requests, we can generate come content on a server. And then sw will cache this html and next time always will return outdated data. So I’m not really sure, are ssr and sw are friends ? :slightly_smiling_face:
Fantastic question, but slightly too technical for the ama which is focused on course roadblocks. Short answer, yes they’re friends, good friends, and can be used alongside each other

#### Should we add integrity tag to service worker scripts links and also the the other scripts?
This is a super interesting debate happening right now. The question becomes the security at the cost of performance trade-off. You should definitely follow it here https://github.com/w3c/webappsec-subresource-integrity/issues/26

#### Is using clients.claim() on the service worker a good practice?
If you use your service worker to load pages differently than they’d load via the network, clients.claim() can be troublesome, as your service worker ends up controlling some clients that loaded without it.

#### If there are a plenty of frameworks like react or angular or vue,how important is to learn to mvc or mvo with vanilla js?
MVC in vanilla js is somewhat daunting because of the inability to separate the framework from the design patterns. Modern frameworks come with their own interpretation of MVC, and I’d suggest understanding how the patterns works and what it’s aimed at (making the solution separable) and then using the version of it that your framework demands

#### I’ve read about handlebars that the template should be surrounded by a script tag, but I see in your templates folder that there’re no surrounding script tag so I get confused, is the script tag optional or handled in another place in wittr project (I mean should be handled somewhere else in general)?
I’d have to look into the wittr source code to answer this, so perhaps it’s beyond the scope of the ama. Maybe I could get back to you on this? :sweat_smile:
