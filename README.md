> Some JavaScript tips to make your code even more awesome than it already is!

JavaScript is an awesome language, but from time to time you can get lost in the multitude of features it offers nowadays.

This repository is going to give you some short and concise tips to improve your code or make things easier or better to read.

## Table of Contents
- [Creating a really empty object](#creating-a-really-empty-object)
- [Swap variables with the array destructuring assignment](#swap-variables-with-the-array-destructuring-assignment)
- [Iterating over indices and values of an array with a for..of loop](#iterating-over-indices-and-values-of-an-array-with-a-forof-loop)
- [Switching over ranges](#switching-over-ranges)
- [Extract unique values from an array](#extract-unique-values-from-an-array)
- [Get the last elements from an array](#get-the-last-elements-from-an-array)

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

## Iterating over indices and values of an array with a for..of loop
You can also get access to the index, next to the element, when you iterate over an array with a for..of-loop.

There is no need to handle the index manually. Array.prototype.entries can do that for you.

```JavaScript
// Iterating over the array with each individual element at hand while separately
// keeping track of the index.
let i = 0;
for (const element of array) {
  console.log(i++, element);
}


// Array.prototype.entries() returns an iterator which itself returns an array instead
// of each individual element every time next() is called.
// By using array destructuring, you take the tuple (array) the iterator returns on
// each iteration step and destructure it into individual variables.
// You can then iterate over the array while having the index and the element at hand on
// each iteration.
for (const [index, element] of array.entries()) {
  console.log(index, element);
}
```

## Switching over ranges
You can also use the switch statement in JavaScript to cover a range instead of only one value. Simply switch over true.

It's a great way to use a switch instead of if-statements where it's simply more readable.

```JavaScript
function getCheering(followers) {
  // If you were to switch over followers, you'd be surprised,
  // because you'd always hit the default case.
  // By switching over true, all cases get evaluated properly, although they
  // contain numeric ranges!
  switch (true) {
    case followers >= 2000:
      return "Wow, I'm speechless. I'm so happy, thank you!!!";
    case followers >= 1000:
      return "Wow, this is so great!";
    case followers >= 500:
      return "Awesome!";
    case followers >= 100:
      return "Wooooo!";
    default:
      return "Yay!";
  }
}

const cheer = getCheering(2125);
console.log(cheer); // => "Wow, I'm speechless. I'm so happy, thank you!!!"
```

## Extract unique values from an array
You can get all unique values from an array by using a Set and the spread operator.

No need to filter the array, or use some other, less readable methods.

But be adviced, this only works for primitives.

```JavaScript
const array = [1, 1, 1, 2, 3, 2, 4, 5, 1, 6, 7, 3, 8, 7, 6, 9];

const uniqueValues = [...new Set(array)];
// => uniqueValues is now: [1, 2, 3, 4, 5, 6, 7, 8, 9]
```

# Get the last elements from an array
You can get the last elements of an array by using Array.prototype.slice with negative numbers.

```JavaScript
const array = [1, 2, 3, 4, 5, 6, 7, 8, 9];

array.slice(-1); // => [9]
array.slice(-2); // => [8, 9]
array.slice(-3); // => [7, 8, 9]
```
