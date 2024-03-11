Here are some JavaScript ES6 features commonly used in React with code examples and explanations:

1. **Arrow Functions**: Arrow functions provide a concise syntax to write function expressions. They are often used in React to preserve the context of `this`.

```javascript
// ES5
var handleClick = function() {
  console.log('Button clicked');
};

// ES6
const handleClick = () => {
  console.log('Button clicked');
};
```

2. **Classes**: React components can be defined as classes. Classes in ES6 are a blueprint for creating objects.

```javascript
class MyComponent extends React.Component {
  render() {
    return <h1>Hello, world!</h1>;
  }
}
```

3. **Template Literals**: Template literals are string literals allowing embedded expressions.

```javascript
const name = 'John';
console.log(`Hello, ${name}!`); // Output: "Hello, John!"
```

4. **Destructuring Assignment**: Destructuring allows you to unpack values from arrays, or properties from objects, into distinct variables.

```javascript
const props = {firstName: 'John', lastName: 'Doe'};

// ES5
var firstName = props.firstName;
var lastName = props.lastName;

// ES6
const {firstName, lastName} = props;
```

5. **Spread Operator**: The spread operator allows an iterable to expand in places where zero or more arguments or elements are expected.

```javascript
const oldArray = [1, 2, 3];
const newArray = [...oldArray, 4, 5]; // [1, 2, 3, 4, 5]
```

6. **Promises and Async/Await**: Promises are used for asynchronous programming. Async/Await is a special syntax to work with promises in a more comfortable fashion.

```javascript
const getData = async () => {
  const response = await fetch('https://api.example.com/data');
  const data = await response.json();
  console.log(data);
};
```

Happy coding! 🚀
