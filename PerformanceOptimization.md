Performance Optimization: Understand the React component lifecycle and learn how to optimize your app for performance. 
Learn about lazy loading, code splitting, memoization, and the useMemo and useCallback hooks.

Let's break down each optimization technique and provide code examples along with detailed explanations:

1. **Lazy Loading and Code Splitting**:

Lazy loading and code splitting are techniques used to improve the initial loading time of your React application by splitting your code into smaller chunks and loading them only when they are needed.

Here's how you can achieve lazy loading and code splitting using React's `lazy` function and dynamic imports:

```jsx
// App.js

import React, { Suspense } from 'react';

const LazyComponent = React.lazy(() => import('./LazyComponent'));

const App = () => {
  return (
    <Suspense fallback={<div>Loading...</div>}>
      <LazyComponent />
    </Suspense>
  );
};

export default App;
```

```jsx
// LazyComponent.js

import React from 'react';

const LazyComponent = () => {
  return <div>This component is lazily loaded.</div>;
};

export default LazyComponent;
```

In this example:

- We import `React.lazy` and pass a function that returns a dynamic import of the component we want to lazily load.
- We use `Suspense` component from React to show a loading indicator while the component is being loaded asynchronously.

2. **Memoization with useMemo**:

`useMemo` is a hook in React that memoizes the result of a function and re-computes it only when one of its dependencies changes. This can be useful for optimizing expensive calculations or preventing unnecessary re-renders of components.

Here's an example of using `useMemo` to memoize the result of a factorial calculation:

```jsx
import React, { useMemo } from 'react';

const FactorialComponent = ({ number }) => {
  const factorial = useMemo(() => {
    let result = 1;
    for (let i = 1; i <= number; i++) {
      result *= i;
    }
    return result;
  }, [number]);

  return <div>Factorial of {number} is {factorial}</div>;
};

export default FactorialComponent;
```

In this example:

- We use `useMemo` to memoize the factorial calculation function.
- The factorial calculation function is only re-computed when the `number` prop changes.

3. **Memoization with useCallback**:

`useCallback` is a hook in React that memoizes a callback function and returns the memoized version of the callback. This can be useful for preventing unnecessary re-renders of child components that depend on callback functions.

Here's an example of using `useCallback` to memoize a callback function:

```jsx
import React, { useCallback } from 'react';

const MemoizedCallbackComponent = () => {
  const handleClick = useCallback(() => {
    console.log('Button clicked');
  }, []);

  return <button onClick={handleClick}>Click me</button>;
};

export default MemoizedCallbackComponent;
```

In this example:

- We use `useCallback` to memoize the `handleClick` callback function.
- The `handleClick` function is only re-created when its dependencies change, which in this case is an empty array.

These optimization techniques can significantly improve the performance of your React application by reducing unnecessary re-renders and loading only the necessary code when it's needed.
