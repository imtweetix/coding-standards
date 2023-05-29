# JavaScript Coding Standard using ES6 (ECMAScript 2015)

## Overview

JavaScript ES6, also known as ECMAScript 2015, is a significant update to the language that introduced several advanced features to facilitate the development of complex applications. It brought numerous enhancements to the language that make JavaScript code more readable, maintainable, and easier to write.

## 1. Use `const` and `let` Instead of `var`

Always use `const` or `let` to declare variables instead of `var`. `const` and `let` respect block scope, which can prevent bugs associated with variable hoisting.

```javascript
// Good
let count = 1;
const name = 'John';

// Bad
var count = 1;
var name = 'John';
```

## 2. Template Literals

Use template literals (`` ` ``) for string interpolation.

```javascript
// Good
const greeting = `Hello, ${name}!`; // Take note of the quotes

// Bad
const greeting = 'Hello, ' + name + '!';
```

## 3. Arrow Functions

Use arrow functions for shorter syntax and lexical `this`.

```javascript
// Good
const add = (a, b) => a + b;

// Bad
const add = function(a, b) {
  return a + b;
};
```

## 4. Default Parameters

Use default parameters instead of setting them inside function bodies.

```javascript
// Good
function multiply(a, b = 1) {
  return a * b;
}

// Bad
function multiply(a, b) {
  b = b || 1;
  return a * b;
}
```

## 5. Object and Array Destructuring

Use object and array destructuring to make your code more readable.

```javascript
// Good
const [first, , third] = ['foo', 'bar', 'baz'];

const { firstName, lastName } = person;

// Bad
const first = arr[0];
const third = arr[2];

const firstName = person.firstName;
const lastName = person.lastName;
```

## 6. Rest and Spread Operators

Use rest (`...`) and spread operators to write more concise and flexible code.

```javascript
// Good
const numbers = [1, 2, 3];
const copy = [...numbers];

function printNames(...names) {
  names.forEach(name => console.log(name));
}

// Bad
const numbers = [1, 2, 3];
const copy = numbers.slice();

function printNames() {
  const names = Array.prototype.slice.call(arguments);
  names.forEach(name => console.log(name));
}
```

## 7. Use Promises for Asynchronous Programming

Promises provide a cleaner, more elegant syntax for handling asynchronous operations compared to callbacks.

```javascript
fetch('url')
  .then(response => response.json())
  .then(data => console.log(data))
  .catch(error => console.log(error));
```

## 8. Async/Await

Use async/await for even cleaner asynchronous code. Async functions return a promise, and the `await` keyword waits for the promise to resolve.

```javascript
async function fetchData() {
  try {
    const response = await fetch('url');
    const data = await response.json();
    console.log(data);
  } catch (error) {
    console.log(error);
  }
}
```

## 9. Modules

Use ES6 modules (import/export) to structure your code. Modules help keep your codebase clean and organized.

```javascript
// module.js
export const add = (a, b) => a + b;
export default multiply;

// main.js
import { add } from './module';
import multiply from './module';
```

## 10. Classes

Use ES6 classes for object-oriented programming. However, remember that JavaScript is prototype-based, and classes are just syntactic sugar.

```javascript
class Animal {
  constructor(name) {
    this.name = name;
 }

  speak() {
    console.log(`${this.name} makes a noise.`);
  }
}

class Dog extends Animal {
  speak() {
    console.log(`${this.name} barks.`);
  }
}
```

## 11. Block-Scoped Functions

Block-scoped functions can help prevent bugs associated with variable hoisting.

```javascript
// Good
{
  function test() {
    //...
  }
}

// Bad
if (true) {
  function test() {
    //...
  }
}
```

## 12. Shorthand Property Names

Use shorthand property names in object literals.

```javascript
// Good
let a = 1, b = 2;
const obj = { a, b };

// Bad
let a = 1, b = 2;
const obj = { a: a, b: b };
```

## 13. Avoid Using `eval()`

The use of `eval()` function is dangerous and leads to security and performance issues.

## 14. Always use `===` and `!==`

Always use `===` and `!==` instead of `==` and `!=` as they check both type and value equality.

```javascript
// Good
if (length === 0) {
  // Do something
}

// Bad
if (length == 0) {
  // Do something
}
```

## 15. Iterating Over Arrays and NodeLists

Use `for...of` instead of `for` or `forEach` for looping over arrays or NodeLists.

```javascript
// Good
for (const value of array) {
  console.log(value);
}

// Bad
for (let i = 0; i < array.length; i++) {
  console.log(array[i]);
}
```

## 16. Exponential Operator

Use the `` operator for exponentiation.

```javascript
// Good
const square = 5  2;

// Bad
const square = Math.pow(5, 2);
```

## 17. Parameter Destructuring

Use parameter destructuring for cleaner code.

```javascript
// Good
function fullName({ firstName, lastName }) {
  return `${firstName} ${lastName}`;
}

// Bad
function fullName(user) {
  return `${user.firstName} ${user.lastName}`;
}
```

## 18. Computed Property Names

Use computed property names in object literals when property names are dynamic.

```javascript
const property = 'foo';
const object = {
  [property]: 'Hello',
  ['b' + 'ar']: 'world'
};
```

## 19. Map Over forEach

Use `map()` over `forEach()` when you want to create a new array by transforming an existing one.

```javascript
// Good
const doubled = numbers.map(number => number * 2);

// Bad
let doubled = [];
numbers.forEach(number => {
  doubled.push(number * 2);
});
```

## 20. Use `Array.includes()` Over `Array.indexOf()`

Use `Array.includes()` to check if an array includes a certain value. It's more readable and expresses the intent clearer than `Array.indexOf()`.

```javascript
// Good
if (array.includes(value)) {
  // ...
}

// Bad
if (array.indexOf(value) > -1) {
  // ...
}
```

## 21. Multiline Strings

Use template literals for multiline strings.

```javascript
// Good
const string = `
  Hello,
  world!
`;

// Bad
const string = 'Hello,\n' +
  'world!';
```

## 22. Short-circuit Evaluation

Use short-circuit evaluation to provide default values.

```javascript
// Good
const value = input || 'default';

// Bad
let value;
if (input) {
  value = input;
} else {
  value = 'default';
}
```

## 23. Ternary Operator

Use the ternary operator for simple conditional expressions.

```javascript
// Good
const value = condition ? 'foo' : 'bar';

// Bad
let value;
if (condition) {
  value = 'foo';
} else {
  value = 'bar';
}
```

## 24. Avoid Modifying Built-In Prototypes

You generally want to avoid extending the prototypes of built-in JavaScript objects.

```javascript
// Bad
Array.prototype.diff = function(a) {
  return this.filter(function(i) {
    return a.indexOf(i) < 0;
  });
};
```

## 25. Use Named Function Expressions

Using named function expressions can produce more readable stack traces in case of an error.

```javascript
// Good
const foo = function bar() {
  // ...
};

// Bad
const foo = function() {
  // ...
};
```

## 26. Use Function Declarations for Top-Level Functions

Function declarations are hoisted, making it easier to understand the flow of your program.

```javascript
// Good
function foo() {
  // ...
}

// Bad
const foo = function() {
  // ...
};
```

## 27. Proper Error Handling

Always use `try...catch` or promise chaining to handle errors.

```javascript
// Good
try {
  performOperation();
} catch (error) {
  console.error(error);
}

// Bad
performOperation();
```

## 28. Don't Extend Native Data Types

Avoid extending native JavaScript objects as it can lead to unexpected behavior for other developers.

## 29. Avoid Using Magic Numbers

Use constants instead of inserting number literals or other constant values directly into your code.

```javascript
// Good
const MAXIMUM_TRIES = 3;

for(let i = 0; i < MAXIMUM_TRIES; i++) {
  // Try something
}

// Bad
for(let i = 0; i < 3; i++) {
  // Try something
}
```

## 30. Use Descriptive Variable Names

Descriptive variable names make your code more self-documenting.

```javascript
// Good
let elapsedTimeInDays = 3;

// Bad
let e = 3;
```

## Conclusion

Following these standards will not only make your code more readable and understandable, but it will also make it more maintainable and less prone to bugs.
