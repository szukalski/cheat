# JavaScript

## Types

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
