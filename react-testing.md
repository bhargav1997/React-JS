I can provide you with an example of testing React components step by step. Let's create a simple React component called `Counter` that increments a value when a button is clicked, and then we'll write tests for it using Jest and React Testing Library.

First, let's create the `Counter` component:

```jsx
// Counter.js

import React, { useState } from 'react';

const Counter = () => {
  const [count, setCount] = useState(0);

  const increment = () => {
    setCount(count + 1);
  };

  return (
    <div>
      <p>Count: {count}</p>
      <button onClick={increment}>Increment</button>
    </div>
  );
};

export default Counter;
```

Now, let's create a test file for our `Counter` component:

```jsx
// Counter.test.js

import React from 'react';
import { render, fireEvent } from '@testing-library/react';
import Counter from './Counter';

test('increments count when the button is clicked', () => {
  const { getByText } = render(<Counter />);

  // Initial count should be 0
  expect(getByText('Count: 0')).toBeInTheDocument();

  // Click the button
  fireEvent.click(getByText('Increment'));

  // Count should be incremented to 1
  expect(getByText('Count: 1')).toBeInTheDocument();
});
```

In this test:

1. We render the `Counter` component using `render` from `@testing-library/react`.
2. We assert that the initial count is displayed as 'Count: 0'.
3. We simulate a click on the button using `fireEvent.click`.
4. We assert that the count is updated to 'Count: 1' after the button click.

Now, let's install the necessary dependencies to run our tests:

```bash
npm install --save-dev @testing-library/react @testing-library/jest-dom
```

Finally, you can run the tests using Jest:

```bash
npm test
```

This will execute the tests in the `Counter.test.js` file and output the results. You should see a passing test indicating that the count increments when the button is clicked.


**Example 2: Todo app testing:**

Let's create a more complex scenario with a `TodoList` component that manages a list of todos. The `TodoList` component will allow adding new todos, marking todos as completed, and deleting todos.

First, let's create the `TodoList` component:

```jsx
// TodoList.js

import React, { useState } from 'react';

const TodoList = () => {
  const [todos, setTodos] = useState([]);
  const [inputValue, setInputValue] = useState('');

  const handleInputChange = (e) => {
    setInputValue(e.target.value);
  };

  const addTodo = () => {
    if (inputValue.trim() !== '') {
      setTodos([...todos, { id: Date.now(), text: inputValue, completed: false }]);
      setInputValue('');
    }
  };

  const toggleTodo = (id) => {
    setTodos(
      todos.map((todo) =>
        todo.id === id ? { ...todo, completed: !todo.completed } : todo
      )
    );
  };

  const deleteTodo = (id) => {
    setTodos(todos.filter((todo) => todo.id !== id));
  };

  return (
    <div>
      <input
        type="text"
        value={inputValue}
        onChange={handleInputChange}
        placeholder="Add a new todo"
      />
      <button onClick={addTodo}>Add Todo</button>
      <ul>
        {todos.map((todo) => (
          <li key={todo.id}>
            <input
              type="checkbox"
              checked={todo.completed}
              onChange={() => toggleTodo(todo.id)}
            />
            <span style={{ textDecoration: todo.completed ? 'line-through' : 'none' }}>
              {todo.text}
            </span>
            <button onClick={() => deleteTodo(todo.id)}>Delete</button>
          </li>
        ))}
      </ul>
    </div>
  );
};

export default TodoList;
```

Now, let's create a test file for our `TodoList` component:

```jsx
// TodoList.test.js

import React from 'react';
import { render, fireEvent } from '@testing-library/react';
import TodoList from './TodoList';

test('adds, toggles, and deletes todos', () => {
  const { getByPlaceholderText, getByText, getByLabelText, queryByText } = render(<TodoList />);

  // Add todos
  const input = getByPlaceholderText('Add a new todo');
  fireEvent.change(input, { target: { value: 'Todo 1' } });
  fireEvent.click(getByText('Add Todo'));
  fireEvent.change(input, { target: { value: 'Todo 2' } });
  fireEvent.click(getByText('Add Todo'));

  // Check if todos are displayed
  expect(queryByText('Todo 1')).toBeInTheDocument();
  expect(queryByText('Todo 2')).toBeInTheDocument();

  // Toggle todo
  fireEvent.click(getByLabelText('Todo 1'));
  expect(queryByText('Todo 1')).toHaveStyle('text-decoration: line-through');

  // Delete todo
  fireEvent.click(getByText('Delete'));
  expect(queryByText('Todo 1')).not.toBeInTheDocument();
});
```

In this test:

1. We render the `TodoList` component.
2. We add two todos and assert that they are displayed.
3. We toggle the first todo and assert that its style is updated to have a line-through.
4. We delete the first todo and assert that it is removed from the list.

Now, you can run the tests using Jest as before.
