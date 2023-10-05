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
