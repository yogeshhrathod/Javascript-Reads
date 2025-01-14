### **Currying: Answers with Examples**

---

#### 1. **What is currying in JavaScript?**  
Currying is a technique of transforming a function with multiple arguments into a series of functions, each taking a single argument.

**Example:**  
```javascript
function multiply(a) {
  return function(b) {
    return a * b;
  };
}

const multiplyBy2 = multiply(2);
console.log(multiplyBy2(3)); // 6
console.log(multiplyBy2(10)); // 20
```

---

#### 2. **How does currying differ from partial application?**  
- **Currying**: Breaks a function into a chain of functions, each taking one argument.  
  ```javascript
  const add = (a) => (b) => a + b;
  console.log(add(2)(3)); // 5
  ```

- **Partial Application**: Fixes a few arguments of a function, returning a function for the remaining arguments.  
  ```javascript
  function add(a, b, c) {
    return a + b + c;
  }

  const partialAdd = add.bind(null, 2);
  console.log(partialAdd(3, 4)); // 9
  ```

---

#### 3. **Write a function to curry any given function.**  
**Generic currying function:**  
```javascript
function curry(fn) {
  return function curried(...args) {
    if (args.length >= fn.length) {
      return fn(...args);
    } else {
      return function(...nextArgs) {
        return curried(...args, ...nextArgs);
      };
    }
  };
}

// Example usage:
function sum(a, b, c) {
  return a + b + c;
}

const curriedSum = curry(sum);
console.log(curriedSum(1)(2)(3)); // 6
console.log(curriedSum(1, 2)(3)); // 6
```

---

#### 4. **What are the advantages of using currying in functional programming?**  
- **Reusability**: Create specialized functions by fixing arguments.  
  ```javascript
  const greet = (greeting) => (name) => `${greeting}, ${name}!`;
  const sayHello = greet("Hello");
  console.log(sayHello("Alice")); // "Hello, Alice!"
  ```

- **Readability**: Makes code more readable and modular.  
  ```javascript
  const calculateVolume = (length) => (width) => (height) => length * width * height;
  console.log(calculateVolume(5)(4)(3)); // 60
  ```

- **Avoids repeated arguments**: Pass arguments gradually as needed.

---

#### 5. **Give a real-world example of where currying can be useful.**  
**Example: Logging with custom prefixes**  
```javascript
function log(prefix) {
  return function(message) {
    console.log(`[${prefix}] ${message}`);
  };
}

const infoLog = log("INFO");
const errorLog = log("ERROR");

infoLog("This is an information message."); // [INFO] This is an information message.
errorLog("This is an error message.");       // [ERROR] This is an error message.
```

**Example: Event handler customization**  
```javascript
function addEventListenerWithPrefix(prefix) {
  return function(eventType, element, callback) {
    element.addEventListener(eventType, (event) => {
      console.log(`${prefix}: Event fired`);
      callback(event);
    });
  };
}

const button = document.querySelector("#myButton");
const prefixedListener = addEventListenerWithPrefix("ButtonClick");

prefixedListener("click", button, () => {
  console.log("Button was clicked!");
});
```

---

Let me know if you'd like further clarification on any point!
