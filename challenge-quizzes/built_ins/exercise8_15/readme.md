## Lesson 8 Exercise 15
```script.js
// *We do not support copy and paste.
// (Blocks of codes are commented out, please review).

//    In this exercise you should fix the printing of your map 
//    in a way that it prints the values and pairs separately, 
//    and not as a array.

//Interesting questions about this task:
//
// I am a little bit confused - why would I need to do this? 
// I am not seeing why I would need array destructuring here? 
//  Can't I simply do this: 
//  for (const member of members) {
//  console.log(member);
//  }
//
// Answer: it's in order to discover a way to implement array 
//     destructuring inside the condition of the for of loop
/*
 * Using array destructuring, fix the following code to print the keys and values of the `members` Map to the console.
 */

const members = new Map();

members.set('Evelyn', 75.68);
members.set('Liam', 20.16);
members.set('Sophia', 0);
members.set('Marcus', 10.25);

for (const member of members) {
    let [key,value] = member; 
    console.log(key, value);
}
```
  * Author: [Luiz Carneiro](https://github.com/luuizpaulo)
