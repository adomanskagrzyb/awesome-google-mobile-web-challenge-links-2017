## Lesson 7 Quizz 20
```script.js
// *We do not support copy and paste.
// (Blocks of codes are commented out, please review).

//    In this task you should create a subclass that extends the 
//    Vehicle class and change the default values. 

//Interesting questions about this task:
//  Many students (me included) had problems in defining the 
//  default values of the variables in the new extended function. 
//  The most reported error was:
//      Cannot read property ‘name’ of undefined error.
//
//   So pay attention in this fragment: 
//         class Bicycle extends Vehicle {
//           constructor(color = 'blue', wheels = 2, horn = 'hank hank') {
//             super(color, wheels, horn);
//           }
//         }
//
/*
 * Programming Quiz: Building Classes and Subclasses (2-3)
 */

class Vehicle {
	constructor(color = 'blue', wheels = 4, horn = 'beep beep') {
		this.color = color;
		this.wheels = wheels;
		this.horn = horn;
	}

	honkHorn() {
		console.log(this.horn);
	}
}

// your code goes here
class Bicycle extends Vehicle {
 constructor(color='blue',wheels=2,horn='honk honk'){
     super(color,wheels,horn);
 }

  honkHorn(){
    super.honkHorn();
  }
}

// tests
const myVehicle = new Vehicle();
myVehicle.honkHorn(); // beep beep
const myBike = new Bicycle();
console.log(myBike.color);
myBike.honkHorn(); // honk honk
```
  * Author: [Luiz Carneiro](https://github.com/luuizpaulo)
