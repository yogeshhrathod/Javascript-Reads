### **Closures: Answers with Examples**

---

#### 1. **What is a closure in JavaScript?**  
A closure is a function that has access to its own scope, the scope of the outer function, and the global scope, even after the outer function has executed.  

**Example:**  
```javascript
function outerFunction() {
  let outerVariable = "I'm from outer scope!";
  
  function innerFunction() {
    console.log(outerVariable); // Accessing outer scope variable
  }
  
  return innerFunction;
}

const closureExample = outerFunction();
closureExample(); // Output: "I'm from outer scope!"
```

---

#### 2. **Explain how closures work with an example.**  
Closures capture variables from their outer scope and retain them in memory.  

**Example:**  
```javascript
function counter() {
  let count = 0; // Outer variable
  return function() {
    count++;
    console.log(count);
  };
}

const increment = counter();
increment(); // 1
increment(); // 2
increment(); // 3
```

Here, the `count` variable persists between calls to `increment` because of the closure.

---

#### 3. **What are some practical use cases of closures?**  
1. **Data encapsulation (private variables):**  
   ```javascript
   function createCounter() {
     let count = 0;
     return {
       increment: () => ++count,
       decrement: () => --count,
       getCount: () => count
     };
   }

   const myCounter = createCounter();
   console.log(myCounter.increment()); // 1
   console.log(myCounter.getCount());  // 1
   ```

2. **Event listeners:**  
   ```javascript
   function attachHandler(message) {
     document.getElementById("btn").addEventListener("click", function() {
       console.log(message); // Closure retains `message`
     });
   }

   attachHandler("Button clicked!");
   ```

---

#### 4. **How do closures help in data encapsulation?**  
Closures allow you to create private variables by keeping them inaccessible from the global scope.  

**Example:**  
```javascript
function secretHolder() {
  let secret = "This is a secret!";
  
  return {
    getSecret: function() {
      return secret;
    },
    setSecret: function(newSecret) {
      secret = newSecret;
    }
  };
}

const holder = secretHolder();
console.log(holder.getSecret()); // "This is a secret!"
holder.setSecret("New secret!");
console.log(holder.getSecret()); // "New secret!"
```

---

#### 5. **Explain the concept of the lexical scope in the context of closures.**  
Lexical scope means that a function's scope is determined by its physical location in the code. Closures rely on lexical scope to access variables from the outer function.  

**Example:**  
```javascript
function outer() {
  let name = "Lexical Scope Example";
  
  function inner() {
    console.log(name); // Accessing the outer variable due to lexical scope
  }
  
  return inner;
}

const innerFunction = outer();
innerFunction(); // "Lexical Scope Example"
```

---

#### 6. **How can closures lead to memory leaks?**  
Closures can lead to memory leaks if references to outer variables are retained unnecessarily, preventing garbage collection.  

**Example of a potential memory leak:**  
```javascript
function createLeak() {
  const largeObject = new Array(1000000).fill("data");
  return function() {
    console.log(largeObject.length); // Closure holds reference to `largeObject`
  };
}

const leakyFunction = createLeak();
// The large object remains in memory as long as `leakyFunction` exists.
```

---

#### 7. **How can closures be used to implement private variables?**  
Private variables can be created by enclosing them in a function scope and providing controlled access through closures.  

**Example:**  
```javascript
function bankAccount(initialBalance) {
  let balance = initialBalance; // Private variable
  
  return {
    deposit: function(amount) {
      balance += amount;
      return balance;
    },
    withdraw: function(amount) {
      if (amount <= balance) {
        balance -= amount;
        return balance;
      } else {
        return "Insufficient funds";
      }
    },
    getBalance: function() {
      return balance;
    }
  };
}

const myAccount = bankAccount(1000);
console.log(myAccount.deposit(500));  // 1500
console.log(myAccount.withdraw(200)); // 1300
console.log(myAccount.getBalance());  // 1300
```

This ensures that the `balance` variable is only accessible through the methods provided.
