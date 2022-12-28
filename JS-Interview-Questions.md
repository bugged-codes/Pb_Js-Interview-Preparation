# 📝 JS Interview Questions.

## Day 1️⃣

### Q.1) Difference between “ == “ and “ === “ operators.

1. "==" operator is called as **Loose equality**.
2. "===" operator is called as **Strict equality.**
3. Both are comparative operatives with a slight difference in between them.
4. Both operators return only the ***Boolean*** value output, which is either `true` or `false`.
5. Main difference between both is that ""=="" checks if only value is true, whereas "===" checks value as well as datatype of a data to compare.
6. e.g., `var x = 2; var y = '2';`
   when we do `x==y` it returns true. --> loose equality
   when we do `x===y` it returns false as it compares `x` is Number and `y` is string datatype --> strict equality.

### Q.2) What is the spread operator ?

1. It is defined by using (…) “Three dots”. It allows us to de-structure the non-primitive data type in JS.
2. It was introduced in ES6 by ECMA International in 2015.****
3. `const a = [1,2,3], b = a;` here, the memory location is passed into var `'b'` as it is defined by memory reference, so if we update `'a'` after defining `'b'` the value of `'a'` as well as ‘b’ will get updated. So, to avoid this also we use spread operator. Like `b = […a];` which will create a separate copy of `'a'` in `'b'` with values of `'a'` and won't update after updating `'a'` .
4. `...rest` is also a operator, in contrast with spread operator the rest operator is used to construct a non-primitive datatype like *array*. In above example we can use rest operator to create a separate variables as values of *array* a by using, `const [x,y,…rest] = a`. Here, *array* values get constructed as separate variables.
5. ```js
   const	arr1 = [1,2,3], arr2 = [5,6,7];
   let firstarr = …arr1;
   let secondarr = …arr2;
   let combinedarr = […arr1, …arr2];
   //it can be also used to separate each element form array and use it store in another element.

   ```

### Q.3) What are the differences between var, let and const ?

1. `var`, `const` and `let` are used to.
2. 1

### Q.4) What is execution context ?

1. All JavaScript code needs to be hosted and run in some kind of environment. In most cases, that environment is be a web browser.
2. The browser's JavaScript engine then creates a special environment to handle the transformation and execution of this JavaScript code. This environment is known as the `Execution Context` . Or it can also be defined as, in JavaScript the environment that enables the JavaScript code to get executed is what we call  **JavaScript Execution Context** .
3. It is the execution context that decides which code section has access to the `functions`, `variables`, and `objects` used in the code. During the Execution Context run-time, the specific code gets parsed by a parser, the `variables` and `functions` are stored in memory, executable byte-code gets generated, and the code gets executed.
4. There are **3** types of Execution contexts in JS -
   1. <u>**Global Execution context/GEC**</u> - This is the default execution context in which JS code start its execution when the file first loads in the browser. All of the global code i.e. code which is not inside any function or object is executed inside the global execution context. GEC cannot be more than one because only one global environment is possible for JS code execution as the JS engine is single threaded.
   2. <u>**Functional Execution context/FEC**</u> - Functional execution context is defined as the context created by the JS engine whenever it finds any function call. Each function has its own execution context. It can be more than one. Functional execution context has access to all the code of the global execution context though vice versa is not applicable. While executing the global execution context code, if JS engine finds a function call, it creates a new functional execution context for that function.
   3. <u>**Eval Execution context**</u> - Execution context inside `eval` function.
5. **Execution context stack (ECS)** - Execution context stack is a stack data structure, i.e. last in first out data structure, to store all the execution stacks created during the life cycle of the script. Global execution context is present by default in execution context stack and it is at the bottom of the stack. While executing the global execution context code, if JS engines find a function call, it creates a functional execution context for that function and pushes it on top of the execution context stack. JS engine executes the function whose execution context is at the top of the execution context stack. Once all the code of the function is executed, JS engines pop out that function’s execution context and start’s executing the function which is below it.
