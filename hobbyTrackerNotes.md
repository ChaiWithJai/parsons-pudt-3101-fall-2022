# Notes on `hobbyTracker`

## Different Ways to Copy an Object

Remember the lesson on variables versus values?

Let's take this block of code:

```
let shrek = {};
let donkey = {};

const result = shrek === donkey;
console.log(result);
```

What do you expect the value of `result` to be? **Don't look down!** Make an educated guess about your answer and write down on a piece of paper why.

The answer is that `result` would return `false`. This is because objects (including arrays and functions) a reference in memory. This is why I harp so much on assigning variables to values during the diagramming portion of class.

So, let's backtrack just a bit:

```
let sisters = 3;
let musketeers = 3;
```

![image](https://user-images.githubusercontent.com/41024828/192020015-33c6350c-3bca-4a32-91f9-e0f44daae371.png)

```
let shrek = {};
let donkey = {};
```

![image](https://user-images.githubusercontent.com/41024828/192020538-f2ac922a-c71e-43a7-8b7d-314902274c00.png)

**The key message here is that just because the contents of an array, object or function are the same, they will not be equal to eachother UNLESS they have the same reference in memory.**

### The Goal is to make a copy of the contents of the object, not its reference in memory

```
let shrek = {isFeaturedInAHitMovie: true, isMainCharacter: true};
donkey = shrek;
donkey.isMainCharacter = false;

console.log(shrek.isMainCharacter);
```

What do you think we're going to log here:  `true` or `false`?

The answer is `false`.

But, why we re-assigned by writing the expression `donkey.isMainCharacter = false`?

Yes, but in this example both `shrek` and `donkey` are pointing to the **same reference in memory**.

### How do we fix this?

#### Make a copy of the object

##### Using a for in loop to make a copy of an object

We're going to use a new type of `for` statement. It's a `for ... in loop`. [It](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/for...in) is used to help us iterate through keys of an object.

Note:  do not iterate over arrays with a `for ... in loop`. You'll want to use a `for ... of loop` instead, but I still HIGHLY advise against doing that at your current level.

```
let shrek = {isFeaturedInAHitMovie: true, isMainCharacter: true};
let donkey = {};

for (const key in shrek) {
  const value = shrek[key];
  donkey[key] = value;
}

donkey.isMainCharacter = false;

console.log(shrek.isMainCharacter);
```

##### Using `Object.assign`

`Object.assign` is a special method that allows us to copy the values of multiple objects and merge them into a single object. Read more about the API on [MDN](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Object/assign).

```
let shrek = {isFeaturedInAHitMovie: true, isMainCharacter: true};
let donkey = {};

Object.assign(donkey, shrek);

donkey.isMainCharacter = false;

console.log(shrek.isMainCharacter);
```

##### Using the rest operator

This is one of the most [powerful features](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Spread_syntax) from ES6. Remember I said, how I said to stay away from ES6? You shouldn't use this, but if you see this in code somewhere else I want you to understand wants happening.

```
let shrek = {isFeaturedInAHitMovie: true, isMainCharacter: true};
let donkey = {...shrek};

donkey.isMainCharacter = false;

console.log(shrek.isMainCharacter);
```

You'll see tons of examples using this `rest` (b.k.a. `spread`) operator. Most people don't know how it works under the hood, its really using an Iterator to move through each key of the object. But don't let anyone clown you for not using it, unless they can write the source code for how the Iterator works under the hood. And to them I say, "I don't argue with people who are broker than me about money."



