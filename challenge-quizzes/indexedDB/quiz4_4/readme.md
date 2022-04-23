## Lesson 4 Quizz 4
```index.js
// *We do not support copy and paste.
// (Blocks of codes are commented out, please review).

// In this task you should replicate pretty much what was done 
// by Jake in the previous video. 

//Interesting questions about this task:
//
// Question - I get it working and it passes the test, but no data actually 
//            displays in the db itself (in Applications tab, IndexedDB/test-db/people/age. 
//            This is completely empty. Anyone knows what could be going on? I'm getting no errors.
//
// Answer -  Just deleted the database, refreshed and there it was.
//           (see also - https://discussions.udacity.com/t/chrome-canary-bug-regarding-indexeddb-objectstore-indexes/440788)
//

import idb from 'idb';

// var dbPromise = idb.open('test-db', 4, function(upgradeDb) {  // you will need to change the DB version 
  switch (upgradeDb.oldVersion) {
    case 0:
      var keyValStore = upgradeDb.createObjectStore('keyval');
      keyValStore.put('world', 'hello');
    case 1:
      upgradeDb.createObjectStore('people', {keyPath: 'name'});
    case 2:
      var peopleStore = upgradeDb.transaction.objectStore('people');
      peopleStore.createIndex('animal', 'favoriteAnimal');
  //  case 3:                                                          // Then create a new switch with a new index 
  //    var peopleStore = upgradeDb.transaction.objectStore('people'); // called age that sorts by 'age' property. 
  //    peopleStore.createIndex('age', 'age');                         // (has to be like that if you want a confirmation in localhost:8889 that
                                                                       // everything is right). See below. 
  }
  // TODO: create an index on 'people' named 'age', ordered by 'age'
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

dbPromise
  .then(function(db) {
    var tx = db.transaction('keyval', 'readwrite');
    var keyValStore = tx.objectStore('keyval');
    keyValStore.put('cat', 'favoriteAnimal');
    return tx.complete;
  })
  .then(function() {
    console.log('Added favoriteAnimal:cat to keyval');
  });

// add people to "people"
dbPromise
  .then(function(db) {
    var tx = db.transaction('people', 'readwrite');
    var peopleStore = tx.objectStore('people');

    peopleStore.put({
      name: 'Sam Munoz',
      age: 25,
      favoriteAnimal: 'dog',
    });

    peopleStore.put({
      name: 'Susan Keller',
      age: 34,
      favoriteAnimal: 'cat',
    });

    peopleStore.put({
      name: 'Lillie Wolfe',
      age: 28,
      favoriteAnimal: 'dog',
    });

    peopleStore.put({
      name: 'Marc Stone',
      age: 39,
      favoriteAnimal: 'cat',
    });

    return tx.complete;
  })
  .then(function() {
    console.log('People added');
  });

// list all cat people
dbPromise
  .then(function(db) {
    var tx = db.transaction('people');
    var peopleStore = tx.objectStore('people');
    var animalIndex = peopleStore.index('animal');

    return animalIndex.getAll('cat');
  })
  .then(function(people) {
    console.log('Cat people:', people);
  });

// TODO: console.log all people ordered by age
 // dbPromise
 // .then(function(db) {                             
 //   var tx = db.transaction('people');               // create a transaction 
 //   var peopleStore = tx.objectStore('people');      // get the object store 
 //   var ageIndex = peopleStore.index('age');         // get the index 
 //
 //   return ageIndex.getAll();                        //then you get all the indexes 
 // })
 // .then(function(people) {
 //   console.log('Years old:', people);              // and finally log them.
 // });
```
  * Author: [Luiz Carneiro](https://github.com/luuizpaulo)
