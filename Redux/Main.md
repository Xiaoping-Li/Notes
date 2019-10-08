# Redux
## Summary
React is a library used to build user interfaces.
* React context - Prevents prop drilling. Allows you to consume props deep within the components without manually pass it down through all the intermediate components
* React context + hooks (useContext + useReducer)

Redux is a library for managing state in a predictable way in JavaScript applications. `Redux is a predictable state container for JavaScript apps`
* It is for JavaScript apps
 * Redux is not tied to React
 * Can be used with React, Angular, Vue or even vanilla JavaScript
 * Redux is a library for JavaScript applications
* It is a state Container
* It is predictable
 * In redux, all state transitions are explicit and it is possible to keep track of them
 * The changes to your application's state become predictable

React-redux is a library that provides bindings to use React and Redux together in an application.
* React-redux offers a couple of functions that will help you connect your react application with redux

## Set up
```
yarn add redux
yarn add react-redux
```

## 4 Steps
1. state:
  * reducer
  * state
2. reducer
  * state
  * action
3. subscribe: get the current state
4. dispatch
