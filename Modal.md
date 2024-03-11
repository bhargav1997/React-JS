React Portals provide a first-class way to render children into a DOM node that exists outside the DOM hierarchy of the parent component.

Here's an example of how you can use portals:

```javascript
import React from 'react';
import ReactDOM from 'react-dom';

class Modal extends React.Component {
  el = document.createElement('div');

  componentDidMount() {
    document.body.appendChild(this.el);
  }

  componentWillUnmount() {
    document.body.removeChild(this.el);
  }

  render() {
    return ReactDOM.createPortal(
      this.props.children,
      this.el,
    );
  }
}

// Usage
function App() {
  return (
    <div>
      <h1>Hello, world!</h1>
      <Modal>
        <div>This is a modal</div>
      </Modal>
    </div>
  );
}

ReactDOM.render(<App />, document.querySelector('#root'));
```

In this example, `Modal` is a component that uses `ReactDOM.createPortal` to render its children into a new "subtree" outside of its parent component's DOM hierarchy. The `Modal` component creates a new DOM element `div` and appends it to the `body` on mount, and removes it on unmount. The children of `Modal` are rendered into this new DOM element via the portal.

This can be useful for rendering components that are visually "detached" from their parents, like modals, popovers, or notifications. 

Here are some best practices for using Portals in React:

1. **Use for UI Overlay**: Portals are best used for floating UI elements that should break out of their container, like modals, tooltips, and popovers.

2. **Event Bubbling**: Remember that events bubble up through portals as if they were part of the same React tree, even though the DOM tree may be different. This is a feature of React's event system.

3. **Avoid Unnecessary Re-renders**: Be mindful of unnecessary re-renders with portals. Since portal content lives outside the parent component, a re-render of the parent can cause unmounting and remounting of the portal content, even if the portal children did not change.

4. **Clean Up**: If you're creating DOM elements and attaching them to the body manually like in the case of modals, don't forget to clean up after the component unmounts to avoid memory leaks.

5. **Accessibility**: Ensure that your portal components are accessible. For example, if you're building a modal, ensure that focus is managed correctly.

6. **Styling**: Since portals render components outside the parent component, styles defined in the parent do not cascade to the children. You might need to ensure that the portal component is styled independently.

Remember, while portals can be a powerful tool, they come with their own set of complexities and should be used judiciously. 

Happy coding! 🚀
