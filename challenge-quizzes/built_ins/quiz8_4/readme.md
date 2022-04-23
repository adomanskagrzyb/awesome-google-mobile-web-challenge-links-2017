## Lesson 8 exercise 4
```script.js
// *We do not support copy and paste.
// (Blocks of codes are commented out, please review).

//    In this exercise you should basically add an interator to plain object.  
//    This iterator should print the name of the properties, its values and 
//    if the iterator is done. 

//Interesting questions about this task:
//
// This task made a enormous jump in comparison with what was previously 
// tought, so many students had problems (me included).
// 
// 8.4 => Hi, I don't understand either. It's like they went from level 10 to 100 
//        in /the same lesson. And it is the first quiz. I have been reading 
//        the forum and the additional material but I'm like how the hell 
//        am I suppose to get here from current + prev lessons. 
// 
//  answer: It’s quite a steep jump to this but you can make it. Might I 
//         suggest you read on MDN docs about Symbol.iterator: 
//         https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Symbol/iterator 
//         
//   answer: I wrote article for the exercise, hope it helps 
//   https://medium.com/@IchiLaMuchy/james-let-me-access-your-keys-aabec78f7f40
//      (these two links helped me a lot) 
 /*
  * Programming Quiz: Make An Iterable Object
  *
  * Turn the `james` object into an iterable object.
  *
  * Each call to iterator.next should log out an object with the following info:
  *   - key: the key from the `james` object
  *   - value: the value of the key from the `james` object
  *   - done: true or false if there are more keys/values
  *
  * For clarification, look at the example console.logs at the bottom of the code.
  *
  * Hints:
  *   - Use `Object.keys()` to store the object's properties in an array.
  *   - Each call to `iterator.next()` should use this array to know which property to return.
  *   - You can access the original object using `this`.
  *   - To access the values of the original object, use `this` and the key from the `Object.keys()` array.
 */
  
  const james = {
      name: 'James',
      height: `5'10"`,
      weight: 185 ,
      [Symbol.iterator]: function(){
          const obj = this;
          const prop = Object.keys(obj);
          let index = -1;
          return{
              next: 
                function(){
                  index++;
                  return{
                   key: prop[index],
                   value: obj[prop[index]],
                   done: (index+1 === prop.length)
                }
              }
          }
      }
  };
   
   const iterator = james[Symbol.iterator]();
  
   console.log(iterator.next()); // 'James'
   console.log(iterator.next()); // `5'10`
   console.log(iterator.next()); // 185
```
  * Author: [Luiz Carneiro](https://github.com/luuizpaulo)
