Here's a simple example of a user registration screen implemented as a modal using React:

```jsx
import React, { useState } from 'react';
import ReactDOM from 'react-dom';

function App() {
  const [modalOpen, setModalOpen] = useState(false);

  const openModal = () => {
    setModalOpen(true);
  };

  const closeModal = () => {
    setModalOpen(false);
  };

  return (
    <div>
      <button onClick={openModal}>Register</button>
      {modalOpen && <Modal onClose={closeModal} />}
    </div>
  );
}

function Modal({ onClose }) {
  return ReactDOM.createPortal(
    <div className="modal">
      <h2>Register</h2>
      <form>
        <label>
          Username:
          <input type="text" name="username" />
        </label>
        <label>
          Password:
          <input type="password" name="password" />
        </label>
        <button type="submit">Submit</button>
      </form>
      <button onClick={onClose}>Close</button>
    </div>,
    document.body
  );
}

ReactDOM.render(<App />, document.querySelector('#root'));
```

In this example, clicking the "Register" button in the `App` component opens the `Modal` component. The `Modal` component is a form for user registration with fields for username and password. The modal can be closed by clicking the "Close" button.

The `Modal` component uses `ReactDOM.createPortal` to render its children into a new "subtree" outside of its parent component's DOM hierarchy. This is useful for rendering components that are visually "detached" from their parents, like modals.

Please note that this is a basic example and doesn't include form validation or handling form submission. You would need to add those features in a real-world application. Also, the modal is appended directly to `document.body`. 
In a real-world application, you might want to use a more specific container for your modals. 

Happy coding! 🚀
