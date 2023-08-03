---
title: "key concepts of react router with examples"
seoTitle: "key concepts of react router with examples"
seoDescription: "Here are some key concepts react router with examples to help you understand React Router better."
datePublished: Tue Jul 11 2023 19:02:00 GMT+0000 (Coordinated Universal Time)
cuid: cljynsh8x00080amrgxlec9m9
slug: key-concepts-of-react-router-with-examples
cover: https://cdn.hashnode.com/res/hashnode/image/stock/unsplash/yhNVwsKTSaI/upload/44fc52e26168316b5ac5d5031a614b67.jpeg
tags: react-router, reactjs, react-router-dom

---

**BrowserRouter**: React Router provides different router types. The `BrowserRouter` is the most commonly used router. It uses HTML5 history API to keep your UI in sync with the URL. Here's an example of how to use it:

```javascript
import { BrowserRouter as Router, Route, Link } from 'react-router-dom';

function App() {
  return (
    <Router>
      <div>
        <nav>
          <ul>
            <li>
              <Link to="/">Home</Link>
            </li>
            <li>
              <Link to="/about">About</Link>
            </li>
          </ul>
        </nav>

        <Route path="/" exact component={Home} />
        <Route path="/about" component={About} />
      </div>
    </Router>
  );
}

function Home() {
  return <h1>Home Page</h1>;
}

function About() {
  return <h1>About Page</h1>;
}
```

**Route**: The `Route` component is used to define a mapping between a URL path and a corresponding component to render. It takes a `path` prop to specify the URL path and a `component` prop to specify the component to render when the path matches. Here's an example:

```javascript
<Route path="/about" component={About} />
```

**Link**: The `Link` component is used to create a hyperlink to navigate between different routes. It renders an `<a>` tag with the specified destination. Here's an example:

```javascript
<Link to="/about">About</Link>
```

**Switch**: The `Switch` component is used to render only the first `Route` or `Redirect` that matches the current location. It helps to ensure that only one route is rendered at a time. Here's an example:

```javascript
import { Switch, Route } from 'react-router-dom';

// ...

<Switch>
  <Route path="/" exact component={Home} />
  <Route path="/about" component={About} />
  <Route path="/contact" component={Contact} />
</Switch>
```

**Nested Routes**: React Router allows you to nest routes by rendering child components within parent components. Here's an example:

```javascript
function App() {
  return (
    <Router>
      <div>
        <Route path="/" exact component={Home} />
        <Route path="/products" component={Products} />
      </div>
    </Router>
  );
}

function Products({ match }) {
  return (
    <div>
      <h1>Products</h1>
      <ul>
        <li>
          <Link to={`${match.url}/1`}>Product 1</Link>
        </li>
        <li>
          <Link to={`${match.url}/2`}>Product 2</Link>
        </li>
      </ul>
      <Route path={`${match.path}/:productId`} component={ProductDetails} />
    </div>
  );
}

function ProductDetails({ match }) {
  const productId = match.params.productId;
  // Fetch product details using productId

  return <h2>Product {productId} Details</h2>;
}
```

**URL Parameters**: React Router allows you to define dynamic segments in your URL paths using colon (`:`) notation. These dynamic segments can be accessed as parameters in your component. Here's an example:

```javascript
<Route path="/users/:userId" component={UserDetails} />

// ...

function UserDetails({ match }) {
  const userId = match.params.userId;
  // Fetch user details using userId

  return <h2>User Details for ID: {userId}</h2>;
}
```

These are some essential concepts to get you started with React Router. There are many more features and functionalities available, such as query parameters, redirects, and route guards. I encourage you to explore the React Router documentation for a comprehensive understanding: [**https://reactrouter.com/web/guides/quick-start**](https://reactrouter.com/web/guides/quick-start)