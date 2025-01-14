### **JavaScript ES6+ Features: Answers with Examples**

---

#### 1. **What are some key ES6 features?**  
- `let` and `const` for block-scoped variables.  
- Arrow functions (`=>`) for concise function syntax.  
- Template literals for string interpolation.  
- Destructuring for extracting values from arrays/objects.  
- Spread/rest operators (`...`).  
- Promises and `async/await` for handling asynchronous code.  
- Modules (`import/export`).  
- Classes and enhanced object literals.

---

#### 2. **Explain `let` vs `const` vs `var`.**  
- **`var`**: Function-scoped, can be redeclared, and hoisted (initialized as `undefined`).  
- **`let`**: Block-scoped, cannot be redeclared, and hoisted (not initialized).  
- **`const`**: Block-scoped, must be initialized, and cannot be reassigned.

**Example:**  
```javascript
var x = 1;
let y = 2;
const z = 3;

if (true) {
  var x = 10; // Redeclares x
  let y = 20; // New block-scoped y
  // z = 30; // Error: Assignment to constant variable
}

console.log(x); // 10
console.log(y); // 2
console.log(z); // 3
```

---

#### 3. **What are arrow functions, and how are they different from regular functions?**  
Arrow functions provide a concise syntax and do not have their own `this`, `arguments`, or `super`.

**Example:**  
```javascript
const add = (a, b) => a + b;
console.log(add(2, 3)); // 5

function regular() {
  console.log(this); // Refers to the caller
}

const arrow = () => {
  console.log(this); // Inherits `this` from surrounding scope
};
```

---

#### 4. **What is destructuring in JavaScript?**  
Destructuring allows you to extract values from arrays or objects into variables.

**Array Destructuring:**  
```javascript
const [a, b] = [1, 2];
console.log(a, b); // 1, 2
```

**Object Destructuring:**  
```javascript
const { name, age } = { name: "Alice", age: 25 };
console.log(name, age); // Alice, 25
```

---

#### 5. **Explain the spread (`...`) and rest (`...`) operators.**  
- **Spread**: Expands arrays/objects into individual elements.  
  ```javascript
  const arr = [1, 2, 3];
  console.log(...arr); // 1, 2, 3
  
  const obj1 = { a: 1 };
  const obj2 = { ...obj1, b: 2 };
  console.log(obj2); // { a: 1, b: 2 }
  ```

- **Rest**: Collects remaining elements into an array.  
  ```javascript
  function sum(...nums) {
    return nums.reduce((acc, n) => acc + n, 0);
  }
  console.log(sum(1, 2, 3)); // 6
  ```

---

#### 6. **What are template literals?**  
Template literals allow embedded expressions in strings using backticks (\`).

**Example:**  
```javascript
const name = "Alice";
const age = 25;
console.log(`My name is ${name}, and I am ${age} years old.`);
```

---

#### 7. **What is the difference between `import` and `require`?**  
- **`import`**: ES6 syntax, used in modules, supports static imports.  
  ```javascript
  import { myFunction } from './module.js';
  ```

- **`require`**: CommonJS syntax, used in Node.js, supports dynamic imports.  
  ```javascript
  const myFunction = require('./module');
  ```

---

#### 8. **Explain the use of `async/await` in JavaScript.**  
`async/await` simplifies working with Promises, making asynchronous code easier to read.

**Example:**  
```javascript
async function fetchData() {
  try {
    const response = await fetch('https://api.example.com/data');
    const data = await response.json();
    console.log(data);
  } catch (error) {
    console.error('Error:', error);
  }
}

fetchData();
```

---

#### 9. **What are default parameters in ES6?**  
Default parameters allow setting default values for function arguments.

**Example:**  
```javascript
function greet(name = "Guest") {
  console.log(`Hello, ${name}!`);
}

greet(); // "Hello, Guest!"
greet("Alice"); // "Hello, Alice!"
```

---

#### 10. **Explain the `for...of` and `for...in` loops.**  
- **`for...of`**: Iterates over iterable objects like arrays, strings, etc.  
  ```javascript
  const arr = [1, 2, 3];
  for (const num of arr) {
    console.log(num); // 1, 2, 3
  }
  ```

- **`for...in`**: Iterates over enumerable properties of an object.  
  ```javascript
  const obj = { a: 1, b: 2 };
  for (const key in obj) {
    console.log(key); // a, b
  }
  ```

---

Let me know if you want more on ES6+ features or move to another topic!
