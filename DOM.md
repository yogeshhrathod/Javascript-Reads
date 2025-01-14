### **JavaScript DOM Manipulation: Answers with Examples**

---

#### 1. **What is the DOM (Document Object Model)?**  
The **DOM** is a programming interface for web documents. It represents the page so that programs can manipulate the structure, style, and content dynamically. It treats the page as a tree of nodes, where each node represents part of the page.

---

#### 2. **How do you access an element in the DOM?**  
There are several methods to access DOM elements:
- **`getElementById()`**: Access element by its ID.
- **`getElementsByClassName()`**: Access elements by class name.
- **`getElementsByTagName()`**: Access elements by tag name.
- **`querySelector()`**: Access the first matching element with CSS selectors.
- **`querySelectorAll()`**: Access all matching elements with CSS selectors.

**Example:**  
```javascript
const element = document.getElementById('myElement');
const elements = document.querySelectorAll('.myClass');
```

---

#### 3. **How do you change the content of an element in the DOM?**  
You can use **`innerText`** or **`innerHTML`** to modify an element's content.  
- **`innerText`** modifies the text content (excluding HTML).
- **`innerHTML`** modifies the content including HTML tags.

**Example:**  
```javascript
document.getElementById("myElement").innerText = "New Text";
document.getElementById("myElement").innerHTML = "<strong>Bold Text</strong>";
```

---

#### 4. **How do you add an element to the DOM?**  
You can create a new element using **`createElement()`**, and then append it using **`appendChild()`** or **`insertBefore()`**.

**Example:**  
```javascript
const newDiv = document.createElement("div");
newDiv.innerText = "Hello, World!";
document.body.appendChild(newDiv);
```

---

#### 5. **How do you remove an element from the DOM?**  
You can remove an element using **`removeChild()`** or **`remove()`**.

**Example:**  
```javascript
const element = document.getElementById("myElement");
element.remove(); // Removes the element directly

// Alternatively:
const parent = document.getElementById("parentElement");
parent.removeChild(element); // Removes the element from its parent
```

---

#### 6. **How do you modify an element’s attributes?**  
You can modify attributes using **`setAttribute()`** and retrieve them using **`getAttribute()`**.

**Example:**  
```javascript
const element = document.getElementById("myElement");
element.setAttribute("src", "image.jpg");
const srcValue = element.getAttribute("src");
console.log(srcValue); // image.jpg
```

---

#### 7. **How do you handle events in JavaScript?**  
You can handle events using **`addEventListener()`** to listen for specific events, or **`onclick`**, **`onchange`**, etc., for inline event handling.

**Example with `addEventListener()`:**  
```javascript
document.getElementById("myButton").addEventListener("click", function() {
  alert("Button clicked!");
});
```

---

#### 8. **What is event delegation in JavaScript?**  
**Event delegation** is a technique where you attach a single event listener to a parent element instead of adding it to individual child elements. This improves performance and simplifies event management.

**Example:**  
```javascript
document.getElementById("parentElement").addEventListener("click", function(event) {
  if (event.target && event.target.matches("button.className")) {
    console.log("Button clicked!");
  }
});
```

---

#### 9. **How do you modify CSS styles of an element in JavaScript?**  
You can modify CSS styles directly using the **`style`** property or manipulate classes using **`classList`** methods like **`add()`, `remove()`, `toggle()`**.

**Example:**  
```javascript
document.getElementById("myElement").style.color = "blue";
document.getElementById("myElement").classList.add("newClass");
document.getElementById("myElement").classList.remove("oldClass");
document.getElementById("myElement").classList.toggle("activeClass");
```

---

#### 10. **How do you create animations in JavaScript?**  
You can create animations using the **`requestAnimationFrame()`** method, CSS animations, or JavaScript libraries like **GSAP**.

**Example with `requestAnimationFrame()`:**  
```javascript
let position = 0;
const element = document.getElementById("myElement");

function animate() {
  position += 1;
  element.style.left = position + "px";

  if (position < 300) {
    requestAnimationFrame(animate); // Keep animating
  }
}

animate();
```

---

#### 11. **What is `localStorage` and `sessionStorage`?**  
- **`localStorage`**: Stores data with no expiration time, even after the browser is closed.
- **`sessionStorage`**: Stores data for the duration of the page session. It is cleared when the page is closed.

**Example:**  
```javascript
localStorage.setItem("username", "John");
sessionStorage.setItem("sessionId", "12345");

console.log(localStorage.getItem("username")); // John
console.log(sessionStorage.getItem("sessionId")); // 12345
```

---

Let me know if you'd like more details or want to move to the next topic!
