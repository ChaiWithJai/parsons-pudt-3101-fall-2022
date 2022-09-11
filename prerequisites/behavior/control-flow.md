### Conditionals

So far the code you've written has been pretty direct in its intent. You can define functions and variables, but so far the functions you've created haven't been able to do that much for you yet. It's time to start writing functions that can do things conditionally by utilizing control flow.

In simple terms - control flow is the order in which instructions are executed within a program. One modifies control flow using control structures, expressions that alter the control flow based on given parameters. The control structures within JavaScript allow the program flow to change within a unit of code or a function.

This reading will be covering one of the two main control structures you will use time and time again - conditional statements. Conditional statements are used to perform different actions based on different conditions.

When you finish this reading, you should be able to:

- Write if, else if, if...else conditional statements.
- Know that conditional statements can have only one if and one else statement.
- Identify that conditional statements can be nested.

### A Quick Word on Syntax

Before we get started we'll quickly go over the terms we'll be using to represent syntax.

`[ ]` are square brackets
`{ }` are curly braces
`( )` are parentheses

### Writing Conditional Statements

Conditional Statements are the second fundamental control structure for writing JavaScript and are pretty straightforward. The simplest conditional statement is the if statement. An if statement has two parts, the test expression (the code that immediately follows the if which goes in parentheses), and the then expression (this code belongs in curly braces ({ }) after the if expression). The then expression will only run when the if expression is truthy.

Here is an example of a simple if statement:

```
// this is the test expression
if (3 === 3) {
  // this is the then expression
  // this code will run if the above statement is true
  console.log("this is a three!");
}
```

The if statement above allows you to specify what should happen if your particular expression evaluates to true. You can chain additional test expressions onto this if statement by using a else if statement.

The syntax for else if is very similar to an if statement:

```
function mathFun() {
  let x = 2 + 3;

  if (x === 3) {
    console.log("we have a 3");
  } else if (x === 4) {
    // this code will run if the above statement is true
    console.log("we have a 4");
  } else if (x === 5) {
    // this code will run if the above statement is true
    console.log("we have a 5");
  }
};

mathFun(); // => "we have a 5"
```

The else if and if statements do not, however, provide the option to specify something else that should happen in the event that all of the above expressions evaluate to be falsey. The if...else statement reads just like English. The JS interpreter will execute the else statement if all the above conditions given are falsey. See below for an example:

```
function mathFun() {
  let x = 19;
  if (x === 3) {
    console.log("we have a 3");
  } else if (x === 4) {
    console.log("we have a 4");
  } else {
    console.log("I will return if everything above me is falsey!");
  }
};

mathFun(); // => "I will return if everything above me is falsey!"
```

You can chain an arbitrary number of else if statements but there can only be one if statement and one optional else statement. The if introduces the control structure and the else acts as a fail safe to catch everything that didn't meet the above conditions.

Only one then expression is ever executed in an if, if...else, or if...else statement. If one of the test expressions is truthy, then the result of its then expression is the result of the entire conditional statement:

```
let x = 3;
if (x === 3) {
  console.log("this will run");
} else {
  console.log("this will not run");
}
```

Additionally, you can nest conditional statements within each other, but it will quickly become difficult to read and is discouraged:

```
function mathFun(x) {
  if (x === "math") {
    if (x === "math" && x[0] === "m") {
      if (x[1] === "a") {
        console.log("this got confusing fast");
      } else {
        console.log("that is not math!");
      }
    } else {
      console.log("that is for sure not math!");
    }
  } else {
    console.log("I will return if everything above me is false!");
  }
};

mathFun("math"); // => "this got confusing fast"
```

### What You Learned

- Conditional statements allow us to control what actions should be taken based on a boolean (truthy or falsey) expression
- In a chain of then expressions (if...else if...else), only one of the then expressions will be executed.
- Conditional statements can have only one if and one else statement.
- Conditional statements can be nested.
