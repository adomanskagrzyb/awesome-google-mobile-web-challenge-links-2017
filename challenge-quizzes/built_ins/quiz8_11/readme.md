## Lesson 8 Quizz 11
```script.js
// *We do not support copy and paste.
// (Blocks of codes are commented out, please review).

//    In this task you should add objects to a created weakset. 

//Interesting questions about this task:
//
// So far no questions and answers were found. 
// But some poeple had problems with the tests because they were 
// not using the '.add()' method three times. 
/*
 * Programming Quiz: Using Sets (3-2)
 *
 * Create the following variables:
 *     - uniqueFlavors and set it to a new WeakSet object
 *     - flavor1 and set it equal to `{ flavor: 'chocolate' }`
 *     - flavor2 and set it equal to an object with property 'flavor' and value of your choice!
 *
 * Use the `.add()` method to add the objects `flavor1` and `flavor2` to `uniqueFlavors`
 * Use the `.add()` method to add the `flavor1` object (again!) to the `uniqueFlavors` set
 */
const uniqueFlavors = new WeakSet();

let flavor1 = { flavor: 'chocolate' };
let flavor2 = { flavor: 'strawberry' };

uniqueFlavors.add(flavor1);
uniqueFlavors.add(flavor2);
uniqueFlavors.add(flavor1);
```
  * Author: [Luiz Carneiro](https://github.com/luuizpaulo)
