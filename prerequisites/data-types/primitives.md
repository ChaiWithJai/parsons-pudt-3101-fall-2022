## Undefined

![Undefined](https://res.cloudinary.com/dg3gyk0gu/image/upload/v1580435620/just-javascript-email-images/jj04/undefined-revised.png)

We’ll start our tour with the Undefined type. This is a very straightforward place to start, because there is only one value of this type—undefined.

```
console.log(typeof(undefined)); // "undefined"
```

It’s called undefined, so you might think it’s not there—but it is a value, and a very real one! Like a black hole, `undefined` is grumpy and can often spell trouble. For example, reading a property from it will break your program:

```
let person = undefined;
console.log(person.mood); // TypeError!
```

Oh, well. Luckily, there is only one undefined in our entire JavaScript universe. You might wonder: why does it exist at all? In JavaScript, it represents the concept of an unintentionally missing value.

You could use it in your own code by writing `undefined`—like you write `2` or `"hello"`. However, undefined also commonly “occurs naturally.” It shows up in some situations where JavaScript doesn’t know what value you wanted. For example, if you forget to assign a variable, it will point to undefined:

```
let bandersnatch;
console.log(bandersnatch); // undefined
```

Then you can point it to another value, or to undefined again if you want.

Don’t get too hung up on its name. It’s tempting to think of `undefined` as some kind of variable status, e.g. “this variable is not yet defined.” But that’s a completely misleading way to think about it! In fact, if you read a variable that was actually not defined (or before the `let` declaration), you will get an error:

```
console.log(jabberwocky); // ReferenceError!
let jabberwocky;
```

That has nothing to do with undefined.

Really, `undefined` is a regular primitive value, like `2` or `"hello"`.

Handle it with care.

## Null

![Null](https://res.cloudinary.com/dg3gyk0gu/image/upload/v1580435620/just-javascript-email-images/jj04/null-revised.png)

The next stop on our tour is Null. You can think of null as undefined’s sister; there is only one value of this type—null. It behaves very similarly to undefined. For example, it will also throw a fuss when you try to access its properties:

```
let mimsy = null;
console.log(mimsy.mood); // TypeError!
```

![Visualize Null](https://res.cloudinary.com/dg3gyk0gu/image/upload/v1580435620/just-javascript-email-images/jj04/null-example.png)

In practice, null is used for intentionally missing values. Why have both null and undefined? This could help you distinguish a coding mistake (which might result in undefined) from valid missing data (which you might express as null). However, this is only a convention, and JavaScript doesn’t enforce this usage. Some people avoid both of them as much as possible!

I don’t blame them.

## Booleans

![Booleans](https://res.cloudinary.com/dg3gyk0gu/image/upload/v1580435620/just-javascript-email-images/jj04/boolean-revised.png)

Next on our tour, we’ll meet booleans! Like day and night or on and off, there are only two boolean values: true and false.

```
console.log(typeof(true)); // "boolean"
console.log(typeof(false)); // "boolean"
```

We can perform logical operations with them:

```
let isSad = true;
let isHappy = !isSad; // The opposite
let isFeeling = isSad || isHappy; // Is at least one of them true?
let isConfusing = isSad && isHappy; // Are both true?
```

![Visualize Booleans](https://res.cloudinary.com/dg3gyk0gu/image/upload/v1580435620/just-javascript-email-images/jj04/boolean-example.png)

First, verify that isHappy points to false, isFeeling points to true, and isConfusing points to false. (If you got different answers, there is a mistake somewhere along the way—walk through each line step by step.)

Next, verify that there is only one true and one false value on your sketch. This is important! Regardless of how booleans are stored in the memory, in our mental model there are only two of them.

## Numbers

![Numbers](https://res.cloudinary.com/dg3gyk0gu/image/upload/v1580773430/just-javascript-email-images/jj04/numbers-v2.png)

So far, we have introduced ourselves to four values: `null`, `undefined`, `true`, and `false`.

Hold on tight, as we add eighteen quintillion, four hundred and thirty-seven quadrillion, seven hundred and thirty-six trillion, eight hundred and seventy-four billion, four hundred and fifty-four million, eight hundred and twelve thousand, six hundred and twenty-four more values to our mental model!

I am, of course, talking about numbers:

```
console.log(typeof(28)); // "number"
console.log(typeof(3.14)); // "number"
console.log(typeof(-140)); // "number"
```

At first, numbers might seem unremarkable, but let’s get to know them a little better!

### Math for Computers

JavaScript numbers don’t behave exactly the same way as regular mathematical numbers do. Here is a snippet that demonstrates it:

```
console.log(0.1 + 0.2 === 0.3); // false
console.log(0.1 + 0.2 === 0.30000000000000004); // true
```

This might look very surprising! Contrary to popular belief, this doesn’t mean that JavaScript numbers are broken. This behavior is common in different programming languages. It even has a name: floating-point math.

You see, JavaScript doesn’t implement the kind of math we use in real life. Floating-point math is “math for computers.” Don’t worry too much about this name or how it works exactly. Very few people know about all its subtleties, and that’s the point! It works well enough in practice that most of the time you won’t think about it. Still, let’s take a quick look at what makes it different.

### Colors and Numbers

Have you ever used a scanner to turn a physical photo or a document into a digital one? This analogy can help us understand JavaScript numbers.

Scanners usually distinguish at most 16 million colors. If you draw a picture with a red crayon and scan it, the scanned image should come out red too—but it will have the closest red color our scanner picked from those 16 million colors. So if you have two red crayons with ever so slightly different colors, the scanner might be fooled into thinking their color is exactly the same!

We can say that a scanner uses colors with limited precision.

Floating-point math is similar. In real math, there is an infinite set of numbers. But in floating-point math, there are only 18 quintillion of them. So when we write numbers in our code or do calculations with them, JavaScript picks the closest numbers that it knows about—just like our scanner does with colors.

In other words, JavaScript uses numbers with limited precision.

We can imagine all of the JavaScript numbers on an axis. The closer we are to 0, the more precision numbers have, and the closer they “sit” to each other:

![GIF image talking about precise.](../../assets//math-for-computers.gif)

This is because relatively small numbers occur more often in our programs, and we usually want them to be precise.

As we move from 0 in either direction, we start losing precision. At some point, even two closest JavaScript numbers stay further apart than by 1:

```
console.log(Number.MAX_SAFE_INTEGER); // 9007199254740991
console.log(Number.MAX_SAFE_INTEGER + 1); // 9007199254740992
console.log(Number.MAX_SAFE_INTEGER + 2); // 9007199254740992 (again!)
console.log(Number.MAX_SAFE_INTEGER + 3); // 9007199254740994
console.log(Number.MAX_SAFE_INTEGER + 4); // 9007199254740996
console.log(Number.MAX_SAFE_INTEGER + 5); // 9007199254740996 (again!)
```

Luckily, any whole numbers between Number.MIN_SAFE_INTEGER and Number.MAX_SAFE_INTEGER are exact. This is why 10 + 20 === 30.

But when we write 0.1 or 0.2, we don’t get exactly 0.1 and 0.2. We get the closest available numbers in JavaScript. They are almost exactly the same, but there might be a tiny difference. These tiny differences add up, which is why 0.1 + 0.2 doesn’t give us exactly the same number as writing 0.3.

If this is still confusing, don’t worry. You can learn more about floating-point math, but you already know more than I did when I started writing this guide! Unless you work on finance apps, you likely won’t need to worry about this.

Special Numbers
It is worth noting that floating-point math includes a few special numbers. You might occasionally run into NaN, Infinity, -Infinity, and -0. They exist because sometimes you might execute operations like 1 / 0, and JavaScript needs to represent their result somehow. The floating-point math standard specifies how they work, and what happens when you use them.

Here’s how special numbers may come up in your code:

```
let scale = 0;
let a = 1 / scale; // Infinity
let b = 0 / scale; // NaN
let c = -a; // -Infinity
let d = 1 / c; // -0
```

Out of these special numbers, NaN is particularly interesting. NaN, which is the result of 0 / 0 and some other invalid math, stands for “not a number.”

You might be confused by why it claims to be a number:

`console.log(typeof(NaN)); // "number"`

However, there is no trick here. From a JavaScript perspective, NaN is a numeric value. It is not null, undefined, a string, or some other type. But in the floating-point math, the name for that term is “not a number”. So it is a numeric value. It happens to be called “not a number” because it represents an invalid result.

It’s uncommon to write code using these special numbers. However, they might come up due to a coding mistake. So it’s good to know they exist.

## Strings

![Strings](https://res.cloudinary.com/dg3gyk0gu/image/upload/v1580773483/just-javascript-email-images/jj05/strings-v2.png)

Our next tour stop is Strings, which represent text in JavaScript. There are three ways to write strings (single quotes, double quotes, and backticks), but they refer to the same concept. These three string literals result in the same string value:

```
console.log(typeof("こんにちは")); // "string"
console.log(typeof('こんにちは')); // "string"
console.log(typeof(`こんにちは`)); // "string"
```

An empty string is a string, too:

```
console.log(typeof('')); // "string"
```

### Strings Aren’t Objects

All strings have a few built-in properties.

```
let cat = 'Cheshire';
console.log(cat.length); // 8
console.log(cat[0]); // "C"
console.log(cat[1]); // "h"
```

This doesn’t mean that strings are objects! String properties are special and don’t behave the way object properties do. For example, you can’t assign anything to cat[0]. Strings are primitives, and all primitives are immutable.

### A Value for Every Conceivable String

In our universe, there is a distinct value for every conceivable string. Yes, this includes your grandmother’s maiden name, the fanfic you published ten years ago under an alias, and the script of Matrix 5 which hasn’t been written yet.

Of course, all possible strings can’t literally fit inside a computer memory chip. But the idea of every possible string can fit inside your head. Our JavaScript universe is a model for humans, not for computers!

This might prompt a question. Does this code create a string?

```
// Try it in your console
let answer = prompt('Enter your name');
console.log(answer); // ?
```

Or does it merely summon a string that already exists in our universe?

The answer to this question depends on whether we’re studying JavaScript “from the outside” or “from the inside.”

Outside our mental model, the answer depends on a specific implementation. Whether a string is represented as a single block of memory, multiple blocks, or a special data structure like a rope, is up to the JavaScript engine.

The question of whether a string already “exists” or is “created” is not something we can test from the code. Inside our mental model, this question doesn’t mean anything. We can’t set up an experiment to say whether strings “get created” or “get summoned” within our JavaScript universe.

To keep our mental model simple, we will say that all conceivable string values already exist from the beginning—one value for every distinct string.
