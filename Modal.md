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
Happy coding! 🚀
