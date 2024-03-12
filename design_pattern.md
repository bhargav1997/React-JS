Let's go through each of the mentioned design patterns in React and provide examples for each:

1. **Compound Components**:

Compound components are a design pattern where a group of components work together to form a single functional unit. They are commonly used to encapsulate related UI components and manage their state collectively.

```jsx
// CompoundComponent.js

import React from 'react';

const CompoundComponent = ({ children }) => {
  const [activeIndex, setActiveIndex] = React.useState(0);

  const handleClick = (index) => {
    setActiveIndex(index);
  };

  const childrenWithProps = React.Children.map(children, (child, index) => {
    return React.cloneElement(child, {
      isActive: index === activeIndex,
      onClick: () => handleClick(index),
    });
  });

  return <div>{childrenWithProps}</div>;
};

export default CompoundComponent;
```

Usage:

```jsx
import React from 'react';
import CompoundComponent from './CompoundComponent';
import Tab from './Tab';

const App = () => {
  return (
    <CompoundComponent>
      <Tab label="Tab 1">Content for Tab 1</Tab>
      <Tab label="Tab 2">Content for Tab 2</Tab>
      <Tab label="Tab 3">Content for Tab 3</Tab>
    </CompoundComponent>
  );
};

export default App;
```

2. **Controlled Components**:

Controlled components are React components whose state is controlled entirely by React. They receive their current value and change handlers through props and notify the parent component when they change.

```jsx
// ControlledInput.js

import React from 'react';

const ControlledInput = ({ value, onChange }) => {
  return <input type="text" value={value} onChange={(e) => onChange(e.target.value)} />;
};

export default ControlledInput;
```

Usage:

```jsx
import React, { useState } from 'react';
import ControlledInput from './ControlledInput';

const App = () => {
  const [inputValue, setInputValue] = useState('');

  const handleChange = (value) => {
    setInputValue(value);
  };

  return <ControlledInput value={inputValue} onChange={handleChange} />;
};

export default App;
```

3. **Uncontrolled Components**:

Uncontrolled components are React components that manage their state internally using refs. They are useful when integrating with third-party libraries or for handling form inputs where you don't need to control the state in React.

```jsx
// UncontrolledInput.js

import React, { useRef } from 'react';

const UncontrolledInput = () => {
  const inputRef = useRef(null);

  const handleSubmit = (e) => {
    e.preventDefault();
    alert('Input value: ' + inputRef.current.value);
  };

  return (
    <form onSubmit={handleSubmit}>
      <input type="text" ref={inputRef} />
      <button type="submit">Submit</button>
    </form>
  );
};

export default UncontrolledInput;
```

Usage:

```jsx
import React from 'react';
import UncontrolledInput from './UncontrolledInput';

const App = () => {
  return <UncontrolledInput />;
};

export default App;
```

These design patterns provide different approaches to managing component behavior and state in React, allowing for flexibility and reusability in building complex user interfaces.
