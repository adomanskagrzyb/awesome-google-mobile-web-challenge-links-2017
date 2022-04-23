## Lesson 4 Quizz 13
```index.js
// *We do not support copy and paste.
// (Blocks of codes are commented out, please review).

// Review if you are using the name of variables already defined in 
// the pre-code for this task.

// No discussion was found for this task.

var staticCacheName = 'wittr-static-v8';
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
    // TODO: respond to avatar urls by responding with
    // the return value of serveAvatar(event.request)
//    if (requestUrl.pathname.startsWith('/avatars/')) {
//      // Lets look for urls that start with avatar
//      event.respondWith(serveAvatar(event.request));
//      // for these ask for serve avatar
//      return;
//    }
  }

  event.respondWith(
    caches.match(event.request).then(function(response) {
      return response || fetch(event.request);
    }),
  );
});

function serveAvatar(request) {
  // Avatar urls look like:
  // avatars/sam-2x.jpg
  // But storageUrl has the -2x.jpg bit missing.
  // Use this url to store & match the image in the cache.
  // This means you only store one copy of each avatar.
  var storageUrl = request.url.replace(/-\dx\.jpg$/, '');

  // TODO: return images from the "wittr-content-imgs" cache
  // if they're in there. But afterwards, go to the network
  // to update the entry in the cache.
  //
  // Note that this is slightly different to servePhoto!
//   return caches.open(contentImgsCache).then(function(cache) {
//     return cache.match(storageUrl).then(function(response) {
//       //open the image cache and look for a match
//       let networkFetch = fetch(request).then(function(networkResponse) {
//         // take the avatar from the network 
//         cache.put(storageUrl, networkResponse.clone());
//           //if we get a response, we put a clone in the cache 
//         return networkResponse;
//       });
//       return response || networkFetch;
//         //or take a response from the cache  
//     });
//   });
}

function servePhoto(request) {
  var storageUrl = request.url.replace(/-\d+px\.jpg$/, '');

  return caches.open(contentImgsCache).then(function(cache) {
    return cache.match(storageUrl).then(function(response) {
      if (response) return response;

      return fetch(request).then(function(networkResponse) {
        cache.put(storageUrl, networkResponse.clone());
        return networkResponse;
      });
    });
  });
}

self.addEventListener('message', function(event) {
  if (event.data.action === 'skipWaiting') {
    self.skipWaiting();
  }
});
```
  * Author: [Luiz Carneiro](https://github.com/luuizpaulo)
