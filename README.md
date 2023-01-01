# 📝 JS Interview Questions.

## Day 1️⃣
</br>

### Q.1) Difference between “ == “ and “ === “ operators.

---

JavaScript provides both **Strict Equality Comparison** (===, !==) and **Loose Equality Comparison** (==, !=). The strict operators take type of variable in consideration, while non-strict operators make type correction/conversion based upon values of variables. The strict operators follow the below conditions for different types,

1. Two strings are strictly equal when they have the same sequence of characters, same length, and same characters in corresponding positions.
3. Two numbers are strictly equal when they are numerically equal. i.e, Having the same number value. There are two special cases in this,
   i. `NaN` is not equal to anything, including `NaN`.
   ii. Positive and negative zeros are equal to one another.
4. Two Boolean operands are strictly equal if both are true or both are false.
5. Two objects are strictly equal if they refer to the same Object.
6. `Null` and `Undefined` types are not equal with ===, but equal with ==. i.e, `null` === `undefined` --> false but `null` == `undefined` --> true

Some of the example which covers the above cases,

   `0` == `false   // true` 
   `0` === `false  // false` 
   `1` == `"1"     // true` 
   `1` === `"1"    // false` 
   `null` == `undefined // true` 
   `null` === `undefined // false` 
   `'0'` == `false // true` 
   `'0'` === `false // false`
   `[]`==`[]` or `[]`===`[] //false`, refer different objects in memory 
   `{}`==`{}` or `{}`===`{} //false`, refer different objects in memory
</br>

### Q.2) What is the spread operator ?

---

1. It is defined by using `…` (Three dots). It allows us to de-structure the non-primitive data type in JS.
2. It was introduced in ES6 by ECMA International in 2015.
3. `const a = [1,2,3], b = a;` here, the memory location is passed into var `'b'` as it is defined by memory reference, so if we update `'a'` after defining `'b'` the value of `'a'` as well as ‘b’ will get updated. So, to avoid this also we use spread operator. Like `b = […a];` which will create a separate copy of `'a'` in `'b'` with values of `'a'` and won't update after updating `'a'` .
4. `...rest` is also a operator, in contrast with spread operator the rest operator is used to construct a non-primitive datatype like *array*. In above example we can use rest operator to create a separate variables as values of *array* a by using, `const [x,y,…rest] = a`. Here, *array* values get constructed as separate variables.
5. ```js
   const	arr1 = [1,2,3], arr2 = [5,6,7];
   let firstarr = …arr1;
   let secondarr = …arr2;
   let combinedarr = […arr1, …arr2];
   //it can be also used to separate each element form array and use it store in another element.
   ```
</br>

### Q.3) What are the differences between var, let and const ?

---

In JavaScript, users can declare a variable using **3 keywords** that are `var`, `let`, and `const`. var is the oldest keyword of the three. let and const were introduced in ES6 in year 2015.
- var declarations are globally scoped or function scoped while let and const are block scoped.
- var variables can be updated and re-declared within its scope; let variables can be updated but not re-declared; const variables can neither be updated nor re-declared.
- They are all hoisted to the top of their scope. But while var variables are initialized with undefined, let and const variables are not initialized.
- While var and let can be declared without being initialized, const must be initialized during declaration.
</br>

### Q.4) What is execution context ?

---

1. All JavaScript code needs to be hosted and run in some kind of environment. In most cases, that environment is be a web browser.
2. The browser's JavaScript engine then creates a special environment to handle the transformation and execution of this JavaScript code. This environment is known as the `Execution Context` . Or it can also be defined as, in JavaScript the environment that enables the JavaScript code to get executed is what we call  **JavaScript Execution Context** .
3. It is the execution context that decides which code section has access to the `functions`, `variables`, and `objects` used in the code. During the Execution Context run-time, the specific code gets parsed by a parser, the `variables` and `functions` are stored in memory, executable byte-code gets generated, and the code gets executed.
4. There are **3** types of Execution contexts in JS -
   1. `<u>`**Global Execution context/GEC** `</u>` - This is the default execution context in which JS code start its execution when the file first loads in the browser. All of the global code i.e. code which is not inside any function or object is executed inside the global execution context. GEC cannot be more than one because only one global environment is possible for JS code execution as the JS engine is single threaded.
   2. `<u>`**Functional Execution context/FEC** `</u>` - Functional execution context is defined as the context created by the JS engine whenever it finds any function call. Each function has its own execution context. It can be more than one. Functional execution context has access to all the code of the global execution context though vice versa is not applicable. While executing the global execution context code, if JS engine finds a function call, it creates a new functional execution context for that function.
   3. `<u>`**Eval Execution context** `</u>` - Execution context inside `eval` function.
5. **Execution context stack (ECS)** - Execution context stack is a stack data structure, i.e. last in first out data structure, to store all the execution stacks created during the life cycle of the script. Global execution context is present by default in execution context stack and it is at the bottom of the stack. While executing the global execution context code, if JS engines find a function call, it creates a functional execution context for that function and pushes it on top of the execution context stack. JS engine executes the function whose execution context is at the top of the execution context stack. Once all the code of the function is executed, JS engines pop out that function’s execution context and start’s executing the function which is below it.
</br>

### Q.5) What is meant by first class functions ?

---

In Javascript, functions are first class objects. A function is said to be a First-class function when it is treated as a varible in that language.

For example, in such a language, a function can be passed as an argument to other functions, can be returned by another function and can be assigned as a value to a variable. In the example below, handler functions assigned to a listener
```js
const handler = () => console.log("This is a click handler function");
document.addEventListener("click", handler);
//Output will print message after the click on button.
```
</br>

### Q.6) What are closures? Give an example of closure.

---

A **closure** is the combination of a function and the lexical environment within which that function was declared. i.e, It is an inner function that has access to the outer or enclosing function’s variables. The closure has three scope chains.
  i. Own scope where variables defined between its curly brackets
  ii. Outer function’s variables
  iii. Global variables.

Here's an example that explains closure concept,
```js
function Welcome(name) {
   var greetingInfo = function (message) {
      console.log(message + " " + name);
      };
      return greetingInfo;
   }
var myFunction = Welcome("John");
myFunction("Welcome "); //Output: Welcome John
myFunction("Hello Mr."); //output: Hello Mr.John
```

As per the above code, the inner function(i.e, greetingInfo) has access to the variables in the outer function scope(i.e, Welcome) even after the outer function has returned.
</br>

### Q.7) Explain call(), apply() and, bind() methods. Give one example of each methods.

---

> **`call()`** : In JS every function has access to some special methods/functions which are available & can be, `call()` method is also a one of those special functions/methods. We use call method to call the function and pass them different objects/datatypes , like we borrow a function to use elesewhere. When using call method we can pass multiple arguments with it, but the first argument must be the refference of the object or function and after that each and every arguments which is required to be passed to the function will be passed individually separated by comma.
   ```js
   let name = {
    firstName: "abc",
    lastName: "xyz",
}
let printFullName = function (){
    console.log(this.firstName + " " + this.lastName);
}

printFullName.call(name);
   ```
> **`apply()`** : Apply method is similar to the call method, with only one difference which is, all arguments required by the function must be passed in an array list.
   ```js
let printFullDeatails = function (age, city){
   console.log("Age of " + this.firstName + " " + this.lastName + " is " + age + " and he lives in " + city)
}

printFullDetails.apply(name, [30, "Mumbai"]);
   ```
> **`bind()`** : It's similar to the `call()` method but instead of calling the function right over it will create a copy of it and will return that function, and that new function , we can call at anytime and anywhere.
   ```js
   const newFun = displayUserDetails.bind(name, company, designation);
   newFun("Infosys", "Tester");
   ```
</br>


## Day 2️⃣
</br>

### Q.8) What is creation phase and execution phase ?

---

</br>

### Q.9) What are objects in javascript ?

---

</br>

### Q.10) What are function constructors ?

---

</br>

### Q.11) What are callbacks ?

---

</br>

### Q.12) Explain Prototypes in JS.

---

</br>

### Q.13) What is prototype chaining in JS.

---

</br>

### Q.14) Give an example of inheritance using function constructor.

---

</br>

## Day 3️⃣
</br>

### Q.15) How many operators do we have in JS ?

---

</br>

### Q.16) What are arrow functions ?

---

</br>

### Q.17) What is the difference between `undefined` vs `not defined` vs `NaN` in JS.

---

</br>

### Q.18) What is callback hell ?

---

</br>

### Q.19) Please explain Self Invoking Function and write it's code.

---

</br>

### Q.20) What is the use of `setTimeout` ?

---

</br>

## Day 4️⃣
</br>

### Q.21) Explain Local Scope, Block Scope, Functional Scope and Scope Chain in javascript.

---

</br>

### Q.22) What is difference between null and undefined ?

---

</br>

### Q.23) What is an event loop and call stack ?

---

</br>

### Q.24) What are promises and why do we need them ?

---

</br>

### Q.25) What is promise chaining in JS.

---

</br>

### Q.26) What are pure functions ?

---

</br>

## Day 5️⃣
</br>

### Q.27) What is hoisting in JS ?

---

</br>

### Q.28) What is a Temporal Dead Zone in JS ?

---

</br>

### Q.29) What is DOM ?

---

</br>

### Q.30) Explain passed by value and passed by reference in JS.

---

</br>

### Q.31) Write code to explain `map` and `filter` in JS arrays.

---

</br>

### Q.32) What is the purpose of async/await keywords in JS ?

---

</br>

### Q.33) Give an example of async/await

---

</br>


## Day 6️⃣
</br>

### Q.34) Create a button , on click of which new Heading tag h1 should be added with text as "MERN stack" on the screen above button.

---

```code
```

</br>

### Q.35) Write code to get 1st H1 element from a webpage using DOM.

---

We can select the first H1 element using DOM with help of `document.querryselector("h1");`.

</br>

### Q.36) Write code to implement timer clock using JS -- display HH:MM:SS -- the time should keep updating every second.

---

</br>

### Q.37) Create an HTML page having content as Hello world and a button named Replace Text. When user will click on this button page content should be changed to "Welcome to Elevation academy"

---

</br>

### Q.38) Create an HTML page having content as Hello world and a button named "Hide Text." When user will click on this button hide the "Hello World" text.

---

</br>