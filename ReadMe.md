# 1. Typescript

> _Install typescript when you've nodejs already installed._

```bash
npm install -g typescript
```

- Then if you use the command `tsc`, it'll generate a JavaScript file in the same directory. You can then run this JavaScript file using Node.js

```bash
tsc filename.ts

node filename.js
```

- To compile and run your TypeScript code in one step, you can use the `ts-node` package

```bash
ts-node filename.ts
```

-Typescript code dont work anywhere alone, it wont work in the browser nor in the nodejs environment. Thats why we need to transpile it first to javascript using a Typescript compiler(eg: tsc, babel)

---

1. A typescript project will likely have a `tsconfig.json` file which provides an infinite number of ways to customize the behviour of the TS compiler.
2. Primary Goal : Static Typing ()
   1. Can do that my annotating the code with "types"
   2. So we can strongly type a variable by using a colon `:` followed by it's type(data-type) which is known as an **Explicit Type**.
   ```ts
   let name1: string;
   let list1: number[] = [1, 2, 3];
   ```
   3. We can opt out of this static typing by using the keyword `any`. If we dont assign a type then it will be bydefault `any` type for typescript
   ```ts
   let name1: any;
   ```
3. By default, `tsc` compiler compiles ts code into es3 which doesnt have support for async-await.
   1. So better to make a `tsconfig.json` file which will configure the compiler based on this data.
      1. Put `"target": "esnext"` and run command `tsc` only. "target" instructs to compile js in the flavour of js like es5, es6, esnext(latest one), etc etc.
      ```bash
      tsc
      ```
      2. `"watch": true` will recompile the code everytime we save the ts file. It'll save us from typing tsc command after every change.
      3. `"lib"` allows us to get intellisense on those libraries which we are using in the typescript project. So it gets us environment for those libraries.
4. While installing some 3rd party libraries, sometimes it can be warning-full as typescript wont detect the type declarations directly. So we install mono repos which are community maintained. Like for in the case of lodash : \

```bash
npm i -D @types/lodash
```

### Create custom type :

1. Define using `type` keyword and name the type with pascalcase.
2. Can allow the custom type to have multiple data types using `|`.

```ts
type CustomStyle = string | "bold" | "italic" | 20;
```

### Strong type an object using `interface`

1. Can define the type of properties inside an object using interfaces.
2. It acts like a class to an object which can be interpreted as a template.

```ts
interface Person {
  first: string;
  last: string;
  [key: string]: any; // for any additionally property with string type key and any type data type
}
```

### Strong typing a function

1. It can be little more complex as it can require to strong type the arguments as well as return values.
2. Function return value can be given a type after the paranthesis in the function definition like `func(): Type`.
   1. But if there is a function doing any side effects or not returning anything then can give a `void` type over there like `func(): void`.

```ts
function pow(x: number, y: number): string {
  // function pow(x: number, y: number): void {
  return Math.pow(x, y).toString();
}
```

---

# 2. Monorepo

> The monorepo approach uses a single repository to host all the code for the multiple libraries or services composing a company’s projects. At its most extreme, the whole codebase from a company — spanning various projects and coded in different languages — is hosted in a single repository.

Benefits :

1. Lowers Barriers of Entry and streamlines the initial setup
2. Centrally Located Code Management
3. Managing all the different pull requests if there are multiple repositories for each project/library can be difficult so a monorepo makes it easy to perform all modifications to all code for all libraries and submit it under a single pull request.

Issues :

1. When the code for a library contains breaking changes, which make the tests for dependent libraries fail, the code must also be fixed before merging the changes.
2. Requires Download of Entire Codebase
3. Unmodified Libraries May Be Newly Versioned
4. Forking Is More Difficult and hence contributors can face problems navigating to their project of interest in the monorepo.

---

# 3. Redux :

Three basic imp parts :

1. Action - What to do
2. Reducer - How to do
3. State - Has current/updated value with the help of Redux store

## WHAT IS REDUX?

1. An open source JS library for managing application state.
2. Recommended for using only with big projects involing complex state management.

## WHY REDUX?

- When a JavaScript application grows big, it becomes difficult for the user to manage its state.

- It can be difficult to pass data from child component to parent component in certain cases.

- Redux solves this problem by managing application's state with a single global object called Store

- Makes Testing very easy

- Consistency throughout the application

---

#### **ACTION**

- An action is a **plain JS object** that describes the intention to cause change(Like ordering something on a button click)
  - Has a `type` field like `{ type : 'ORDER' }`
  - Tells what to do but doesnt tell how to do
  - Pure Object example :
  - ```
        return {
        type : "INCREMENT",
        paylaod: num
    }
    ```
- `Action creator` is a pure function which creates an action. Example : incNumber() is the function which creates action

```
export const incNumber = (num) => {
    return {
        type : "INCREMENT",
        paylaod: num
    }
}
```

#### **REDUCER**

- A reducer is a function that determines changes to an application's state, return the new state and tell the store how to do.

```bash
ACTION ---→	 REDUCER ---→ STORE
    ↑                       |
    |                       |
    |-------VIEWS ←---------|
```

- Reducers are functions that take `current state` and an `action` both as arguements and return a `new state`.
- Example : Fruit making machine with 3 parts like redux which are : 1. Action(moving the handle), 2. Reducer(machine crushing fruit), 3. State(Juice result)

#### **REDUX STORE**

- Redux store brings together state, actions and reducers of the app
- Only a single centralised store is there for the app
- It is basically a reducer only with root reducer

#### **REDUX PRINCIPLES**

1. Single store is the single source of truth
2. State is read-only and to change it there needs to be a dispatch of an action
3. Immutability in data (data is consistent and not changing), one way data flow and predictibilty of the outcome
4. Changes are made with 'Pure Reducer Function' means if same argument is passed then same outcome will come.

--

UI Views - Kid
Action creators - Parents - will send 2 things: Type & Payload.
(parents dispatching msg via Whatsapp to mad boy for kid's demands)
Reducer - Can be a real world entity like Mad boy
(Mad boy fulfills demands of kid from redux store)

### [Redux Flow chart](https://i.ibb.co/VpdCXmB/ecdbd6fa-5433-42cb-ac71-21ecadf49142.jpg)

## Installation :

```
npm i redux react-redux
```

---

Project steps :

1. Gave appropriate CSS and View template
2. Made actions
3. Made Reducers and index.js to combine all reducers
4. Made store to
5. Got the state from the store inside app's index.js
6. Using `Provider` in the index.js for App
7. Getting state via useSelector() hook in the App.js and updating it via useDispatch()

---

- ReactJS has `useContext` hooks which works similar like redux
- But Redux has `useSelector` hook to deal with states

---

# 4. Redux-Saga

- An intuitive Redux side effect manager.
- Commonly used with Redux to handle asynchronous operations like API calls.

# 5. Generator Functions in JS

- Redux Saga relies heavily on generator functions.
- These are special functions in JavaScript marked by an asterisk (\*) that allow you to pause and resume their execution.
  - You can either use `function* generatorFunc() {...}` or `function *generatorFunc(){...}` to create them.
- They are used to represent asynchronous flows in a synchronous-looking manner.
- Using `yeild` keyword, we can pause the execution of a generator function without executing the whole function body.
- The `yield` expression returns a value.
  - However, unlike the return statement, it doesn't terminate the program.
  - That's why you can continue executing code from the last yielded position.

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
2. code before the second yield
{ value: 200, done: false }
3. code after the second yield
{ value: undefined, done: true }
```

- The first `generator.next()` statement executes the code up to the first yield statement and pauses the execution of the program.
- The second `generator.next()` starts the program from the paused position.
- When all the elements are accessed, it returns `{value: undefined, done: true}`.

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
