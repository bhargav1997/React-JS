Error Boundaries in React are a way to catch JavaScript errors anywhere in their child component tree, log those errors, and display a fallback UI instead of the component tree that crashed.

Here's an example of how you can use Error Boundaries:

```javascript
import React from 'react';

class ErrorBoundary extends React.Component {
  constructor(props) {
    super(props);
    this.state = { hasError: false };
  }

  static getDerivedStateFromError(error) {
    // Update state so the next render will show the fallback UI.
    return { hasError: true };
  }

  componentDidCatch(error, errorInfo) {
    // You can also log the error to an error reporting service
    console.log(error, errorInfo);
  }

  render() {
    if (this.state.hasError) {
      // You can render any custom fallback UI
      return <h1>Something went wrong.</h1>;
    }

    return this.props.children; 
  }
}

// Usage
<ErrorBoundary>
  <MyComponent />
</ErrorBoundary>
```

In this example, `ErrorBoundary` is a component that catches JavaScript errors anywhere in its child component tree, logs those errors, and displays a fallback UI instead of the component tree that crashed. `getDerivedStateFromError` is a lifecycle method that catches errors during the "render" phase. `componentDidCatch` catches errors during the "commit" phase.

Remember, error boundaries only catch errors in the components below them in the tree. An error boundary can’t catch an error within itself. 
Happy coding! 🚀
