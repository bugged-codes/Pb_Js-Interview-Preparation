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

In Javascript, everything goes though execution context. When the JavaScript engine scans a script file, it makes an environment called the **Execution Context** that handles the entire transformation and execution of the code. During the context runtime, the parser parses the source code and allocates memory for the variables and functions. The source code is generated and gets executed. There are 2 phases of javascript execution context:
1. **Creation Phasse/Memory Allocation Phase :** In this phase, the JavaScript engine creates the execution context and sets up the script's environment. It determines the values of variables and functions and sets up the scope chain for the execution context. In genreal 3 things happen in creation phase:
   1. JS engine reates a global object that is `window` in the browser and `global` in NodeJs.
   2. JS engine sets up a memory for storing variables and functions.
   3. JS engine Stores the variables with values as undefined and function references.
2. **Execution Phase :** In this phase, the JavaScript engine executes the code in the execution context. It processes any statements or expressions in the script and evaluates any function calls line by line form top to bottom of code.
</br>

### Q.9) What are objects in javascript ?

---
In JavaScript **Objects** may be defined as an unordered collection of related data, of primitive or reference types, in the form of “key: value” pairs. These keys can be variables or functions and are called properties and methods, respectively, in the context of an object.
An object can be created with figure brackets {…} with an optional list of properties. A property is a “key: value” pair, where a key is a string (also called a “property name”), and the value can be anything.</br>
In simple words a javaScript object is an entity having *state and behavior* (properties and method). For example: car, pen, bike, chair, glass, keyboard, monitor etc. JavaScript is an object-based language. **Everything is an object in JavaScript**. JavaScript is template based not class based. Here, we don't create class to get the object. But, we direct create objects.
</br>

### Q.10) What are function constructors ?

---

The `Function()` constructor creates a new Function object with the use of **`new`** keyword. Function objects created with the Function constructor are parsed when the function is created. This is less efficient than creating a function with a function expression or function declaration and calling it within your code, because such functions are parsed with the rest of the code. In JavaScript, when `this` keyword is used in a constructor function, `this` refers to the object when the object is created. 
```js
// constructor function
function Person (name, age) {
    this.name = name,
    this.age = age
    this.greet = function (){
      return ("Hi" + " " + this.name)
    }
}

// create an object
const person = new Person("abc", 20);

// Accessing Properties
console.log(perosn.name);
console.log(person.greet());
```
</br>

### Q.11) What are callbacks ?

---

As Javascript is a *synchronous, single-threaded just in time compiled language*, and every thing in js has to go through ***Execution context*** which has only one thread to run the entire code. So, if we know that a perticular function in JS is gonna take more time to compute, then it might halt the entire thread from running. To avoid this thread-blocking we use asynchronous side of JS to get our work done while other functions are done executing. Callbacks are also needed because javascript is an event driven language. That means instead of waiting for a response javascript will keep executing while listening for other events.</br>
In JS callbacks are nothing but a function passed inside another function as a parameter. All the functions in JS are **First-Class Functions** which allows for this to happen in JS. This callback function will run after execution of outer function, which is asynchronous side of Javascript. Some of the predefined callback functions are setTimeOut(), addEventListener() etc.
```js
setTimeout(function one(){
   console.log("5 seconds are over");
}, 5000)

function two(three){
   three();
   console.log("Function 2 executed!");
}

two(function three(){
  console.log("Function 3 completed");
});
```
</br>

### Q.12) Explain Prototypes in JS.

---

In JavaScript, every function and object has a property named **prototype** by default as it is a *prototype-based language* that facilitates the objects to acquire properties and features from one another. Here, each object contains a prototype object. In JavaScript, whenever a function is created the prototype property is added to that function automatically. This property is a *prototype object* that holds a constructor property where we can attach methods and properties in a prototype object, which enables all the other objects to inherit these methods and properties.</br>
Whenever an object is created in JavaScript, its corresponding functions are loaded into memory. So, a new copy of the function is created on each object creation. In a prototype-based approach, all the objects share the same function. This ignores the requirement of creating a new copy of function for each object. Thus, the functions are loaded once into the memory.
</br>

### Q.13) What is prototype chaining in JS.

---

Every object in JavaScript can be linked to a prototype object which is the mechanism through which inheritance is provided.Ther exists a property `--proto__` that allows us to see the prototype an object is pointing to. When a property or method is called on an object JS engine will check it inside object for it's defination, if the object doesn’t contain it, the JS engine will then look to the object’s prototype to resolve the property or method. If an object doesn’t contain a property or method, the JavaScript engine will continue up the prototype chain to try and resolve it. In JavaScript, all functions have a Prototype property and all objects have a `__proto__` property that points to the prototype of their constructor function. The prototype on object instance is available through `Object.getPrototypeOf(object)` or *`__proto__`* property whereas prototype on constructors function is available through `Object.prototype`. </br>
**Prototype Chaining** is used to build new types of objects based on existing ones. It is similar to inheritance in a class based language. Prototype object has a prototype of its own, and so on until an object is reached with null as its prototype. By definition, null has no prototype, and acts as the final link in this prototype chain.
```js
function Car(color, hp){
   this.color = color;
   this.hp = hp;
}
Car.prototype.works = () => true;

let car1 = new Car("White", 10);

Car.prototype.doors = 4

let car2 = new Car("Blue", 25,);
car2.doors = 2;

let getproto = Object.getPrototypeOf(car1);

console.log(getproto); // Car { works: [Function], doors: 4 }
console.log(car1); // Car { color: 'White', hp: 10 }
console.log(car2); // Car { color: 'Blue', hp: 25, doors: 2 }
```
</br>

### Q.14) Give an example of inheritance using function constructor in JS.

---

Inheriting a previously defined *constructor function* means using the *parameters* of the previously defined function along with adding some new parameters to the newly defined constructor function. For this, we need to use the `call()` function which allows us to call a function defined somewhere else in the current context. </br>
In below given example we can observe that the constructor function of Employee is inherited to create a new constructor function Developer which can be used to create objects with new properties along with the inherited properties of the parent constructor.
```js
function Employee(name, age, gender, id) {
   this.name = name;
   this.age = age;
   this.gender = gender;
   this.id = id;
};

function Developer(name, age, gender, id, specialization) {
  
   // Calling Employee constructor function
   Employee.call(this, name, age, gender, id);
  
   // Adding a new parameter
   this.specialization = specialization;
};
  
// Creating objects
let Employee1 = new Employee("Suraj", 28, "Male", 564);
let Developer1 = new Developer("Karishma", 31, "Female", 345, "Frontend Developer");
console.log(Employee1); // Employee {name: 'Suraj', age: 28, gender: 'Male', id: 564}
console.log(Developer1); // Developer {name: 'Karishma', age: 31, gender: 'Female', id: 345, 
```
</br>

## Day 3️⃣
</br>

### Q.15) How many operators do we have in JS ?

---

An *expression* is a valid unit of code that resolves to a value. There are two types of expressions: those that have side effects (such as assigning values) and those that purely *evaluate*. e.g.
>X = 7 is an example of first type. This expression uses the `=` *operator* to assign the *value* seven to the *variable* `x`. The expression itself evaluates to 7.

>3 + 4 is an example of second type. This expression uses the `+` *operator* to add 3 and 4 together and produces a *value*, 7.

JS supports multiple types of variables, which are as follows:
1. **Arithmetic Operators :** An arithmetic operator takes numerical values (either literals or variables) as their operands and returns a single numerical value. In addition to standard arithmetic operators JS also provides certain additional operators.
> `+` (Addition),  `-` (Subtraction),  `*` (Multiplication),  `/` (Division),  `%` (Remainder),  `++` (Increment),  `--` (Decrement),  `**` (Exponential Operator)

</br>

2. **Assignment Operator :** An assignment operator assigns a value to its left operand based on the value of its right operand.
> `=` Equal to assignment operator.

</br>

3. **Comparison Operator :** A comparison operator compares its operands and returns a logical value based on whether the comparison is true. The operands can be numerical, string, logical, or object values.
> `==` (Loose equality),  `===` (Strict equality),  `!=` (Not equal),  `!==` (Strictly Not equal),  `<` (Less than), `<=` (Less than or Equal to),  `>` (Greater than),  `>=` (Greater than or Equal to)

</br>

4. **Bitwise Operator :** A bitwise operator treats their operands as a set of 32 bits (zeros and ones), rather than as decimal, hexadecimal, or octal numbers. For example, the decimal number nine has a binary representation of 1001. Bitwise operators perform their operations on such binary representations, but they return standard JavaScript numerical values.
> `&` (Bitwise AND),  `|` (Bitwise OR),  `^` (Bitwise XOR),  `~` (Bitwise NOT)

</br>

5. **Logical Operator :** Logical operators are typically used with *Boolean* (logical) values as they return a *Boolean* value.
> `&&` (Logical AND),  `||` (Logical OR),  `!` (Logical NOT)

</br>

6. **Conditional (ternary) Operator :** The conditional operator is the only JavaScript operator that takes three operands. The operator can have one of two values based on a condition. The syntax is: `condition ? value1 : value2`

</br>

7. **Special Operators :** These operators are additonal operators that JS provides.
> `delete` (Delete Operator which deletes property of an Object),  `typeof` (Typeof Operator which returns the type of an operand),  `void` (Void Operator specifies an expression to be evaluated without returning a value.),  `in` (In operator it returns true if the specified property is in the specified object.),  `this` (We use the this keyword to refer to the current object. In general, this refers to the calling object in a method. Must use this either with the dot or the bracket)

</br>

8. **`()` Grouping Operator :** The grouping operator `( )` controls the precedence of evaluation in expressions.

</br>

### Q.16) What are arrow functions ?

---

The **Arrow Functions** were introduced in *ES6* version of *ECMA Script* in 2015 provides a concise way to write functions in JavaScript. It is nothing but, a shorter syntax for a anonymous function expression and does not have its own this, arguments, super, or new.target. These functions are best suited for non-method functions, and they cannot be used as constructors. Another significant advantage it offers is the fact that it does not bind its own this. In other words, the context inside arrow functions is lexically or statically defined.
</br>
Limitations on arrow functions are as follows:
 - Arrow functions don't have their own bindings to `this`, `arguments`, or `super`, and should not be used as `methods`.
 - Arrow functions cannot be used as `constructors`. Calling them with `new` throws a TypeError. They also don't have access to the `new.target` keyword.
 - Arrow functions cannot use `yield` within their body and cannot be created as generator functions.
 - The parentheses can only be omitted if the function has a single simple parameter. If it has multiple parameters, no parameters, or default, destructured, or rest parameters, the parentheses around the parameter list are required.
 - The braces can only be omitted if the function directly returns an expression. If the body has additional lines of processing, the braces are required — and so is the `return` keyword. Arrow functions cannot guess what or when you want to return.
 - Due to being anonymous arrow functions are always unnamed. If the arrow function needs to call itself, use a named function expression instead. You can also assign the arrow function to a variable so it has a name.
 - Returning object literals using the concise body syntax `(params) => { object: literal }` does not work as expected. To fix this, wrap the object literal in parentheses `const func = () => ({ foo: 1 });`
 - the `call()`, `apply()`, and `bind()` methods are not useful when called on arrow functions, because arrow functions establish this based on the scope the arrow function is defined within, and the `this` value does not change based on how the function is invoked.
 - Arrow functions do not have their own arguments object.
```js
   // Traditional Anonymous function.
   (function (a) {
      return a + 100;
   });

   a => a + 100; // Shorter Arrow Function with same functionality.
```
</br>

### Q.17) What is the difference between `undefined` vs `not defined` vs `NaN` in JS.

---

**`Undefined` :**
1. It is also *not an assignment value*, like where a variable has been declared but has not yet been assigned a value.
2. The undefined value is a primitive value used when a variable has not been assigned a value.
3. Indicates absence of variable itself.
4. Converted to NaN while performing primitive operations.
5. Type of undefined is undefined.

**`NaN` :**
1. NaN stands for *(Not-A-Number)*
2. It represents something which is not a number.
3. NaN is not equal to itself.
4. The isNaN() function is used to determine whether a value is an illegal number (Not-a-Number) or not. i.e, This function returns true if the value equates to NaN.
5. Not a Number, is a member of a numeric data type that can be interpreted as a value that is undefined.
```js
   isNaN("Hello");   //true
   isNaN("100");     //false
```

**`null` :**
1. It is an assignment value which indicates that variable points to no object. 
2. Type of null is object.
3. The null value is a primitive value that represents the null, empty, or non-existent reference.
4. Indicates the absence of a value for a variable.
5. Converted to zero (0) while performing primitive operations.
</br>

### Q.18) What is callback hell ?

---

**Callback:** A callback is a function that is passed as an argument to another function that executes the callback based on the result. They are basically functions that are executed only after a result is produced. Callbacks are an important part of asynchronous JavaScript.
</br>
**Callback Hell:** Callback Hell is essentially nested callbacks stacked below one another forming a pyramid structure. Every callback depends/waits for the previous callback, thereby making a pyramid structure that affects the readability and maintainability of the code.
```js
async1(function(){
        async2(function(){
            async3(function(){
                async4(function(){
                    ....
                });
            });
        });
    }); 
```
</br>

### Q.19) Please explain Self Invoking Function and write it's code.

---

JavaScript *Self invoking functions* are nameless self-executing functions and invoked immediately after defining it. These self-invoking functions are man-made, these functions will execute automatically when followed by `( )`. Without `( )`, a function cannot be self-invoked. This is useful in initialization, adding event listeners, etc. These functions are also called as Immediately Invoked Function Expressions, as IIFE or Self Executing functions. The purpose of wrapping these functions is to control the visibility of its members. These anonymous functions are arguments passed to higher-order functions that needs to return a function. If the function is used only once, using a self Invoking function is easier as it is light weighted syntactically compared to the named function.
```js
   (function() {
   // body of the function
   console.log("Hi.)
   })();
```
</br>

### Q.20) What is the use of `setTimeout` ?

---

The `setTimeout()` method is used to call a function or evaluate an expression after a specified number of milliseconds only once. We use this to delay some kinds of executions. It is also used for animations and DOM manipulations in jquery.
</br>
For example, let's log a message after 2 seconds using setTimeout method,
```js
   setTimeout(function () {
      console.log("Good morning");
   }, 2000);
```
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