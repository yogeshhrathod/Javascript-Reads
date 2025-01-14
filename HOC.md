### **Higher-Order Functions (HOC): Answers with Examples**

---

#### 1. **What is a Higher-Order Function (HOC) in JavaScript?**  
A Higher-Order Function is a function that either:  
- Takes another function as an argument, or  
- Returns a function as its result.  

**Example:**  
```javascript
function withLogging(fn) {
  return function(...args) {
    console.log(`Calling function ${fn.name} with arguments:`, args);
    return fn(...args);
  };
}

function add(a, b) {
  return a + b;
}

const loggedAdd = withLogging(add);
console.log(loggedAdd(3, 5)); // Logs info, then outputs 8
```

---

#### 2. **Give examples of built-in HOCs in JavaScript.**  
1. **`map`**  
   ```javascript
   const numbers = [1, 2, 3];
   const squared = numbers.map((n) => n * n);
   console.log(squared); // [1, 4, 9]
   ```

2. **`filter`**  
   ```javascript
   const numbers = [1, 2, 3, 4, 5];
   const even = numbers.filter((n) => n % 2 === 0);
   console.log(even); // [2, 4]
   ```

3. **`reduce`**  
   ```javascript
   const numbers = [1, 2, 3, 4];
   const sum = numbers.reduce((acc, n) => acc + n, 0);
   console.log(sum); // 10
   ```

---

#### 3. **How do HOCs differ from regular functions?**  
- **HOCs** operate on other functions, enhancing or modifying their behavior.  
- **Regular functions** typically operate on data.

**Example of HOC:**  
```javascript
function multiplyBy(factor) {
  return function(number) {
    return number * factor;
  };
}

const double = multiplyBy(2);
console.log(double(5)); // 10
```

---

#### 4. **Write a simple HOC that takes a function and returns a new function with additional behavior.**  
**Example: A timing HOC**  
```javascript
function measureExecutionTime(fn) {
  return function(...args) {
    const start = performance.now();
    const result = fn(...args);
    const end = performance.now();
    console.log(`Execution time: ${end - start} ms`);
    return result;
  };
}

function slowFunction(num) {
  for (let i = 0; i < 1e6; i++) {} // Simulate slow work
  return num * 2;
}

const timedFunction = measureExecutionTime(slowFunction);
console.log(timedFunction(10)); // Logs execution time, then outputs 20
```

---

#### 5. **What are the advantages of using HOCs in programming?**  
- **Code reusability**: Encapsulate common logic in reusable functions.  
  ```javascript
  function withErrorHandling(fn) {
    return function(...args) {
      try {
        return fn(...args);
      } catch (error) {
        console.error("Error occurred:", error);
      }
    };
  }

  const safeParse = withErrorHandling(JSON.parse);
  console.log(safeParse('{"valid": "json"}')); // Works fine
  console.log(safeParse("invalid json")); // Catches and logs error
  ```

- **Improved readability**: Break down complex logic into smaller functions.  
- **Enhance existing functions**: Add logging, timing, or caching.  

---

#### **Real-World Example: HOC in React**  
In React, HOCs are used to enhance components.  
```javascript
function withAuthentication(Component) {
  return function WrappedComponent(props) {
    if (!props.isAuthenticated) {
      return <div>Please log in.</div>;
    }
    return <Component {...props} />;
  };
}

function Dashboard(props) {
  return <div>Welcome to the Dashboard, {props.user}!</div>;
}

const ProtectedDashboard = withAuthentication(Dashboard);
```

Let me know if you'd like further examples or clarification!
