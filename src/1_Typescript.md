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
