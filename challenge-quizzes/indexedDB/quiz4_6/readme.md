## Lesson 4 Quizz 6
```IndexController.js
// *We do not support copy and paste.
// (Blocks of codes are commented out, please review).

// This task requires all the commands seen in the previous videos. 

//Interesting questions about this task:
//
// Question - I am on 4.6 and I it looks like the openDatabase() is 
//              never called (I don't see the console.log or the db at all). Any help?  
//
// Answer -   Some things, you can do to check if your script is the same as on the server:
//            1. Press Shift+F5 
//            2. Call it directly and check if it is the same.
//            3. Check if the build process work or restart it with `npm run serve`
//            4. Have "Disable cache" activated on the network tab in the developer console.
//            
//           In most cases one of these could help to solve the problem. 
//           I for my own forget sometimes to save. So the build process did 
//           not start and therefore the server did not have the actual copy of 
//           my current work status.
//
// Warning -  I had been struggling with lesson 4-6, then realized Chrome canary 
//            Version 64.0.3269.0 (Official Build) canary (64-bit) was not behaving 
//            as expected. It was throwing errors that doesn't make sense from my code. 
//            Also it didn't update on reload. 
//            Just switched to google Chrome Version 62.0.3202.94 (Official Build) 
//            (64-bit). It works fine on the version
//

import PostsView from './views/Posts';
import ToastsView from './views/Toasts';
import idb from 'idb';

function openDatabase() {
  // If the browser doesn't support service worker,
  // we don't care about having a database
  if (!navigator.serviceWorker) {
    return Promise.resolve();
  }

      // TODO: return a promise for a database called 'wittr'
      // that contains one objectStore: 'wittrs'
      // that uses 'id' as its key
      // and has an index called 'by-date', which is sorted
      // by the 'time' property
//  return idb.open('wittr', 1, function(upgradeDb) {
// Open the database called Wittr with version number 1 for ex. 
//    let store = upgradeDb.createObjectStore('wittrs', {
// Create an object store with the name wittrs (has to be like that 
//     if you want a confirmation from localhost:8889).
//      keyPath: 'id',
// with a key you want as the primary key 
//    });
//    store.createIndex('by-date', 'time');
// you also create an index for the time property of the stored objects 
//  });
}

export default function IndexController(container) {
  this._container = container;
  this._postsView = new PostsView(this._container);
  this._toastsView = new ToastsView(this._container);
  this._lostConnectionToast = null;
  this._openSocket();
  this._dbPromise = openDatabase();
  this._registerServiceWorker();
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

// called when the web socket sends message data
IndexController.prototype._onSocketMessage = function(data) {
  var messages = JSON.parse(data);

  this._dbPromise.then(function(db) {
    if (!db) return;

    // TODO: put each message into the 'wittrs'
    // object store.

// Now you need to get elements into the store
//    let tx = db.transaction('wittrs', 'readwrite');
// Create a read and write transaction  
//    let store = tx.objectStore('wittrs');
// Say what you want to store
//    messages.forEach((message) => {
// And put each of these messages into the store object  
//      store.put(message);
//    });
  });

  this._postsView.addPosts(messages);
};
```
  * Author: [Luiz Carneiro](https://github.com/luuizpaulo)
