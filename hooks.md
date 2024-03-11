Here are the main hooks provided by React with code examples and explanations:

1. **useState**: This hook lets you add state to functional components.

```javascript
import React, { useState } from 'react';

function Counter() {
  const [count, setCount] = useState(0);

  return (
    <div>
      <p>You clicked {count} times</p>
      <button onClick={() => setCount(count + 1)}>
        Click me
      </button>
    </div>
  );
}
```

2. **useEffect**: This hook lets you perform side effects in function components. It is a close replacement for `componentDidMount`, `componentDidUpdate`, and `componentWillUnmount`.

```javascript
import React, { useState, useEffect } from 'react';

function Example() {
  const [count, setCount] = useState(0);

  // Similar to componentDidMount and componentDidUpdate:
  useEffect(() => {
    document.title = `You clicked ${count} times`;
  });

  return (
    <div>
      <p>You clicked {count} times</p>
      <button onClick={() => setCount(count + 1)}>
        Click me
      </button>
    </div>
  );
}
```

3. **useContext**: This hook lets you subscribe to React context without introducing nesting.

```javascript
import React, { useContext } from 'react';
const ThemeContext = React.createContext('light');

function ThemedButton() {
  const theme = useContext(ThemeContext);
  return <button theme={theme}>I am styled by theme context!</button>;
}
```

4. **useReducer**: This hook is an alternative to `useState`. It helps you manage complex state logic involving multiple sub-values or when the next state depends on the previous one.

```javascript
import React, { useReducer } from 'react';

const initialState = {count: 0};

function reducer(state, action) {
  switch (action.type) {
    case 'increment':
      return {count: state.count + 1};
    case 'decrement':
      return {count: state.count - 1};
    default:
      throw new Error();
  }
}

function Counter() {
  const [state, dispatch] = useReducer(reducer, initialState);
  return (
    <>
      Count: {state.count}
      <button onClick={() => dispatch({type: 'increment'})}>+</button>
      <button onClick={() => dispatch({type: 'decrement'})}>-</button>
    </>
  );
}
```

5. **useRef**: This hook can be used to create mutable variables that persist across re-renders.

```javascript
import React, { useRef } from 'react';

function TextInputWithFocusButton() {
  const inputEl = useRef(null);
  const onButtonClick = () => {
    // `current` points to the mounted text input element
    inputEl.current.focus();
  };
  return (
    <>
      <input ref={inputEl} type="text" />
      <button onClick={onButtonClick}>Focus the input</button>
    </>
  );
}
```

6. **useMemo**: This hook returns a memoized value, only recomputing the memoized value when one of the dependencies has changed.

```javascript
import React, { useMemo } from 'react';

function MyComponent({ a, b }) {
  const result = useMemo(() => {
    // Expensive computation goes here
  }, [a, b]);
  return <div>{result}</div>;
}
```

7. **useCallback**: This hook returns a memoized version of the callback that only changes if one of the dependencies has changed.

```javascript
import React, { useState, useCallback } from 'react';

function MyComponent() {
  const [count, setCount] = useState(0);

  const increment = useCallback(() => {
    setCount(count + 1);
  }, [count]);

  return <button onClick={increment}>Increase count</button>;
}
```

8. **useImperativeHandle**: This hook customizes the instance value that is exposed to parent components when using `ref`. In other words, it allows parent components to call methods on child components.

```javascript
import React, { useRef, useImperativeHandle, forwardRef } from 'react';

const FancyInput = forwardRef((props, ref) => {
  useImperativeHandle(ref, () => ({
    focus: () => {
      // ...
    }
  }));
  return <input />;
});

// Usage
const ref = useRef();
<FancyInput ref={ref} />;
// Now you can call `ref.current.focus()`
```

9. **useLayoutEffect**: This hook is identical to `useEffect`, but it fires synchronously after all DOM mutations. Use this to read layout from the DOM and synchronously re-render. Updates scheduled inside `useLayoutEffect` will be flushed synchronously, before the browser has a chance to paint.

```javascript
import React, { useLayoutEffect } from 'react';

function MyComponent() {
  useLayoutEffect(() => {
    // Your code here
  });
  return <div />;
}
```

10. **useDebugValue**: This hook can be used to display a label for custom hooks in React DevTools.

```javascript
import React, { useState, useDebugValue } from 'react';

function useFriendStatus(friendID) {
  const [isOnline, setIsOnline] = useState(null);

  // Show a label in DevTools next to this Hook
  // e.g. "FriendStatus: Online"
  useDebugValue(isOnline ? 'Online' : 'Offline');

  // Rest of the hook code
}

function FriendStatus(props) {
  const isOnline = useFriendStatus(props.friend.id);
  if (isOnline === null) {
    return 'Loading...';
  }
  return isOnline ? 'Online' : 'Offline';
}
```

Remember, hooks are a new addition in React 16.8. They let you use state and other React features without writing a class. Happy coding! 🚀
