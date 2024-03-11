Redux Toolkit is the official, opinionated, batteries-included toolset for efficient Redux development. It simplifies the Redux setup process, reduces boilerplate code, and includes Redux Thunk by default¹.

Here's a simple example of how you can use Redux Toolkit to manage the state of a counter application:

```javascript
import { configureStore, createSlice } from '@reduxjs/toolkit';

// Define a slice of the Redux state
const counterSlice = createSlice({
  name: 'counter',
  initialState: 0,
  reducers: {
    increment: (state) => state + 1,
    decrement: (state) => state - 1,
  },
});

// Extract the action creators object and the reducer
const { actions, reducer } = counterSlice;

// Define the store
const store = configureStore({ reducer });

// Dispatch actions
store.dispatch(actions.increment());
store.dispatch(actions.decrement());
```

In this example, `createSlice` automatically generates action creators and action types based on the reducers you provide, which helps reduce boilerplate. `configureStore` sets up the Redux store with good defaults for development, including setting up the Redux DevTools Extension and adding middleware like Redux Thunk.

For more in-depth tutorials and explanations, you can refer to the following resources:
- [How to Use Redux and Redux Toolkit – Tutorial for Beginners](^1^)
- [Tutorials Overview | Redux Toolkit - JS.ORG](^2^)
- [Redux Toolkit Setup Tutorial - DEV Community](^3^)
- [Learn Redux Toolkit – The Recommended Way to Use Redux - freeCodeCamp.org](^4^)
- [React 18 with Redux Toolkit: A Simple Guide with Code Explanations](^5^)

Remember, while Redux Toolkit simplifies many aspects of using Redux, it's still important to understand the core concepts of Redux. 

In Redux Toolkit, you can use custom middleware by providing it to the `configureStore` function. Here's an example of how you can add a custom middleware:

```javascript
import { configureStore, getDefaultMiddleware } from '@reduxjs/toolkit';
import logger from 'redux-logger';
import rootReducer from './reducer';

// Define your custom middleware
const customMiddleware = storeAPI => next => action => {
  // Your custom logic goes here
  return next(action);
};

const middleware = [...getDefaultMiddleware(), customMiddleware, logger];

const store = configureStore({
  reducer: rootReducer,
  middleware,
});
```

In this example, `customMiddleware` is a custom middleware function. It follows the standard Redux middleware signature of `(storeAPI) => (next) => (action) => {}`. You can put your custom logic inside this function⁵.

If you want to include the default middleware as well as your custom middleware, you can use `getDefaultMiddleware` to get an array of the default middleware, and then spread that array into the `middleware` option for `configureStore`¹²⁴.

Remember, middleware in Redux is a way to enhance the dispatch function with custom logic. It's often used for dealing with asynchronous actions³. 

Happy coding! 🚀
