## Lesson 7 Quizz 11
```script.js
// *We do not support copy and paste.
// (Blocks of codes are commented out, please review).

//    In this task you should write a function that accepts 
//    an object as default. 

//Interesting questions about this task:
//
// So far no questions and answers were found. 
//
/*
 * Programming Quiz: Using Default Function Parameters (2-2)
 */

// your code goes here
function buildHouse ({floors=1,color='red',walls='brick'}={}) {
    return `Your house has ${floors} floor(s) with ${color} ${walls} walls.`;
}
// tests
console.log(buildHouse()); // Your house has 1 floor(s) with red brick walls.
console.log(buildHouse({})); // Your house has 1 floor(s) with red brick walls.
console.log(buildHouse({floors: 3, color: 'yellow'})); // Your house has 3 floor(s) with yellow brick walls.
```
  * Author: [Luiz Carneiro](https://github.com/luuizpaulo)
