## Lesson 4 Quizz 10
```IndexController.js
// *We do not support copy and paste.
// (Blocks of codes are commented out, please review).

// Review if you are using the name of variables already defined in 
// the pre-code for this task.

var staticCacheName = 'wittr-static-v7';
var contentImgsCache = 'wittr-content-imgs';
var allCaches = [staticCacheName, contentImgsCache];

self.addEventListener('install', function(event) {
  event.waitUntil(
    caches.open(staticCacheName).then(function(cache) {
      return cache.addAll([
        '/skeleton',
        'js/main.js',
        'css/main.css',
        'imgs/icon.png',
        'https://fonts.gstatic.com/s/roboto/v15/2UX7WLTfW3W8TclTUvlFyQ.woff',
        'https://fonts.gstatic.com/s/roboto/v15/d-6IYplOFocCacKzxwXSOD8E0i7KZn-EPnyo3HZu7kw.woff',
      ]);
    }),
  );
});

self.addEventListener('activate', function(event) {
  event.waitUntil(
    caches.keys().then(function(cacheNames) {
      return Promise.all(
        cacheNames
          .filter(function(cacheName) {
            return (
              cacheName.startsWith('wittr-') && !allCaches.includes(cacheName)
            );
          })
          .map(function(cacheName) {
            return caches.delete(cacheName);
          }),
      );
    }),
  );
});

self.addEventListener('fetch', function(event) {
  var requestUrl = new URL(event.request.url);

  if (requestUrl.origin === location.origin) {
    if (requestUrl.pathname === '/') {
      event.respondWith(caches.match('/skeleton'));
      return;
    }
    if (requestUrl.pathname.startsWith('/photos/')) {
      event.respondWith(servePhoto(event.request));
      return;
    }
  }

  event.respondWith(
    caches.match(event.request).then(function(response) {
      return response || fetch(event.request);
    }),
  );
});

function servePhoto(request) {
  // Photo urls look like:
  // /photos/9-8028-7527734776-e1d2bda28e-800px.jpg
  // But storageUrl has the -800px.jpg bit missing.
  // Use this url to store & match the image in the cache.
  // This means you only store one copy of each photo.
  var storageUrl = request.url.replace(/-\d+px\.jpg$/, '');

  // TODO: return images from the "wittr-content-imgs" cache
  // if they're in there. Otherwise, fetch the images from
  // the network, put them into the cache, and send it back
  // to the browser.
  //
  // HINT: cache.put supports a plain url as the first parameter
//  return caches.open(contentImgsCache).then(function(cache) {
           // First open the cache for the images, once you got it ...
//    return cache.match(storageUrl).then(function(response) {
          //  look for a match for an URL 
//      if (response) return response;
          //  if theres one simply return it 
//      return fetch(request).then(function(networkResponse) {
          //  Otherwise you take it from the internet and store in the cache
//        cache.put(storageUrl, networkResponse.clone());
//        return networkResponse;
//      });
//    });
//  });
}

self.addEventListener('message', function(event) {
  if (event.data.action === 'skipWaiting') {
    self.skipWaiting();
  }
});
```
  * Author: [Luiz Carneiro](https://github.com/luuizpaulo)
