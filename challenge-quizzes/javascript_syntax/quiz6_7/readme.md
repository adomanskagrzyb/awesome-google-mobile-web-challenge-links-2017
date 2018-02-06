## Lesson 6 Quizz 7
```script.js
// *We do not support copy and paste.
// (Blocks of codes are commented out, please review).

//    In this task you should use Destructuring to print   
//  some itens of an array.

//Interesting questions about this task:
//
// So far no questions and answers were found. 
//
/*
 * Programming Quiz: Destructuring Arrays (1-3)
 *
 * Use destructuring to initialize the variables `one`, `two`, and `three`
 * with the colors from the `things` array.
 */

const things = ['red', 'basketball', 'paperclip', 'green', 'computer', 'earth', 'udacity', 'blue', 'dogs'];

const [one] = things;
const [ , , ,two] = things;
const [,,,,,,,three] = things;

const colors = `List of Colors
1. ${one}
2. ${two}
3. ${three}`;

console.log(colors);
```
  * Author: [Luiz Carneiro](https://github.com/luuizpaulo)
