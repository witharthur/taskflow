Interview Questions:


### **1. How do you select elements in the DOM?**
document.getElementById('id');
document.getElementsByClassName('class');
document.getElementsByTagName('div');
document.querySelector('.class');
document.querySelectorAll('.class');

### **2. What are event listeners?**
An **event listener** waits for a specific user action (like a click, keypress, or scroll) and runs a function when that event occurs.
element.addEventListener('click', () => {
  console.log('Button clicked!');

### 3. Explain Event Delegation
Event delegation is a technique in JavaScript where instead of adding event listeners to multiple child elements, you add a single event listener to their parent element. The event listener uses **event bubbling** to catch events from child elements. This approach improves performance and simplifies code, especially when dealing with dynamically added elements.
document.querySelector('#list').addEventListener('click', function(event) {
  if (event.target.tagName === 'LI') {
    console.log('You clicked on:', event.target.textContent);
  }
});

### 4. How do you prevent default behavior in JS?
In JavaScript, you can prevent the default behavior of an event (such as a form submission or a link navigation) by using the **`event.preventDefault()`** method.  
This stops the browser from executing the default action associated with that event.
document.querySelector('form').addEventListener('submit', function(event) {
  event.preventDefault(); // Prevents the form from submitting
  console.log('Form submission stopped!');
});

### 5. What is the difference between var, let, and const?
`var`, `let`, and `const` are used to declare variables in JavaScript, but they differ in **scope**, **re-declaration**, **re-assignment**, and **hoisting**:
- **`var`**  
  - Scope: Function-scoped  
  - Re-declaration: Allowed  
  - Re-assignment: Allowed  
  - Hoisting: Hoisted and initialized as `undefined`  
  - Notes: Can cause unexpected behavior due to hoisting  
- **`let`**  
  - Scope: Block-scoped  
  - Re-declaration: Not allowed  
  - Re-assignment: Allowed  
  - Hoisting: Hoisted but not initialized  
  - Notes: Use for variables that will change  
- **`const`**  
  - Scope: Block-scoped  
  - Re-declaration: Not allowed  
  - Re-assignment: Not allowed  
  - Hoisting: Hoisted but not initialized  
  - Notes: Use for constants or variables that should not be reassigned  

var a = 1;
let b = 2;
const c = 3;

a = 10; // Works
b = 20; // Works
c = 30; // Error - cannot reassign const


### 6. How does bubbling and capturing work in events?
In JavaScript, when an event occurs in the DOM, it goes through **three phases**: **capturing**, **target**, and **bubbling**.

1. **Capturing Phase (Event Capturing):**  
   The event starts from the root (`window` or `document`) and travels **down** through parent elements until it reaches the target element.
2. **Target Phase:**  
   The event reaches the exact element (target) that triggered the event.
3. **Bubbling Phase (Event Bubbling):**  
   After reaching the target, the event bubbles **up** through its ancestors back to the root.
By default, most event listeners in JavaScript use **bubbling**.  
You can enable **capturing** by passing `true` as the third argument in `addEventListener`.
document.querySelector('#parent').addEventListener('click', () => {
  console.log('Parent clicked!');
}, false); // Bubbling phase

document.querySelector('#child').addEventListener('click', () => {
  console.log('Child clicked!');
}, true); // Capturing phase

### 7. How do you add and remove classes in JS?
In JavaScript, you can manipulate CSS classes of an element using the `classList` property. This allows you to add, remove, toggle, or check for classes easily.
- `element.classList.add('className')` → Adds one or more classes.  
- `element.classList.remove('className')` → Removes one or more classes.  
- `element.classList.toggle('className')` → Adds the class if it doesn’t exist, removes it if it does.  
- `element.classList.contains('className')` → Returns `true` if the element has the specified class.

const box = document.querySelector('.box');
// Add a class
box.classList.add('active');
// Remove a class
box.classList.remove('hidden');
// Toggle a class
box.classList.toggle('highlight');
// Check if a class exists
if (box.classList.contains('active')) {
  console.log('The box is active!');
}

### 8. What is closure in JavaScript?
A **closure** is a function that has access to its own scope, the scope of its outer function, and the global scope, even after the outer function has finished executing. Closures allow functions to "remember" the environment in which they were created.
- A closure gives access to variables from an outer function even after that function has returned.  
- Useful for data privacy, creating private variables, and maintaining state.  
function outerFunction() {
  let count = 0;

  return function innerFunction() {
    count++;
    console.log('Count:', count);
  };
}

const increment = outerFunction();

increment(); // Count: 1
increment(); // Count: 2
increment(); // Count: 3

### 9. Explain arrow functions
Arrow functions are a concise syntax for writing functions in JavaScript, introduced in ES6. They are especially useful for short functions and callbacks.
- Shorter syntax compared to traditional functions.  
- Do **not** have their own `this`, `arguments`, or `super`—they inherit `this` from the surrounding scope.  
- Cannot be used as constructors.  

// Traditional function
function add(a, b) {
  return a + b;
}
// Arrow function
const add = (a, b) => a + b;
// Arrow function with single parameter
const square = x => x * x;
// Arrow function with multiple statements
const multiplyAndLog = (a, b) => {
  const result = a * b;
  console.log(result);
  return result;
};

### 10. What is the difference between == and ===?
In JavaScript, `==` and `===` are used to compare values, but they behave differently:
- **`==` (Equality Operator)**  
  - Compares values **after type coercion**.  
  - Converts the operands to the same type before comparing.  
  - Can lead to unexpected results if types are different.
- **`===` (Strict Equality Operator)**  
  - Compares values **without type coercion**.  
  - Returns `true` only if both the value **and** type are the same.  
  - Safer and recommended in most cases.