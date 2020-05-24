**# What’s the difference between Object Oriented Programming (OOP) and Functional Programming (FP)?
**
**
**
**
**
JavaScript is a multi-paradigm language, meaning that it supports multiple different programming styles, including event-driven, functional and object-oriented.
There are many different programming paradigms, but in contemporary computing two of the most popular styles are Functional Programming (FP) and Object-Oriented Programming (OOP) — and JavaScript can do both.
**## 

**
**## Object-Oriented Programming
**
OOP is based around the concept of “objects”. These are data structures that contain data fields — known in JavaScript as “properties” — and procedures — known as “methods”.
Some of JavaScript’s in-built objects include Math (used for methods such as random , max and sin ), JSON (used for parsing JSON data), and primitive data types like String , Array , Number and Boolean .
Whenever you rely on in-built methods, prototypes or classes, you are essentially using Object-Oriented Programming.
**## 

**
**## Functional Programming
**
FP is based around the concept of “pure functions”, which avoid shared state, mutable data and side-effects. This might seem like a lot of jargon, but chances are you’ve created written many pure functions in your code.
Given the same inputs, a pure function always returns the same output. It does not have side effects: these are anything, such as logging to the console or modifying an external variable, beyond returning the result.
As for shared state, here’s a quick example of it state can change the output of a function, even if the input is the same. Let’s set out a scenario with two functions: one to add a number by 5, and one to multiply it by 5.

const num = {
  val: 1
}; 
const add5 = () => num.val += 5; 
const multiply5 = () => num.val *= 5;

If we call add5 first and multiply5 second, the overall result is 30 . But if we call the functions the other way around and log the result, we get something different: 10 .
This goes against the principle of functional programming, as the result of the functions differs depending on the context. We can re-write the above code so that the results are predictable:

const num = {
  val: 1
};
const add5 = () => Object.assign({}, num, {val: num.val + 5}); 
const multiply5 = () => Object.assign({}, num, {val: num.val * 5});

Now, the value of num.val remains 1 , and regardless of the context add5(num) and multiply5(num) will always produce the same result.

