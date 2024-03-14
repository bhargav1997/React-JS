In React, a Controlled Component is a component that manages form data via its own state. It receives values through props and updates them through callbacks like onChange. 

Here's an example of a controlled component:

```jsx
import React, { useState } from 'react';

function ControlledForm() {
  const [name, setName] = useState('');

  const handleChange = (event) => {
    setName(event.target.value);
  };

  const handleSubmit = (event) => {
    event.preventDefault();
    alert('A name was submitted: ' + name);
    setName('');
  };

  return (
    <form onSubmit={handleSubmit}>
      <label>
        Name:
        <input type="text" value={name} onChange={handleChange} />
      </label>
      <input type="submit" value="Submit" />
    </form>
  );
}

export default ControlledForm;
```

In this example, the `ControlledForm` component has a state variable `name` that holds the value of the input element. 
The `handleChange` function is called whenever the input value changes, updating the `name` state. 
When the form is submitted, the `handleSubmit` function is called, which shows an alert with the submitted name and then resets the `name` state to an empty string.

This is a simple example, but controlled components can become more complex with multiple inputs and more complex state. 
The key idea is that React is in control of the input values and form submissions, not the DOM. 
This makes it easier to integrate with the rest of the React application and manage complex state and UI logic. 

Remember to import the `ControlledForm` component in your main component (usually `App.js`) and use it like any other component:

```jsx
import ControlledForm from './ControlledForm';

function App() {
  return (
    <div className="App">
      <ControlledForm />
    </div>
  );
}

export default App;
```

This will render the `ControlledForm` component in your application. 
You can then enter a name in the input field and submit the form to see the alert message. After you close the alert, the input field will be cleared. 
This is because we reset the `name` state in the `handleSubmit` function. This is a common pattern in controlled components: you control the state of the input elements and handle form submissions in React, not in the DOM. 
This gives you more control and makes it easier to integrate with the rest of your React application. 
