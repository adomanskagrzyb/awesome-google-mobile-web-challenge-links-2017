# Lesson 3: Service Workers

[<= GO BACK ](../README.md)

If some of the topics in lesson 3 were new to you, we hope the resource links will help.

## Resource links

* [Firefox: Service Workers (explained)](https://developer.mozilla.org/en-US/docs/Web/API/Service_Worker_API/Using_Service_Workers)
* [Google Web Fundamentals: Overview](https://developers.google.com/web/fundamentals/primers/service-workers)
* [Google Web Fundamentals: Service Workers Life Cycle](https://developers.google.com/web/fundamentals/primers/service-workers/lifecycle)
* [Firefox: Cache](https://developer.mozilla.org/en-US/docs/Web/API/Cache)
* [Firefox: Service Worker API](https://developer.mozilla.org/en-US/docs/Web/API/Service_Worker_API)
* [Firefox: CacheStorage](https://developer.mozilla.org/en-US/docs/Web/API/CacheStorage)
* [High-performance service worker loading](https://developers.google.com/web/fundamentals/primers/service-workers/high-performance-loading)
* [Google Chrome Developers video: Introduction to Service Workers](https://www.youtube.com/watch?v=jVfXiv03y5c1)
* [Mozilla Service Workers examples](https://serviceworke.rs/)
* [JavaScript Promises for Dummies](https://scotch.io/tutorials/javascript-promises-for-dummies)
* [Jake Archibald: The offline cookbook](https://jakearchibald.com/2014/offline-cookbook/)
* [Service Workers 101](https://github.com/delapuente/service-workers-101)

## Libraries

* [Google Workbox Libraries](https://developers.google.com/web/tools/workbox/) Collection of tools and helpers for working with Service Worker
* [Zack Argyle (Pinterest)](https://github.com/pinterest/service-workers) Utilities for creating, testing and experimenting with Service Workers

## Overview
The service worker intercepts all requests the user makes. It can send the request straight to the server or first try to load cached data while requesting new data from the server.

![service worker](https://www.smashingmagazine.com/wp-content/uploads/2016/11/service-worker-offline-large-opt.jpg)

## Creating cache and saving information in the cache

```Javascript
caches.open(‘cache_store_name’).then(function(cache) {
    return cache.addAll(urlsToCache);
})
```

It is possible to use these three ways to store information in cache:

* `cache.add(request)`: stores single request
* `cache.addAll(request)`: stores an array of requests
* `cache.put(request, response)`: stores a single request and its response


## Fetch cached and non-cached data

```Javascript
caches.match(event.request).then(function(response) {
    return response || fetch(event.request);
})
```

It is possible to use these 2 ways to fetch cached data:

* `caches.match(cache_name)`: Matches a single request and return a promise
* `caches.matchAll(cache_name)`: Matches an array and returns a promise


## Delete cache

```Javascript
caches.keys().then(function(cacheNames) {
    return Promise.all(
    cacheNames.filter(function(cacheName) {
        return cacheName.startsWith('wittr-') && cacheName != static_cache_name;
        }).map(function(cacheName) {
            return caches.delete(cacheName);
        })
    );
})
```

* `caches.delete(cache_name)`: finds cache with given name and return a promise
* `caches.keys()`: returns a promise with an array of cache keys

