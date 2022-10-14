# JavaScript

## Basics

### Object

Collection of key/value pairs.

```js
let cheat = {
  topic: "JavaScript",
  version: 1
};

// Create new property by assignment
cheat.date = "2022-10-14"
cheat.empty = {}

// Access property
cheat.topic
cheat["version"]

// Conditionally access property
cheat.contents?.section1
```

### Array

Numerically indexed list of values.

```js
let primes = [2, 3, 5, 7];
primes[4] = 9;

primes[0]
primes.length
primes[primes.length-1]

let empty = [];

// Arrays and objects can hold each other
let points = [
  {x: 0, y: 0},
  {x: 1, y: 1}
];
let data = {
  array1: [[1,2], [3,4]],
  array2: [[5,6], [7,8]]
};
```

### Operators

```js
let count = 0;
count++;    // count + 1;
count--;    // count - 1;
count += 2; // count + 2;
count *= 3; // count * 3;

let x = 2, y = 33;
x === y   // false
x !== y   // true
x < y     // true
x <= y    // true
false === (x > y) // true: false equals false
(x === 2) && (y ===3) // true
(x > 3) || (y < 3) // false
!(x === y) // true
```

### Functions

```js
function plus1(x) {
  return x + 1;
}

// Can assign a function to a var
let square = function(x) {
  return x * x;
}
```

#### Arrow Functions

```js
const plus1 = x => x + 1; // map x to output x +1
const square = x => x * x;
```

#### Methods

```js
points.dist = function() {
  let p1 = this[0];
  let p2 = this[1];
  let a = p2.x-p1.x;
  let b = p2.y-p1.y;
  return Math.sqrt(a*a + b*b); // a^2 + b^2 = c^2
}
points.dist()
```

### Control statements

```js
if (x >= 0) {
  // Do something
}
else {
  // Do something else
}

function sum(array) {
  let sum = 0;
  for(let x of array) { // Loop over array, assigning each element to x
    sum += x;
  }
  return sum;
}

let x = 5;
while(x > 1) {
  // Do something
  x--;
}

let n = 5;
for(i=1, i <= n; i++)
  // Do something
```
