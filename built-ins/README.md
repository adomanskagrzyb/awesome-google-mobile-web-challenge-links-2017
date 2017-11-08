# Lesson 7: built-ins

If some of the built-ins in lesson 7 were new to you, we hope the resource links here will help you:

[<= GO BACK ](../README.md)

## Resource Links

* [Symbols: unique and immutable data type often used to identify object properties.](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Symbol)
* [Symbol Iterator: Read more below (Iterable & Iterator)](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Symbol/iterator)
* [Sets: Object to store unique values](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Set)
* [WeakSet: Object to store unique values](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/WeakSet)
* [Sets vs WeakSets](#set-weak)
* [Map:  store key-value pairs](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Map)
* [WeakMap:  store key-value pairs](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/WeakMap)
* [Map vs WeakMap](#map-weak)
* [Promises: start some work async and let you get back to your regular work](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Promise)
* [Proxies: define custom behavior for fundamental operations](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Proxy)
* [Generators: returned by a generator function, it conforms to both the iterable & iterator protocol](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Generator)



## Iterable & Iterator Protocols

### The Iterable Protocol

> The iterable protocol is used for defining and customizing the iteration behavior of objects.
> What that really means is you now have the flexibility in ES6 to specify a way for iterating through values in an object.
> For some objects, they already come built-in with this behavior. For example, strings and arrays are examples of built-in iterables.

> **_Udacity quote_**


### The Iterator Protocol

> The iterator protocol is used to define a standard way that an object produces a sequence of values.
> What that really means is you now have a process for defining how an object will iterate.
> This is done through implementing the .next() method.

> **_Udacity quote_**

---

## <a name="set-weak">Set vs WeakSet</a>

A WeakSet is just like a normal Set with a few key differences:

- a WeakSet can only contain objects
- a WeakSet is not iterable which means it can’t be looped over
- a WeakSet does not have a .clear() method


### Garbage Collection

> In JavaScript, memory is allocated when new values are created and is "automatically" freed up when those values are no longer needed. This process of freeing up memory after it is no longer needed is what is known as garbage collection.

> WeakSets take advantage of this by exclusively working with objects. If you set an object to null, then you’re essentially deleting the object. And when JavaScript’s garbage collector runs, the memory that object previously occupied will be freed up to be used later in your program.

> **_Udacity quote_**

---

## <a name="map-weak">Map vs WeakMap<a>

A WeakMap is just like a normal Map with a few key differences:

- a WeakMap can only contain objects as keys,
- a WeakMap is not iterable which means it can’t be looped and
- a WeakMap does not have a .clear() method.

### Garbage Collection

> In JavaScript, memory is allocated when new values are created and is "automatically" freed up when those values are no longer needed. This process of freeing up memory after it is no longer needed is what is known as garbage collection.

> WeakMaps take advantage of this by exclusively working with objects as keys. If you set an object to null, then you’re essentially deleting the object. And when JavaScript’s garbage collector runs, the memory that object previously occupied will be freed up to be used later in your program.

> **_Udacity quote_**

