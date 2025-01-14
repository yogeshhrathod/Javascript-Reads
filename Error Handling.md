### **JavaScript Error Handling: Answers with Examples**

---

#### 1. **What are the different types of errors in JavaScript?**  
- **Syntax Error**: Errors in the structure of the code.  
  Example:  
  ```javascript
  console.log("Hello); // Missing closing quote
  ```

- **Reference Error**: Using a variable that hasn't been declared.  
  Example:  
  ```javascript
  console.log(x); // x is not defined
  ```

- **Type Error**: Performing an invalid operation on a type.  
  Example:  
  ```javascript
  const num = 5;
  num.toUpperCase(); // TypeError: num.toUpperCase is not a function
  ```

- **Range Error**: When a value is not within the expected range.  
  Example:  
  ```javascript
  const arr = [];
  arr.length = -1; // RangeError: Invalid array length
  ```

---

#### 2. **What is `try...catch` in JavaScript?**  
`try...catch` is used to handle exceptions gracefully without crashing the program.

**Example:**  
```javascript
try {
  const result = 10 / 0;
  console.log(result);
} catch (error) {
  console.error("An error occurred:", error.message);
}
```

---

#### 3. **What is the purpose of the `finally` block in `try...catch`?**  
The `finally` block executes code after the `try` and `catch` blocks, regardless of whether an exception was thrown.

**Example:**  
```javascript
try {
  console.log("Inside try");
} catch (error) {
  console.log("Inside catch");
} finally {
  console.log("Inside finally");
}
// Output: 
// Inside try
// Inside finally
```

---

#### 4. **How do you throw custom errors in JavaScript?**  
Use the `throw` statement to create custom error messages.

**Example:**  
```javascript
function divide(a, b) {
  if (b === 0) {
    throw new Error("Division by zero is not allowed");
  }
  return a / b;
}

try {
  console.log(divide(10, 0));
} catch (error) {
  console.error(error.message); // Division by zero is not allowed
}
```

---

#### 5. **What is the difference between `Error`, `TypeError`, and `RangeError`?**  
- **`Error`**: General error.  
- **`TypeError`**: Occurs when a value is not of the expected type.  
- **`RangeError`**: Occurs when a number is out of its allowed range.

**Examples:**  
```javascript
// General Error
throw new Error("Something went wrong");

// TypeError
null.toString(); // TypeError: Cannot read property 'toString' of null

// RangeError
new Array(-1); // RangeError: Invalid array length
```

---

#### 6. **How do you use `try...catch` with asynchronous code?**  
Use `try...catch` with `async/await` to handle errors in asynchronous code.

**Example:**  
```javascript
async function fetchData() {
  try {
    const response = await fetch("invalid-url");
    const data = await response.json();
    console.log(data);
  } catch (error) {
    console.error("Error fetching data:", error.message);
  }
}

fetchData();
```

---

#### 7. **What is `window.onerror` and how is it used?**  
`window.onerror` is an event handler for catching global JavaScript errors.

**Example:**  
```javascript
window.onerror = function(message, source, lineno, colno, error) {
  console.log("Error message:", message);
  console.log("Source:", source);
  console.log("Line:", lineno);
  console.log("Column:", colno);
  console.log("Error object:", error);
};

console.log(undeclaredVariable); // This will trigger window.onerror
```

---

#### 8. **How do you handle uncaught Promise rejections?**  
Use the `unhandledrejection` event to catch unhandled Promise rejections.

**Example:**  
```javascript
window.addEventListener("unhandledrejection", (event) => {
  console.error("Unhandled rejection:", event.reason);
});

Promise.reject("Something went wrong");
```

---

#### 9. **What are the best practices for error handling in JavaScript?**  
- Always handle errors using `try...catch` for synchronous code.  
- Use `async/await` with `try...catch` for asynchronous code.  
- Validate user inputs and edge cases.  
- Throw custom errors with meaningful messages.  
- Use centralized error logging (e.g., `window.onerror` or monitoring tools).  
- Avoid using `catch` to silently ignore errors; log them instead.

---

#### 10. **What are stack traces, and how do they help in debugging?**  
A **stack trace** shows the sequence of function calls leading to an error. It helps developers identify the exact location of the problem.

**Example:**  
```javascript
function func1() {
  func2();
}

function func2() {
  throw new Error("Something went wrong");
}

try {
  func1();
} catch (error) {
  console.error(error.stack); // Displays the stack trace
}
```

---

Let me know if you'd like to continue to the next topic!
