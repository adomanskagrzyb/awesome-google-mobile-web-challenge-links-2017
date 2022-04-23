## Lesson 4 Quizz 12
```IndexController.js
// *We do not support copy and paste.
// (Blocks of codes are commented out, please review).

// Review if you are using the name of variables already defined in 
// the pre-code for this task.

// Question - So i’m on the quiz 4.12 and i’m wondering how many of 
//            the photos should be deleted from the cache?
//
// Answer -   Not all the messages have a photo attached, but if they do, 
//            they will have a `photo` property. (You can check it out by 
//            logging out all the messages in the console and finding a 
//            one that contains a photo
import PostsView from './views/Posts';
import ToastsView from './views/Toasts';
import idb from 'idb';

function openDatabase() {
  // If the browser doesn't support service worker,
  // we don't care about having a database
  if (!navigator.serviceWorker) {
    return Promise.resolve();
  }

  return idb.open('wittr', 1, function(upgradeDb) {
    var store = upgradeDb.createObjectStore('wittrs', {
      keyPath: 'id',
    });
    store.createIndex('by-date', 'time');
  });
}

export default function IndexController(container) {
  this._container = container;
  this._postsView = new PostsView(this._container);
  this._toastsView = new ToastsView(this._container);
  this._lostConnectionToast = null;
  this._dbPromise = openDatabase();
  this._registerServiceWorker();
  this._cleanImageCache();

  var indexController = this;

  setInterval(function() {
    indexController._cleanImageCache();
  }, 1000 * 60 * 5);

  this._showCachedMessages().then(function() {
    indexController._openSocket();
  });
}

IndexController.prototype._registerServiceWorker = function() {
  if (!navigator.serviceWorker) return;

  var indexController = this;

  navigator.serviceWorker.register('/sw.js').then(function(reg) {
    if (!navigator.serviceWorker.controller) {
      return;
    }

    if (reg.waiting) {
      indexController._updateReady(reg.waiting);
      return;
    }

    if (reg.installing) {
      indexController._trackInstalling(reg.installing);
      return;
    }

    reg.addEventListener('updatefound', function() {
      indexController._trackInstalling(reg.installing);
    });
  });

  // Ensure refresh is only called once.
  // This works around a bug in "force update on reload".
  var refreshing;
  navigator.serviceWorker.addEventListener('controllerchange', function() {
    if (refreshing) return;
    window.location.reload();
    refreshing = true;
  });
};

IndexController.prototype._showCachedMessages = function() {
  var indexController = this;

  return this._dbPromise.then(function(db) {
    // if we're already showing posts, eg shift-refresh
    // or the very first load, there's no point fetching
    // posts from IDB
    if (!db || indexController._postsView.showingPosts()) return;

    var index = db
      .transaction('wittrs')
      .objectStore('wittrs')
      .index('by-date');

    return index.getAll().then(function(messages) {
      indexController._postsView.addPosts(messages.reverse());
    });
  });
};

IndexController.prototype._trackInstalling = function(worker) {
  var indexController = this;
  worker.addEventListener('statechange', function() {
    if (worker.state == 'installed') {
      indexController._updateReady(worker);
    }
  });
};

IndexController.prototype._updateReady = function(worker) {
  var toast = this._toastsView.show('New version available', {
    buttons: ['refresh', 'dismiss'],
  });

  toast.answer.then(function(answer) {
    if (answer != 'refresh') return;
    worker.postMessage({action: 'skipWaiting'});
  });
};

// open a connection to the server for live updates
IndexController.prototype._openSocket = function() {
  var indexController = this;
  var latestPostDate = this._postsView.getLatestPostDate();

  // create a url pointing to /updates with the ws protocol
  var socketUrl = new URL('/updates', window.location);
  socketUrl.protocol = 'ws';

  if (latestPostDate) {
    socketUrl.search = 'since=' + latestPostDate.valueOf();
  }

  // this is a little hack for the settings page's tests,
  // it isn't needed for Wittr
  socketUrl.search += '&' + location.search.slice(1);

  var ws = new WebSocket(socketUrl.href);

  // add listeners
  ws.addEventListener('open', function() {
    if (indexController._lostConnectionToast) {
      indexController._lostConnectionToast.hide();
    }
  });

  ws.addEventListener('message', function(event) {
    requestAnimationFrame(function() {
      indexController._onSocketMessage(event.data);
    });
  });

  ws.addEventListener('close', function() {
    // tell the user
    if (!indexController._lostConnectionToast) {
      indexController._lostConnectionToast = indexController._toastsView.show(
        'Unable to connect. Retrying…',
      );
    }

    // try and reconnect in 5 seconds
    setTimeout(function() {
      indexController._openSocket();
    }, 5000);
  });
};

IndexController.prototype._cleanImageCache = function() {
  return this._dbPromise.then(function(db) {
    if (!db) return;

    // TODO: open the 'wittr' object store, get all the messages,
    // gather all the photo urls.
    //
    // Open the 'wittr-content-imgs' cache, and delete any entry
    // that you no longer need.
//     var imagesNeeded = [];
      //     First we create an array with the image we want to keep
//     var tx = db.transaction('wittrs');
      //     Then a transaction to look in the wittrs object store 
//     return tx
//       .objectStore('wittrs')
//       .getAll()
//       .then(function(messages) {
      //       get the object store and all the messages stored
//         messages.forEach(function(message) {
//           if (message.photo) {
      //           Check if the message has a photo attached to it
//             imagesNeeded.push(message.photo);
      //             if it has a photo, add to the images array 
//           }
//         });
//         return caches.open('wittr-content-imgs');
//       })
//       .then(function(cache) {
//         return cache.keys().then(function(requests) {
      //         Open the cache and take all the requests stored in it
//           requests.forEach(function(request) {
//             var url = new URL(request.url);
      //             for each request we pass the URL 
//             if (!imagesNeeded.includes(url.pathname)) {
      //             if the path of the image is not in the array, just delete it
//               cache.delete(request);
//             }
//           });
//         });
//       });
//   });
// };

// called when the web socket sends message data
IndexController.prototype._onSocketMessage = function(data) {
  var messages = JSON.parse(data);

  this._dbPromise.then(function(db) {
    if (!db) return;

    var tx = db.transaction('wittrs', 'readwrite');
    var store = tx.objectStore('wittrs');
    messages.forEach(function(message) {
      store.put(message);
    });

    // limit store to 30 items
    store
      .index('by-date')
      .openCursor(null, 'prev')
      .then(function(cursor) {
        return cursor.advance(30);
      })
      .then(function deleteRest(cursor) {
        if (!cursor) return;
        cursor.delete();
        return cursor.continue().then(deleteRest);
      });
  });

  this._postsView.addPosts(messages);
};
```
  * Author: [Luiz Carneiro](https://github.com/luuizpaulo)
