## Functions

We hope you are ready - because you are on the brink of one of the most fun parts of writing JavaScript: writing functions. A function is a procedure of code that will run when called. When we write a function, we can use it as many times as we please. We only write a function once. Writing a function is known as a function declaration or function definition. Functions are the fundamental building blocks of JavaScript and mastering them is a big step on the road to JavaScript mastery!

When you finish this reading, you should be able to:

- Describe what a function in JavaScript is
- Demonstrate how to invoke a function
- Write a function using function declaration
- Use the return keyword to return a value from a function

### Writing functions

A function is a set of code that will run when called. Functions really start to make sense when put in the perspective of solving problems. For example, imagine we want to use code to find the average of two given numbers. This means we'll write code that takes two numbers, adds them together, and then divides their sum by two:

```
(5 + 5) / 2 // Returns 5

(15 + 3) / 2 // Returns 9

(7 + 2) / 2 // Returns 4.5
```

Writing out the same code again and again is tedious. Instead, you can define or declare a re-usable function.

### Function declaration

A function declaration is when a function is defined and saved so that we can use it or re-use it later. When we use a declared function, we are calling the function. Calling a function is also known as invoking a function. A function call is also known as a function invocation. The example below declares a function named average and invokes it later on.

A function definition consists of the function keyword, followed by three things:

1. The name of the function.
2. A list of parameters to the function, enclosed in parentheses (( )).
3. The code to be run when this function is run, enclosed in curly braces ({ }).

Let's think back to the code we wrote to find the average of two numbers. Instead of manually writing out the math whenever we want to find the average of a new pair of numbers, we could write a function to handle the logic of taking two numbers, adding them together, and then dividing their sum by two.

For example, we would write a function that:

- Has a function name of average
- Takes in two parameters (number1 and number2)
- Has code to be run that handles the logic of averaging two numbers

```
function average(number1, number2) {
return (number1 + number2) / 2;
}
```

First thing to notice for the above average function is that we didn't use any real numbers. You always want to write functions to accept as wide a range of data as possible. Utilizing the incoming parameters to a function is key to keeping functions flexible and re-usable.

In the case of the average function, we want to use it to calculate the average of any two numbers. The parameters for the average function are number1 and number2. In other words, the average function expects to be given two numbers, that will be referenced by the variable names, number1 and number2, in the code to be run. We'll be talking a lot more about parameters later. For now, know that when you define a function with parameters you are declaring those parameters as usable variables within that function.

The beauty of a function is that if we define it in a clever way, it will be highly re-usable with a lot of different data! For example, our average function will work with any two numbers.

### Invoking or calling a function

Now that we've written a function how do we actually use it? Once defined a function can be invoked or called as many times as we please.

When we invoke or call a function, we specify the data for a function to use. When we specify what data to use for a function call, we refer to that process as passing arguments to the function.

```
// Function definition
function average(number1, number2) {
    return (number1 + number2) / 2;
}

// This function call passes the arguments 10 and 16.
average(10, 16) // Returns 13
```

When we call the function average(10, 16), we run the code inside the definition for average. That is, we plug in the parameters with real numbers (number1 becomes 10 and number2 becomes 16). Think of number1 and number2 as variables that contain the values we pass in when we called the function. Then we proceed by running the code inside the function. The parameter names number1 and number2 are used throughout the body of the function and behave like variables.

### Order of code

Let's step away from average for a bit to see how a simple function call works. Say we run a JavaScript file with code that looks like this:

```
console.log("First!");
console.log("Second!");
```

Running this code will return exactly as we expect. We will see First! printed out, followed by Second!. In other words, JavaScript will evaluate your code left-to-right and top-to-bottom. Very intuitive! It's exactly how you are reading these notes right now.

However, when JavaScript sees a function definition, JavaScript will not evaluate the code inside the definition. It will execute the code inside the definition only when the function is invoked. For example, a file with the code below would only print First! followed by Fourth!:

```
console.log("First!");

function callMe() {
    console.log("Second!");
    console.log("Third!");
}

console.log("Fourth!");
```

To actually get the code within callMe to evaluate, we must call the callMe function by invoking it with parentheses (callMe()). The code below will now print based on the order of the console.log statements and the function invocation:

```
function callMe() {
    console.log("Second!");
    console.log("Third!");
}

console.log("First!");
callMe();
console.log("Fourth!");

// Running this file will print these statements in this order:
// "First!"
// "Second!"
// "Third!"
// "Fourth!"
```

Let's say JavaScript is running the file above. Here are the steps it would take, starting from the top of the file:

1. JS sees a definition for the callMe function. It will remember this definition in case we call the function later. It will not evaluate the code inside the function yet.
2. JS prints out "First!".
3. JS sees that we are calling callMe(). At this point it will look at definition of the callMe function and run the code inside. As if we jumped inside the function definition, the console.log statements for printing "Second!" and "Third!" will execute.
4. JS sees there is no more code to run inside of the callMe function, so it jumps back to where we originally invoked callMe().
5. JS will continue evaluating in order and print "Fourth!".

Alternatively, you could invoke the callMe function after the console.log statements:

```
function callMe() {
    console.log("Second!");
    console.log("Third!");
}

console.log("First!");
console.log("Fourth!");
callMe();

// Running this file will print these statements in this order:
// "First!"
// "Fourth!"
// "Second!"
// "Third!"
```

Here are the steps running this file would take, starting from the top of the file:

1. JS sees a definition for the callMe function.
2. JS prints out "First!".
3. JS prints out "Fourth!".
4. JS sees that we are invoking the callMe function (callMe()). It will run the code inside the callMe function - this means it will execute the console.log statements to print "Second!" and "Third!".

### Returning a value

Now that we know how functions are declared and invoked let's talk about the inside of the function. We'll start with a statement: Every function in JavaScript returns undefined unless otherwise specified.

Now what does that mean? We'll start with a simple example:

```
function sayNumber(number) {
    console.log(number);
}

sayNumber(1); // Prints 1 and returns undefined
```

So what happened there? Let's do a quick step by step:

1. We declared the sayNumber function
2. sayNumber was called handing in the argument of 1
3. The number parameter is printed to the console
4. Then the function ends without encountering a return statement. Since nothing was specifically returned then the function returned the default value for a function which is undefined.

Now let's change our above example to use the keyword return to return a value:

```
function sayNumber(number) {
    console.log(number);
    return true;
}

sayNumber(1); // Prints 1 and returns true
```

Let's go back to our previous average function and talk about the return we used there:

```
function average(number1, number2) {
    return (number1 + number2) / 2;
}

const result = average(10, 16); // The function call returns 13,
// so the result variable is set to 13.

// We can check what a function returns by printing its result:
console.log(result); // Prints 13

// Alternatively, we can print the function invocation:
console.log(average(10, 16)); // Prints 13
```

When we call a function, we jump to the function definition and run the code inside. When we hit a return statement, we immediately exit the function, jump back to where we called the function, and evaluate the function call to the value it returned.

Every function call evaluates to its return value! In other words, the expression average(10, 16) evaluates to 13 just like how the expression 1 + 1 evaluates to 2.

Another important rule of the return statement is that it stops function execution immediately. This means that any code after a return will not be executed!

```
function average(number1, number2) {
    let sum = number1 + number2;
    return sum;
    // Anything under the `return sum` statement will NOT be executed.
    console.log("this will not run");
    return false;
}
```

`average(2, 7); // Returns 9`

So the three things to remember about return statements is:

1. Every function call evaluates to its return value.
2. Every function in JavaScript returns undefined unless a return is specified
3. Once a return statement is encountered, the function will immediately stop and return the value, ignoring any code below the return statement.

### The importance of naming

A quick but very important side note about good naming. Take this to heart right now: Good names are important. Do yourself, and every other programmer reading your code, a favor by always using meaningful function and variable names.

For example, x is a very non-descriptive name for a variable or function. As we tackle more complicated problems and our code grows to be more complex, we are likely to forget what badly named variables originally stood for and what their purpose was. Non-descriptive names make our code error-prone. Great code reads like English and almost explains itself. As programmers, our goal is to write code that is not only correct, but also elegant, readable, and maintainable! Hold yourself to this high standard.

As far as syntax goes in JavaScript, we always name our functions and variables camelCase for multiple words. (Ex: tipCalculator, currentNumber, puppyPartyFinder). Other languages use other conventions so it's best to pick up the standard for your chosen language and stick with it.

### What you learned so far

By writing a function we can reuse code over and over again to solve similar problems with different input data (arguments). This will make your life easier and allow you to start working on more complex problems.

This reading covered:

- How to define and invoke a function in JavaScript
- How to use the return keyword to return a value from a function
- Writing readable JavaScript code by using meaningful names and following camelCase conventions for multiple word variables and functions
