Let's go through the step-by-step implementation of React Router in a React application with proper examples and explanations.

**Step 1: Installation**

First, you need to install React Router in your React project:

```bash
npm install react-router-dom
```

**Step 2: Setting up Routes**

In your React application, you need to define the routes using `BrowserRouter` and `Route` components provided by React Router. 

```javascript
// App.js

import React from 'react';
import { BrowserRouter as Router, Route, Switch } from 'react-router-dom';
import Home from './components/Home';
import About from './components/About';
import Contact from './components/Contact';
import NotFound from './components/NotFound';

function App() {
  return (
    <Router>
      <div className="App">
        <Switch>
          <Route exact path="/" component={Home} />
          <Route path="/about" component={About} />
          <Route path="/contact" component={Contact} />
          <Route component={NotFound} />
        </Switch>
      </div>
    </Router>
  );
}

export default App;
```

**Step 3: Creating Components**

Now, let's create the components for each route. For example, `Home.js`, `About.js`, `Contact.js`, and `NotFound.js`.

```javascript
// Home.js

import React from 'react';

const Home = () => {
  return (
    <div>
      <h2>Welcome to Home Page!</h2>
    </div>
  );
}

export default Home;
```

```javascript
// About.js

import React from 'react';

const About = () => {
  return (
    <div>
      <h2>About Us</h2>
      <p>We are a team of passionate developers!</p>
    </div>
  );
}

export default About;
```

```javascript
// Contact.js

import React from 'react';

const Contact = () => {
  return (
    <div>
      <h2>Contact Us</h2>
      <p>Reach out to us for any queries.</p>
    </div>
  );
}

export default Contact;
```

```javascript
// NotFound.js

import React from 'react';

const NotFound = () => {
  return (
    <div>
      <h2>404 - Page Not Found</h2>
      <p>Sorry, the page you are looking for does not exist.</p>
    </div>
  );
}

export default NotFound;
```

**Step 4: Linking to Routes**

To navigate between different routes, you can use the `Link` component provided by React Router.

```javascript
// Header.js

import React from 'react';
import { Link } from 'react-router-dom';

const Header = () => {
  return (
    <div>
      <nav>
        <ul>
          <li><Link to="/">Home</Link></li>
          <li><Link to="/about">About</Link></li>
          <li><Link to="/contact">Contact</Link></li>
        </ul>
      </nav>
    </div>
  );
}

export default Header;
```

**Step 5: Explaining the Code**

- In `App.js`, we wrap our routes inside `Router` component from React Router. The `Switch` component ensures that only one route is matched at a time.
- Each `Route` component defines a specific path and the corresponding component to render.
- If none of the paths match, the `Route` with no path specified (like the `NotFound` route) will be rendered.
- In the components, we simply define the content to be displayed for each route.
- `Link` component is used to create navigation links between routes without reloading the page.

**Step 6: Using React Router**

Now, you can use the `Header` component to navigate between different routes in your application. When you click on a link, React Router will handle the navigation and render the corresponding component.

That's it! You've successfully implemented React Router in your React application. You can now create multi-page applications with ease using React Router.
