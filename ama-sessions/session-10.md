## Final Technical [AMA] Session on Slack #10

**Date**: Tuesday, 30-01-2018 at 17pm-18pm CET<br>
**Mentors**: Paul and Faiz Malkani<br>
**Written down by**: [Dorijan Tomic](https://discussions.udacity.com/u/dorijan11lfpvv)

#### Is it correct to say that the new ES6 classes is a proxy of the old one ? i.e. if we declare a class using ES5 and we declare same class using the new syntactic sugar of ES6 , are the two classes proxies of each other ?
Hey Mzn09, great question, you’re correct. Since ES6 class declaration syntax is just syntactic sugar, and the ES5 declaration is still perfectly valid, the classes do proxy each other.

#### Is using an IdexedDB a good approach to cache data received from the API. In this case I am receiving apartments, which I can book later on. The whole so called “apartment” object arrives from exterior server via their API, the only thing that changes is if it booked or not.
Hey mkbeectrl, that’s a good approach, but it’ll only make a difference if you can make selective API calls - for example if you can provide an apartment ID in your call and get whether or not it’s been booked. If you’re going to refetch the entire object anyway, then you’re not going to see much of a difference

#### How do we know wich is the best Offline Cache Strategy on our Mobile Web App?
Hey javiexpo, there’s no “best” strategy - picking the correct option is totally dependent on your needs. For example, the Pokedex.org Progressive Web App uses IndexedDB for application state and the Pokemon data set while the Cache API is used for URL addressable resources. Check out this fantastic article about this subject: https://medium.com/dev-channel/offline-storage-for-progressive-web-apps-70d52695513c

#### What type of application is suitable for using Service Worker? Is there any stack of technologies we should go with SW that you can recommend?
Hey Tho Vo, look at your app carefully. Does it need features like offline support, sending push notifications, doing background sync with service workers, client-side load balancing, etc? If so, you need service workers. As for stacks, service workers work fantastically with modern frameworks like React and Angular, so it’s completely a matter of usecase and preference

#### Transpiling or polyfilling. When to use which and why?
Hey Logician724, the definitions answer both your questions - a polyfill will try to emulate certain APIs, so can use them as if they were already implemented, while a transpiler on the other hand will transform your code and replace the respective code section by other code, which can already be executed.

#### In order to make our app offline first, which tools would you recommend? I recently found out about workbox for example. Is this a good option for most browsers?
Hey nimrod13, Google’s been the pioneer for the mobile web in recent times, so most of their tools are fantastic. Workbox is the successor to older tools and a must have, while another great tool is Lighthouse, which lets you audit and check the integrity of your apps

#### Are any limits for storage content in the IndexedDB? … Or is a variable that depends on the storage of the devices?
Hey javiexpo, for IndexedDB, you can use up to 50MB on desktop, 5MB on mobile for free. However, the user can allow the limit to be removed by granting permission.

#### A lot of the course covers changes from ES5 to ES6. I noticed that ES7 and ES8 have also been released. Should we spend time learning the changes for these editions? Is there anything in these editions that you’d definitely recommend looking into? Or are these not as important as the jump from 5 to 6?
Hey mark, I’d suggest prioritizing the current version, but also going over the previous versions and seeing what changed and why. This will give you a better understanding of how a certain snippet works, and where its best suited to be applied

#### With each level of abstraction things got slow, is it applicable to js for the ES6 ?
Hey abdoutelb, as with all languages, it does apply to ES6 too. However, this prompts me to quote Donald Kruth - "Programmers waste enormous amounts of time thinking about, or worrying about, the speed of noncritical parts of their programs, and these attempts at efficiency actually have a strong negative impact when debugging and maintenance are considered. We should forget about small efficiencies, say about 97% of the time: premature optimization is the root of all evil. Yet we should not pass up our opportunities in that critical 3%." In other words, optimize when and where your profiler shows that you need to.

#### During the course about IndexedDb Jake says he will chicken out and use a library, and then Jake recommends an IndexedDB library of his choice. Now, is that library widely used in Google’s own productions (because I believe you all have gone through these decision makings with your teams before) or did you go with another custom library, or go through the pain writing directly to the API? Or do you have another library you would recommend for production?
Hey Gawee, I personally use a custom library, because I believe that rewriting code slows down my progress. However, I’d suggest understanding what exactly the library is doing for you rather than just importing it. Some fantastic options are Jake’s own library, or Dexie:

* https://github.com/jakearchibald/idb
* http://dexie.org/

#### From your perspective what are the topics should I focus on learning to be a web app dev? And can you suggest a learning path?
Hey faragDev, from my perspective I’d suggest spending less time thinking about what to learn, and spending more time doing - the knowledge comes automatically along the way :wink:

#### Hey Faiz Malkani, what type of images shell we cache? should we cache only optimized images or should we try to cache the best looking images?
Hey Miguel Costa, depends on your usecase - if the best looking images are too many and are going to push your usage over the limit, then perhaps you should downgrade what you’re caching.

#### What advice do you have for dealing with high intense data applications, I’m working on a Angular App which utilizes a REST API to keep the Graph State live, It vigorously polls an API and fetches a 3 - 5 mb file, which is a collection of Entities. Is there a good Method for me to improve caching?
Hey howardpanton, does caching apply in your use case - sorry I haven’t completely understood your situation. If you’re vigorously polling an API to keep a graph state in realtime, what purpose does caching have?

#### Hey, I’m from design background (UI/UX ) and learning service workers was challenging for me, what do you recommend to learn more about, to understand indexedDB part? Another question, Can I implement both jQuery & ES6 in the same project? or should I stop using jQuery after using ES6?
Hey Mai, first of all, high-five :hand: - designer/developer here as well. From personal experience, I’d suggest starting off with how databases work, then moving on to RDBMS versus key-object pair storage, and then finally coming to web-based storage protocols and structured data storage for websites. And yes, you can use both. However, a lot of jQuery functions can be done in native ES6 so check how much you need jQuery before deciding to use it as well

#### Is there a point in upgrading a photography portfolio site (gallery) into PWA? Provided that it’s not an everyday web tool that clients use.
Hey Chris, if you have the time, then definitely. Most web users are now mobile based, and the likelihood that someone’s going to look at the site via mobile is high. As for your caching concerns, perhaps you could cache low-quality versions and then fetch the original ones.

#### Base on your knowledge and experience; Wich front-end framework (ReactJs, Angular, Polymer) are more suitable for Mobile Web App that will implement Offline First approach?
Hey javiexpo, there’s no best option. All work really well, so pick one that suits you best, decide what’s best for your team and the project, and go from there!

#### As someone who’s never used any kind of framework iv’e been suggested by someone to start with React just because it’s closer to vanilla JS , and start small projects with vanilla JS and then make the same project with react, is that a good way to learn different frameworks? Should i learn React first because it’s closer to Vanilla?
Hey Doki. learn what’s best for your project and your team. Some frameworks might have a higher learning curve than others, but eventually through persistence and hard work they all make sense. Learning one framework and adapting all projects to it is a dangerous practice

#### I see 5mb is not too much for storing data on mobile with IndexDB, by example, if I am trying to do some web app like Quora which user can upload a lot of image in their post. it may overlap the limit of 5mb when we try to cache the data we receive the data from server, in this case, how can we solve this problem? should we need to define a strategy to choose which one to cache?
Hey Tho Vo, a good practice is to cache links to images in your storage, and load those images when you’re online. However, some sites do choose to cache low-resolution versions of images and fetch the full versions each time

#### When trying to develop a web app is using a framework a better approach or write your own code from scratch… there are so many JavaScript frameworks out there?
Hey Sam Phiri, like the others said, don’t reinvent the wheel and slow down your project. However, understand clearly what the framework is doing for you and how its doing it, so you can optimize accordingly and not do something like `wholeInternet.download()`

#### Hello! What do you think about integrating blockchain technologies for making apps more secure?
Hey Adrian Sav, first off, blockchain solves a trust problem primarily. Second, one advice that I give to people every time a new tech is launched - don’t pick the tech stack and then build the product on top of it. Come up with the idea and then choose a tech stack based on use case

#### How to protect our app from crackers?
Hey @MohaM, I laughed, because I imaginedthis and wondered how they could violate your app. However, here are some good links on app security:

* https://developer.mozilla.org/en-US/docs/Web/Security
* https://www.beyondsecurity.com/web-security-and-web-scanning.html
* https://medium.com/@urish/fortunately-the-pwa-apis-are-being-built-with-security-in-mind-721bcc9e7764

#### Are PWAs more common in areas/countries with slower internet speeds? In my environment PWAs are not very known to the general users. Most users and developers stick to normal apps.
Hey Niklas Merz, they’re very popular in such areas, because of the internet speed and also because such users tend to have lower end devices with limited storage for large native apps. However, the trend is spreading fast and many products are opting to go this route

#### I have seen that Udacity site doesnt show the dainsor connection error when I have been offline on my laptop does that been done using service workers also
Hey Khaledkzy, you should find out :wink: A great way to check if a site is using a PWA is to open the console, open the Applications tab and click on Service Worker
