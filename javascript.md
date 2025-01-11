# JavaScript Notes

A concise summary of essential JavaScript concepts.

## 1. Variables and Scope

- **var**: Function-scoped, reassignable, hoisted.  
- **let**: Block-scoped, reassignable, no hoisting like var.  
- **const**: Block-scoped, not reassignable.

```js
function testScope() {
    if (true) {
        var x = 10;
        let y = 20;
        const z = 30;
    }
    console.log(x); // 10
    // console.log(y); // Error
    // console.log(z); // Error
}
```

## 2. Data Types

- **Primitives**: string, number, boolean, null, undefined, Symbol, BigInt  
- **Reference**: Objects (arrays, functions, etc.)

```js
let num = 42;             // Primitive
let obj = { key: "value" }; // Reference
```

## 3. Operators

- **Arithmetic**: `+`, `-`, `*`, `/`, `%`, `**`  
- **Comparison**: `===` vs `==`  
- **Logical**: `&&`, `||`, `!`

```js
console.log(5 ** 2); // 25
console.log(5 === "5"); // false
```

## 4. Functions

- **Function Declaration**: Hoisted  
- **Arrow Functions**: Concise, no own `this`
- **Default Parameters**: `function greet(name = "Guest") { ... }`
- **Rest/Spread**: `...`

```js
function sayHello() {
    console.log("Hello!");
}
sayHello();

const add = (a, b) => a + b;
```

## 5. Control Flow

- **for**, **for...of**, **for...in**

```js
for (const value of [1, 2, 3]) console.log(value);
for (const key in { a: 1, b: 2 }) console.log(key);
```

## 6. Objects

- **Object Literals** and **Destructuring**
- **Shorthand Properties**

```js
const person = { name: "John", age: 30 };
const { name, age } = person;

const user = { name };
```

## 7. Arrays

- **map**, **filter**, **reduce**

```js
const numbers = [1, 2, 3, 4];
const doubled = numbers.map(n => n * 2);
```

## 8. Event Loop & Async JS

- **Callbacks**, **Promises**, **async/await**

```js
setTimeout(() => console.log("Later"), 1000);
console.log("First");

async function getData() {
    const data = await fetchData();
    console.log(data);
}
```

## 9. Prototype & this

```js
function Person(name) {
    this.name = name;
}
Person.prototype.sayHello = function() {
    console.log(`Hello, I'm ${this.name}`);
};
```

## 10. ES6 Modules

```js
// Default export
export default function greet() { ... }
import greet from "./module.js";

// Named export
export const PI = 3.14;
import { PI } from "./module.js";
```

## 11. Closures

```js
function outer() {
    let counter = 0;
    return function inner() {
        counter++;
        console.log(counter);
    };
}
```

## 12. Memory Management

- Detach unused listeners  
- Nullify references when not needed

## 13. Web APIs

- **localStorage**, **sessionStorage**  
- **fetch** for network requests

```js
localStorage.setItem("key", "value");
fetch("https://api.example.com/data")
    .then(r => r.json())
    .then(data => console.log(data));
```
