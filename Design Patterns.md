### **JavaScript Design Patterns: Answers with Examples**

---

#### 1. **What are design patterns in JavaScript?**  
Design patterns are reusable solutions to common problems that occur in software design. In JavaScript, they help in writing maintainable, scalable, and efficient code.

---

#### 2. **What is the Singleton Pattern?**  
The **Singleton Pattern** ensures that a class has only one instance and provides a global access point to that instance.

**Example:**  
```javascript
class Singleton {
  constructor() {
    if (!Singleton.instance) {
      this.value = Math.random();
      Singleton.instance = this;
    }
    return Singleton.instance;
  }
}

const instance1 = new Singleton();
const instance2 = new Singleton();

console.log(instance1 === instance2); // true
```

---

#### 3. **What is the Factory Pattern?**  
The **Factory Pattern** defines an interface for creating objects but allows subclasses to alter the type of objects that will be created.

**Example:**  
```javascript
class Car {
  constructor(model) {
    this.model = model;
  }
}

class CarFactory {
  createCar(model) {
    return new Car(model);
  }
}

const factory = new CarFactory();
const car1 = factory.createCar("Sedan");
const car2 = factory.createCar("SUV");

console.log(car1.model); // Sedan
console.log(car2.model); // SUV
```

---

#### 4. **What is the Observer Pattern?**  
The **Observer Pattern** allows an object (subject) to notify other objects (observers) about changes in its state without knowing who or what those objects are.

**Example:**  
```javascript
class Subject {
  constructor() {
    this.observers = [];
  }
  addObserver(observer) {
    this.observers.push(observer);
  }
  notifyObservers() {
    this.observers.forEach((observer) => observer.update());
  }
}

class Observer {
  update() {
    console.log("State updated!");
  }
}

const subject = new Subject();
const observer1 = new Observer();
subject.addObserver(observer1);

subject.notifyObservers(); // State updated!
```

---

#### 5. **What is the Module Pattern?**  
The **Module Pattern** is used to encapsulate code into a single unit or module to avoid polluting the global scope and to provide a public API.

**Example:**  
```javascript
const counterModule = (function () {
  let count = 0;
  return {
    increment: function () {
      count++;
      console.log(count);
    },
    decrement: function () {
      count--;
      console.log(count);
    },
  };
})();

counterModule.increment(); // 1
counterModule.decrement(); // 0
```

---

#### 6. **What is the Prototype Pattern?**  
The **Prototype Pattern** allows you to create new objects by cloning an existing object, usually by creating a base object and then extending it.

**Example:**  
```javascript
const carPrototype = {
  drive() {
    console.log("Driving...");
  },
  stop() {
    console.log("Stopping...");
  },
};

const car1 = Object.create(carPrototype);
car1.drive(); // Driving...
```

---

#### 7. **What is the Decorator Pattern?**  
The **Decorator Pattern** allows you to add new functionality to an object without altering its structure.

**Example:**  
```javascript
class Car {
  drive() {
    console.log("Driving a car");
  }
}

function addGPS(car) {
  car.gps = function () {
    console.log("GPS activated");
  };
}

const myCar = new Car();
addGPS(myCar);

myCar.drive(); // Driving a car
myCar.gps(); // GPS activated
```

---

#### 8. **What is the Command Pattern?**  
The **Command Pattern** is used to encapsulate a request as an object, allowing for parameterization of clients with queues, requests, and operations.

**Example:**  
```javascript
class Light {
  turnOn() {
    console.log("Light is on");
  }
  turnOff() {
    console.log("Light is off");
  }
}

class Command {
  constructor(light) {
    this.light = light;
  }
  execute() {
    this.light.turnOn();
  }
}

const light = new Light();
const lightOnCommand = new Command(light);
lightOnCommand.execute(); // Light is on
```

---

#### 9. **What is the Adapter Pattern?**  
The **Adapter Pattern** allows you to convert the interface of a class into another interface that clients expect. It’s often used to allow incompatible interfaces to work together.

**Example:**  
```javascript
class OldSystem {
  oldMethod() {
    console.log("Old system method");
  }
}

class NewSystem {
  newMethod() {
    console.log("New system method");
  }
}

class Adapter {
  constructor(oldSystem) {
    this.oldSystem = oldSystem;
  }
  newMethod() {
    this.oldSystem.oldMethod();
  }
}

const oldSystem = new OldSystem();
const adapter = new Adapter(oldSystem);
adapter.newMethod(); // Old system method
```

---

#### 10. **What is the Strategy Pattern?**  
The **Strategy Pattern** defines a family of algorithms and allows the algorithm to be selected at runtime.

**Example:**  
```javascript
class Payment {
  constructor(paymentStrategy) {
    this.paymentStrategy = paymentStrategy;
  }

  executePayment(amount) {
    this.paymentStrategy.pay(amount);
  }
}

class CreditCardPayment {
  pay(amount) {
    console.log(`Paid ${amount} using credit card`);
  }
}

class PayPalPayment {
  pay(amount) {
    console.log(`Paid ${amount} using PayPal`);
  }
}

const creditCardPayment = new CreditCardPayment();
const payPalPayment = new PayPalPayment();

const payment1 = new Payment(creditCardPayment);
payment1.executePayment(100); // Paid 100 using credit card

const payment2 = new Payment(payPalPayment);
payment2.executePayment(200); // Paid 200 using PayPal
```

---

Let me know if you'd like to explore more design patterns or continue with another topic!
