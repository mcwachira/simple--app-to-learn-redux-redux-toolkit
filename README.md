# This is a repo to help me understand redux and redux toolkit

The project is a simple counter app. Its through this app I was able to understand redux , redux toolkit and the differences between the two

In the project directory, you can run:

### `Redux`

Its a complex state management tool with a single store as a cds

### `Reducers`

Manages the state and returns a newly updated state

### `Actions`

action are made up of two properties
1.a unique identifier 2. payload which has data

### `Dispatch`

Used to send actions to update the data

## Learn More

You can learn more in the [Create React App documentation](https://facebook.github.io/create-react-app/docs/getting-started).

To learn React, check out the [React documentation](https://reactjs.org/).

### Store Js in redux

```
import { createStore } from "redux";

const reducerFn = (state = { counter: 0 }, action) => {

    if (action.type === 'inc') {
        return { state.counter + 1 }
    }
    else if (action.type === 'dec') {
        return { state.counter - 1 }
    }
    else if (action.type === 'add') {
        return { state.counter + action.payload }
    }
    return state;

}

const store = createStore(reducerFn)

export default store;

```

### App Js in redux

```
import { useSelector, useDispatch } from 'react-redux';
import './App.css';

function App() {
const counter = useSelector((state) => state.counter)
const dispatch = useDispatch()
const increment = () => {
dispatch({ type: 'inc' })
}
const decrement = () => {
dispatch({ type: 'dec' })
}
const addBy = () => {
dispatch({ type: "add", payload: 10 })
}
return (

<div >
<h1>
Counter App
</h1>
<h2>{counter}</h2>

      <button onClick={increment}>increment</button>
      <button onClick={decrement}>decrement</button>
      <button onClick={addBy}>  add by 10</button>
    </div>

);
}

export default App;
```

### Redux Toolkit

Its an opinionated, batteries-included toolset for efficient Redux development.

## Redux Toolkit includes

### configureStore()

Wraps createStore to provide simplified configuration options and good defaults. It can automatically combine your slice reducers, adds whatever Redux middleware you supply.

### createReducer()

It lets you supply a lookup table of action types to case reducer functions, rather than writing switch statements.

### createAction()

Generates an action creator function for the given action type string. The function itself has toString() defined, so that it can be used in place of the type constant.

### createSlice()

It accepts an object of reducer functions, a slice name, and an initial state value, and automatically generates a slice reducer with corresponding action creators and action types.

### Store Js in redux-toolkit

```
import { configureStore, createSlice } from "@reduxjs/toolkit";

const counterSlice = createSlice({
name: 'counter',
initialState: { counter: 0 },
reducers: {
increment(state, action) {
state.counter++;
},
decrement(state, action) {
state.counter--;
},
addBy(state, action) {
state.counter += action.payload;
}
}

})

export const actions = counterSlice.actions;

const store = configureStore({
reducer: counterSlice.reducer
})

export default store

### App.js in redux toolkit

import { useSelector, useDispatch } from 'react-redux';
import { actions } from './store/index';
import './App.css';

function App() {
const counter = useSelector((state) => state.counter)
const dispatch = useDispatch()
const increment = () => {
dispatch(actions.increment())
}
const decrement = () => {
dispatch(actions.decrement())
}
const addBy = () => {
dispatch(actions.addBy(10))
}
return (

<div >
<h1>
Counter App
</h1>
<h2>{counter}</h2>

      <button onClick={increment}>increment</button>
      <button onClick={decrement}>decrement</button>
      <button onClick={addBy}>  add by 10</button>
    </div>

);
}

export default App;
```

This section has moved here: [https://facebook.github.io/create-react-app/docs/deployment](https://facebook.github.io/create-react-app/docs/deployment)

### `npm run build` fails to minify

This section has moved here: [https://facebook.github.io/create-react-app/docs/troubleshooting#npm-run-build-fails-to-minify](https://facebook.github.io/create-react-app/docs/troubleshooting#npm-run-build-fails-to-minify)
