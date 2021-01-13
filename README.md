> Some JavaScript tips to make your code even more awesome than it already is!

JavaScript is an awesome language, but from time to time you can get lost in the multitude of features it offers nowadays.

This repository is going to give you some short and concise tips to improve your code or make things easier or better to read.

## Table of Contents

## Tips
### Creating a really empty object
You can create a really empty object by using `Object.create(null)`.

This prevents modification from the outside and creates a dictionary as vanilla as possible.

```JavaScript
// object used as a dict
const dict = {};
dict.__proto__; // => {}
dict.hasOwnProperty; // => f hasOwnProperty() {}

Object.prototype.myFunction = function() {};

dict.myFunction; // => f myFunction() {}

const emptyDict = Object.create(null);
emptyDict.__proto__; // => undefined
emptyDict.hasOwnProperty; // => undefined

// emptyDict isn't affected by the Object prototype
emptyDict.myFunction; // => undefined
```

## Swap variables with the array destructuring assignment
You can use an array destructuring assignment to swap two variables.

```JavaScript
let a = 1;
let b = 2;

// traditional
let tmp = a;
a = b;
b = tmp;

// with destructuring
[a, b] = [b, a];
```
