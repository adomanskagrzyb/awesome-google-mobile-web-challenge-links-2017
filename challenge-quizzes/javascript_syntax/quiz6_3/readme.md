## Lesson 6 Quizz 3
```script.js
// *We do not support copy and paste.
// (Blocks of codes are commented out, please review).

//    In this task you should evaluate which variables do not change 
// along the scripts. Those should be declared with const. The 
// one which changes along the script shall be decalred with let.

//Interesting questions about this task:
//
// So far no questions and answers were found. 
//
/*
 * Programming Quiz: Using Let and Const (1-1)
 */

const CHARACTER_LIMIT = 255;
const posts = [
	"#DeepLearning transforms everything from self-driving cars to language translations. AND it's our new Nanodegree!",
	"Within your first week of the VR Developer Nanodegree Program, you'll make your own virtual reality app",
	"I just finished @udacity's Front-End Web Developer Nanodegree. Check it out!"
];

// prints posts to the console
function displayPosts() {
	for (let i = 0; i < posts.length; i++) {
		console.log(posts[i].slice(0, CHARACTER_LIMIT));
	}
}

displayPosts();
```
  * Author: [Luiz Carneiro](https://github.com/luuizpaulo)
