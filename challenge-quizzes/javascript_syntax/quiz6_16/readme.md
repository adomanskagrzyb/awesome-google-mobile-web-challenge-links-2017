## Lesson 6 Quizz 16
```script.js
// *We do not support copy and paste.
// (Blocks of codes are commented out, please review).

//    In this task you should calculate the mean value of 
//    an array of numbers using the ...Rest parameter and 
//    a for...of loop

//Interesting questions about this task:
//
// So far no questions and answers were found. 
//
/*
 * Programming Quiz: Using the Rest Parameter (1-5)
 */

// your code goes here

function average(...nums) {
    let total=0;
    for(const num of nums){
      total+=num;  
    }
    if (total===0){return total};
    return total/nums.length;
}

console.log(average(2, 6));
console.log(average(2, 3, 3, 5, 7, 10));
console.log(average(7, 1432, 12, 13, 100));
console.log(average());
```
  * Author: [Luiz Carneiro](https://github.com/luuizpaulo)
