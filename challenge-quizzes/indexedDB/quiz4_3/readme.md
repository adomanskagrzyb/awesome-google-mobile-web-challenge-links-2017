## Lesson 4 Quizz 3
```index.js
// *We do not support copy and paste.
// (Blocks of codes are commented out, please review).

// In this task you should replicate pretty much what was done 
// by Jake in the videos. 

//Interesting questions about this task:
//
// So far no questions and answers were found. 
//

import idb from 'idb';

var dbPromise = idb.open('test-db', 1, function(upgradeDb) {
  var keyValStore = upgradeDb.createObjectStore('keyval');
  keyValStore.put('world', 'hello');
});

// read "hello" in "keyval"
dbPromise
  .then(function(db) {
    var tx = db.transaction('keyval');
    var keyValStore = tx.objectStore('keyval');
    return keyValStore.get('hello');
  })
  .then(function(val) {
    console.log('The value of "hello" is:', val);
  });

// set "foo" to be "bar" in "keyval"
dbPromise
  .then(function(db) {
    var tx = db.transaction('keyval', 'readwrite');
    var keyValStore = tx.objectStore('keyval');
    keyValStore.put('bar', 'foo');
    return tx.complete;
  })
  .then(function() {
    console.log('Added foo:bar to keyval');
  });

 // dbPromise
 //  .then(function(db) {
      // TODO: in the keyval store, set
      // "favoriteAnimal" to your favourite animal
      // eg "cat" or "dog"
 //   var tx = db.transaction('keyval', 'readwrite');  // At first you need to create a
                                                       // read and write transaction with
                                                       // access to the keyval store.
 //   var keyValStore = tx.objectStore('keyval');      // Then you create a transaction 
 //   keyValStore.put('wombat', 'favoriteAnimal');     // and get the store and put on it. 
 //   return tx.complete;                              // Once the transaction has
                                                       // finished, you can log (if you want) 
                                                       // a conffirmation message. 
 //  })
 //  .then(function() {
 //    console.log('Added favoriteAnimal: wombat to keyval');
 //  })
  ```
    * Author: [Luiz Carneiro](https://github.com/luuizpaulo)
