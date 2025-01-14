### **Asynchronous JavaScript: Answers with Examples**

---

#### 1. **Explain the difference between `setTimeout` and `setInterval`.**  
- **`setTimeout`**: Executes a function after a specified delay (only once).  
- **`setInterval`**: Executes a function repeatedly at specified intervals.  

**Example of `setTimeout`:**  
```javascript
setTimeout(() => {
  console.log("Executed after 2 seconds");
}, 2000);
```

**Example of `setInterval`:**  
```javascript
setInterval(() => {
  console.log("Executed every 1 second");
}, 1000);
```

---

#### 2. **What is the event loop in JavaScript?**  
The **event loop** is a mechanism that allows JavaScript to handle asynchronous operations by managing the call stack, task queue, and microtask queue, ensuring non-blocking behavior.

**Example Demonstrating the Event Loop:**  
```javascript
console.log("Start");

setTimeout(() => {
  console.log("Timeout");
}, 0);

Promise.resolve().then(() => {
  console.log("Promise resolved");
});

console.log("End");
```

**Output:**  
```
Start  
End  
Promise resolved  
Timeout  
```

Explanation:  
- Synchronous code runs first (`Start`, `End`).
- Promises (microtasks) run before `setTimeout` (macrotasks).

---

#### 3. **What are Promises in JavaScript?**  
A **Promise** represents the eventual completion (or failure) of an asynchronous operation and its resulting value.

**States of a Promise:**  
- **Pending**: Initial state, neither fulfilled nor rejected.  
- **Fulfilled**: Operation completed successfully.  
- **Rejected**: Operation failed.

**Example of a Promise:**  
```javascript
const fetchData = new Promise((resolve, reject) => {
  setTimeout(() => {
    resolve("Data fetched successfully");
  }, 2000);
});

fetchData.then((data) => {
  console.log(data); // "Data fetched successfully"
});
```

---

#### 4. **What is `async/await` and how is it different from Promises?**  
`async/await` is syntactic sugar over Promises, making asynchronous code easier to read and write.

**Example using Promises:**  
```javascript
function fetchData() {
  return new Promise((resolve) => {
    setTimeout(() => {
      resolve("Data fetched");
    }, 2000);
  });
}

fetchData().then((data) => console.log(data));
```

**Example using `async/await`:**  
```javascript
async function fetchData() {
  const data = await new Promise((resolve) => {
    setTimeout(() => {
      resolve("Data fetched");
    }, 2000);
  });
  console.log(data);
}

fetchData();
```

---

#### 5. **What is the difference between `Promise.all` and `Promise.race`?**  
- **`Promise.all`**: Resolves when all Promises are resolved or rejects if any Promise fails.  
- **`Promise.race`**: Resolves or rejects as soon as the first Promise settles.

**Example of `Promise.all`:**  
```javascript
const p1 = Promise.resolve(1);
const p2 = Promise.resolve(2);
const p3 = Promise.resolve(3);

Promise.all([p1, p2, p3]).then((values) => {
  console.log(values); // [1, 2, 3]
});
```

**Example of `Promise.race`:**  
```javascript
const p1 = new Promise((resolve) => setTimeout(() => resolve(1), 1000));
const p2 = new Promise((resolve) => setTimeout(() => resolve(2), 500));

Promise.race([p1, p2]).then((value) => {
  console.log(value); // 2
});
```

---

#### 6. **Explain the difference between microtasks and macrotasks.**  
- **Microtasks**: Include Promises and `queueMicrotask`. They are executed before the next macrotask.  
- **Macrotasks**: Include `setTimeout`, `setInterval`, and I/O operations.

**Example:**  
```javascript
console.log("Start");

setTimeout(() => {
  console.log("Macrotask: Timeout");
}, 0);

Promise.resolve().then(() => {
  console.log("Microtask: Promise");
});

console.log("End");
```

**Output:**  
```
Start  
End  
Microtask: Promise  
Macrotask: Timeout  
```

---

Let me know if you'd like more details or examples!
