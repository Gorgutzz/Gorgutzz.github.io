---
layout: post
title:      "JavaScript Hoisting and Scope"
date:       2019-12-31 03:25:03 +0000
permalink:  javascript_hoisting_and_scope
---


For someone starting out in JavaScript, understanding how the scope of variables and hoisting of declarations work is essential since alot of JavaScript's behavior is dependant on these concepts. The implementation of the newest ECMAScript 6 introduced new features which are interconnected with scope and hoisting as well. 

The concept of hoisting is a feature of JavaScript that moves the declaration of variables and functions to the top which in turn means they can be used before actually declaring them. In essence this means that you can have a variable x equal to a value at the top and then declaring that variable as x at the bottom of your code. Javascript will understand this and it would be as if you declared both variables at the top, however, it will not understand if you initiliaze the variable where you declare it and assign a value at the bottom causing an undefined error. This is why it is common practice to declare and intialize variables at the beginning of every scope.

Example of this:

```
var x = 2;  

elem.innerHTML = x + " " + y; 

var y = 3;
```

Scope in Javascript is the accessibility of variables, with there being local and global scopes. Variables defined inside a function are in the local scope. And they have a different scope for every call of that function. This means that variables having the same name can be used in different functions. This is because those variables are bound to their respective functions, each having different scopes, and are not accessible in other functions. Global scope, on the other hand, is when a variable is defined outside of a function. It becomes a global variable and these variables inside the global scope can be accessed and altered in any other scope. 

Example where x is global and y is local:

```
var x = ''dog";

function someFunction() {
    var y = "cat";
}

```

ES6 introduced two keywords for declaring variables, them being 'let' and 'const'. 'let' allows you to declare variables that are limited to a scope of a block statement, unlike var, which defines a variable globally, or locally to an entire function regardless of block scope. Variables declared by 'let' have their scope in the block for which they are defined, as well as in any contained sub-blocks. 'const' are similar to let variables, except that their values cannot be changed. It is similar to 'let' in that it’s block scoped but unlike 'let' must be initialized with a value. It is not possible to hoist 'let' or 'const' variables as well. Generally, it is recomended to use 'const' for everything unless something can't have a set value, using 'let' for the latter cases. 

Example of let:

```
function someFunc(){
  let x = 5;
  console.log(x);  // output 5
  if(true){
   let x = 20;
   console.log(x); // output 20
  }
  console.log(x);  // output 10
}
```

Example of const and how an error would occur if you tried to re-declare it.

```
function someFunc(){
  const x = 3;
  console.log(x);  //output 3 
	x = 4;   // error
	console.log(x); 
}
```




