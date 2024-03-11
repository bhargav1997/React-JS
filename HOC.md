Let's dive into Higher-Order Components (HOCs) in React.

A higher-order component (HOC) in React is a pattern used to share common functionality between components without repeating the code. HOCs are not part of the React API. They are a pattern that emerges from React's compositional nature.

A HOC is a function that takes a component and returns a new component.

```javascript
const EnhancedComponent = higherOrderComponent(WrappedComponent);
```

Let's create a simple HOC:

```javascript
// A simple HOC that logs component props
function withPropsLog(WrappedComponent) {
  return class extends React.Component {
    componentDidMount() {
      console.log(this.props);
    }

    render() {
      // Wraps the input component in a container, without mutating it. Good!
      return <WrappedComponent {...this.props} />;
    }
  };
}
```

In this example, `withPropsLog` is a HOC. It's a function that takes a component and returns a new component that logs its props when it mounts.

Here's how you can use it:

```javascript
class MyComponent extends React.Component {
  render() {
    return <div>Hello, world!</div>;
  }
}

const MyComponentWithPropsLog = withPropsLog(MyComponent);

// Usage
<MyComponentWithPropsLog foo="bar" />
```

When `MyComponentWithPropsLog` mounts, it will log `{foo: "bar"}` to the console.

Remember, HOCs are a way to reuse component logic. They aren't the only way, and you should not try to force every bit of logic into a HOC. 
Use them when they make sense, and feel free to use other patterns when they don't. 

Happy coding! 🚀
