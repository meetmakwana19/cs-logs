# 5. Generator Functions in JS

- Redux Saga relies heavily on generator functions.
- These are special functions in JavaScript marked by an asterisk (\*) that allow you to pause and resume their execution.
  - You can either use `function* generatorFunc() {...}` or `function *generatorFunc(){...}` to create them.
- They are used to represent asynchronous flows in a synchronous-looking manner.
- Using `yeild` keyword, we can pause the execution of a generator function without executing the whole function body.
- The `yield` expression returns a value.
  - However, unlike the return statement, it doesn't terminate the program.
  - That's why you can continue executing code from the last yielded position.
- So **`yeild`** means "I want to emit this value, but I'll pause execution here until someone requests the next value."

```js
function* generatorFunc() {
  console.log("1. code before first yield");
  yield 100;

  console.log("2. code before the second yield");
  yield 200;

  console.log("3. code after the second yield");
}

const generator = generatorFunc();

console.log(generator.next());
console.log(generator.next());
console.log(generator.next());
```

```bash
1. code before first yield
{ value: 100, done: false }
1. code before the second yield
{ value: 200, done: false }
1. code after the second yield
{ value: undefined, done: true }
```

Another example :

```js
function* myGenerator() {
  yield 1;
  yield 2;
  yield 3;
}

const generator = myGenerator();
console.log(generator.next()); // { value: 1, done: false }
console.log(generator.next()); // { value: 2, done: false }
console.log(generator.next()); // { value: 3, done: false }
console.log(generator.next()); // { value: undefined, done: true }
```

- The first `generator.next()` statement executes the code up to the first yield statement and pauses the execution of the program.
- The second `generator.next()` starts the program from the paused position.
- When all the elements are accessed, it returns `{value: undefined, done: true}`.
  - So the `next()` method returns an object with two properties: `value` (the yielded value) and `done` (a boolean indicating if the generator has finished).
  -  To advance the generator function's execution, you call the `next()` method on the generator object. 
  -  This method resumes the generator function from where it was paused by the last yield statement and runs until the next yield or until the function exits.
- The `next()` method returns an object with a `value` property. This `value` property holds the value that was emitted by the most recent `yield` statement. It's essentially the value produced by the generator function during that step of execution.


> Also, Generator functions and Generators in JavaScript are a way to create iterators, which allow you to efficiently iterate over a potentially large sequence of values one at a time.

> They are used for tasks like iterating through arrays, processing streams of data, or generating sequences dynamically.

Using a Generator to Generate an Infinite Sequence:

- Generators can be used to create infinite sequences or handle large data sets efficiently without loading everything into memory.

```js
function* infiniteSequence() {
  let i = 0;
  while (true) {
    yield i++;
  }
}

const generator = infiniteSequence();
console.log(generator.next().value); // 0
console.log(generator.next().value); // 1
console.log(generator.next().value); // 2
// ...
```

Another example for Passing Arguments to Generator Functions : 

```js
// generator function
function* generatorFunc() {

    // returns 'hello' at first next()
    let x = yield 'hello';
    
    // returns passed argument on the second next()
    console.log(x);
    console.log('some code');

    // returns 5 on second next()
    yield 5;
    
}

const generator = generatorFunc();

console.log(generator.next());
console.log(generator.next(6));
console.log(generator.next());
```
```bash
{ value: 'hello', done: false }
6
some code
{ value: 5, done: false }
{ value: undefined, done: true }
```


## Generators:

Using a generator,

- you can stop the execution of a function from anywhere inside the function
- and continue executing code from a halted position
- To create a generator, you need to first define a generator function with `function*` symbol.
- The objects of generator functions are called **generators**.

```js
// define a generator function
function* generator_function() {
   ... .. ...
}

// creating a generator
const generator_obj = generator_function();
```

- When you call a generator function, it returns a "Generator object" only with a 'suspended' state. (Can check by console logging on devtools console)
-  It represents the current state of the generator function's execution. 
-  You can use the `next()` method of the generator object to advance the function's execution and retrieve the next yielded value.
-  By using generator functions, you can write your code in a step-by-step manner, which makes it clear what happens at each step. 
   -  This makes your code more "declarative," meaning you explicitly state what should happen in response to certain actions or events, making it easier for you and others to understand and reason about the code.

