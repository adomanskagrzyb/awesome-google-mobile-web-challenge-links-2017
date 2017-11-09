# Lesson 4: IndexedDB & Caching

If some of the topics in lesson 4 were new to you, we hope the resource links here will help you:

[<= GO BACK ](../README.md)

> IndexedDB is an API to store data (structured) uncluding files and [blobs](https://en.wikipedia.org/wiki/Binary_large_object).
> The API allows you to create indexes to perform efficient searches of the stored data.
> Web Storage allows to store small amounts of data but is useless for larger amounts of data.
> IndexedDB provides a solution to this problem.

> *_Rewritten for clarity from MDN_*

## Resource Links

* [IDB API](https://developer.mozilla.org/en-US/docs/Web/API/IndexedDB_API)
* [IDBObject Store](https://developer.mozilla.org/en-US/docs/Web/API/IDBObjectStore)
* [IDB: Put (save object)](https://developer.mozilla.org/en-US/docs/Web/API/IDBObjectStore/put)


## Video Links

* [Google Developer Working with IndexedDB](https://www.youtube.com/watch?v=vCumk1sXHcY)

## Overview:

Throughout the course, we make use of the [idb package](https://www.npmjs.com/package/idb) to use promises rather than callbacks. In order to use IndexedDB (idb package) you have to import it first:

```
import idb from 'idb';
```

When you use the ```idb.open()``` method it returns a promise that resolves to a DB which gives you access to the database. Once you create the database you can create an objectStore to store key/value pairs.

You can also create an index just by referencing your objectStore and calling the ```createIndex(indexName, keyPath)``` method.

```
var dbPromise = idb.open('database_name', 1, function(upgradeDb) {
  var store = upgradeDb.createObjectStore('store_name', {
    keyPath: 'id'
  });
  store.createIndex('indexName', 'keypath');
});
```
---

### Read & Write to IndexedDB

Every time you want to access or write to the database you created, you have to open a transaction using ```transaction('store_name')``` or ```transaction('store_name', 'readwrite')```  if you want to write to your database. After that you just reference your objectStore and use ```put({})``` to store something:

```
dbPromise.then(function(db) {
  var tx = db.transaction('store_name', 'readwrite');
  var yourStore = tx.objectStore('store_name');

  yourStore.put({
    name: 'John Smith',
    age: 25,
    favoriteAnimal: 'dog'
  });

  return tx.complete;
}).then(function() {
  console.log('I just added something to my Database');
});
```

To get items you do something similar:

```
dbPromise.then(function(db) {
  var tx = db.transaction('store_name');
  var yourStore = tx.objectStore('store_name');

  return yourStore.getAll();
}).then(function(yourObjects) {
  console.log('I got these objects in my store', yourObjects);
});
```

For more methods and a full review of the IndexedDB API, please read the [IndexedDB API page](https://developer.mozilla.org/en-US/docs/Web/API/IndexedDB_API)
