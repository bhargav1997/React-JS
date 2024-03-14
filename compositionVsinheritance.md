I can explain the difference between Composition and Inheritance in React with examples.

**Inheritance** is a concept where one class inherits properties from another class. In React, this is not commonly used because React components are more flexible when they use composition.

**Composition** is a way to combine simple functions or components to form more complex ones. React has a powerful composition model, and it's recommended to use composition instead of inheritance to reuse code between components.

Here are some examples:

**Inheritance:**

```jsx
class Button extends React.Component {
  render() {
    return <button className="common-button">{this.props.children}</button>;
  }
}

class PrimaryButton extends Button {
  render() {
    return <button className="common-button primary">{this.props.children}</button>;
  }
}
```

In the above example, `PrimaryButton` is inheriting from `Button`. This is not a common or recommended pattern in React.

**Composition:**

```jsx
function Button(props) {
  return <button className="common-button">{props.children}</button>;
}

function PrimaryButton(props) {
  return (
    <Button>
      <span className="primary">{props.children}</span>
    </Button>
  );
}
```

In the composition example, `PrimaryButton` is composed by using the `Button` component. This is the recommended pattern in React as it promotes cleaner and more modular code. 

Remember, in React, components are like functions, and they can be used in a similar way to how you'd use functions or objects in JavaScript (i.e., build them up by combining smaller parts). This is the essence of composition. 
