---
title: "API Tutorial for Beginners in react: Learn API in 10 Minutes"
seoTitle: "Making API Call Methods in React: A Comprehensive Guide"
seoDescription: "Unlock the Power of API Calls in React: A Comprehensive Guide on Fetching, Updating, and Managing Data" - Learn how to master API call methods in React App"
datePublished: Tue Jul 25 2023 04:00:10 GMT+0000 (Coordinated Universal Time)
cuid: clkhrqnee000909mu8kxm6co9
slug: api-tutorial-for-beginners-in-react-learn-api-in-10-minutes
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1690227308167/b30ccbe5-bd90-44fc-b293-96c717a9fad0.png
ogImage: https://cdn.hashnode.com/res/hashnode/image/upload/v1690229627798/541cf856-bf49-4f00-884a-710f37ab31fc.png
tags: reactjs, graphql, beginners, axios

---

## What is API?

In web development, an API (Application Programming Interface) refers to a set of rules and protocols that allows different software applications, particularly web-based applications, to interact with each other. Web APIs are typically used to enable communication between a client-side application (e.g., a web browser) and a server-side application (e.g., a web server).

Web APIs are crucial for building dynamic and interactive web applications. They allow developers to access data, services, and functionalities from external servers or services, providing a way to integrate third-party services into their own applications. Web APIs are commonly used to retrieve data from servers, submit data to servers, and perform various operations, such as authentication and authorization.

There are different types of web APIs, and two of the most commonly used ones are:

1.**RESTful API (Representational State Transfer)**: REST is an architectural style that defines a set of constraints for building scalable and stateless web services. RESTful APIs use HTTP methods **(GET, POST, PUT, DELETE, etc.)** to perform CRUD (Create, Read, Update, Delete) operations on resources.

2.**GraphQL API**: GraphQL is a query language for APIs that allows clients to request exactly the data they need and nothing more. Unlike RESTful APIs, where the server defines the response structure, GraphQL clients can specify the shape of the response they want.

Web APIs play a crucial role in enabling modern web applications to access and interact with a wide range of services and data sources, making web development more versatile and interconnected.

## How to call API in web app(In react)?

In React, you can make API calls using various methods. Here are a few commonly used approaches:

## Fetch API:

The Fetch API is a built-in JavaScript API for making network requests. It is widely supported by modern browsers. You can use it to make HTTP requests and handle responses.

```javascript
fetch('https://api.example.com/data')
  .then(response => response.json())
  .then(data => {
    // Handle the data
  })
  .catch(error => {
    // Handle any errors
  });
```

You can also add additional options to the fetch request, such as headers, request methods (GET, POST, etc.), and request bodies.

Let's go through each example individually - GET, POST, PATCH, and DELETE using the Fetch API in a React component:

First, make sure you have the necessary imports in your React component:

```typescript
import React, { useState } from 'react';
```

**1.GET Request:**

```javascript
const DataFetcher = () => {
  const [data, setData] = useState([]);
  const [loading, setLoading] = useState(true);

  // Function to fetch data from the server using GET request
  const fetchData = async () => {
    try {
      setLoading(true);
      const response = await fetch('https://api.example.com/data'); // Replace with your API endpoint

      if (!response.ok) {
        throw new Error('Network response was not ok');
      }

      const data = await response.json();
      setData(data);
      setLoading(false);
    } catch (error) {
      console.error('Error fetching data:', error);
      setLoading(false);
    }
  };

  return (
    <div>
      <h2>Data fetched from the server:</h2>
      {loading ? (
        <div>Loading...</div>
      ) : (
        <ul>
          {data.map(item => (
            <li key={item.id}>{item.name}</li>
          ))}
        </ul>
      )}
      <button onClick={fetchData}>Fetch Data</button>
    </div>
  );
};

export default DataFetcher;
```

[**2.POST**](http://2.POST) **Request:**

```javascript
const DataFetcher = () => {
  const [data, setData] = useState([]);
  const [loading, setLoading] = useState(true);

  // Function to add data to the server using POST request
  const addData = async () => {
    try {
      setLoading(true);
      const response = await fetch('https://api.example.com/data', {
        method: 'POST',
        headers: {
          'Content-Type': 'application/json',
        },
        body: JSON.stringify({
          name: 'John Doe',
          age: 30,
          email: 'john.doe@example.com',
        }),
      });

      if (!response.ok) {
        throw new Error('Network response was not ok');
      }

      const responseData = await response.json();
      setData(prevData => [...prevData, responseData]);
      setLoading(false);
    } catch (error) {
      console.error('Error adding data:', error);
      setLoading(false);
    }
  };

  return (
    <div>
      <button onClick={addData}>Add Data</button>
    </div>
  );
};

export default DataFetcher;
```

**3.PATCH Request:**

```javascript
const DataFetcher = () => {
  const [data, setData] = useState([]);
  const [loading, setLoading] = useState(true);

  // Function to update data on the server using PATCH request
  const updateData = async () => {
    try {
      setLoading(true);
      const response = await fetch('https://api.example.com/data/1', { // Replace '1' with the ID of the data you want to update
        method: 'PATCH',
        headers: {
          'Content-Type': 'application/json',
        },
        body: JSON.stringify({
          name: 'Updated John Doe',
          age: 31,
          email: 'updated.john.doe@example.com',
        }),
      });

      if (!response.ok) {
        throw new Error('Network response was not ok');
      }

      const responseData = await response.json();
      setData(responseData); // Assuming the response is the updated data object
      setLoading(false);
    } catch (error) {
      console.error('Error updating data:', error);
      setLoading(false);
    }
  };

  return (
    <div>
      <button onClick={updateData}>Update Data</button>
    </div>
  );
};

export default DataFetcher;
```

**4.DELETE Request:**

```javascript
const DataFetcher = () => {
  const [data, setData] = useState([]);
  const [loading, setLoading] = useState(true);

  // Function to delete data from the server using DELETE request
  const deleteData = async () => {
    try {
      setLoading(true);
      const response = await fetch('https://api.example.com/data/1', { // Replace '1' with the ID of the data you want to delete
        method: 'DELETE',
      });

      if (!response.ok) {
        throw new Error('Network response was not ok');
      }

      setData(prevData => prevData.filter(item => item.id !== 1)); // Assuming the data is an array with 'id' property
      setLoading(false);
    } catch (error) {
      console.error('Error deleting data:', error);
      setLoading(false);
    }
  };

  return (
    <div>
      <button onClick={deleteData}>Delete Data</button>
    </div>
  );
};

export default DataFetcher;
```

## Axios:

Axios is a popular third-party library for making HTTP requests from JavaScript. It provides a simple and intuitive API with features like request cancellation, automatic JSON parsing, and request/response interceptors.

First, install Axios by running npm install axios or yarn add axios. Then, you can use Axios to make API calls in your React components:

```javascript
import axios from 'axios';

axios.get('https://api.example.com/data')
  .then(response => {
    const data = response.data;
    // Handle the data
  })
  .catch(error => {
    // Handle any errors
  });
```

Axios also supports other HTTP methods like POST, PUT, DELETE, etc., which you can use based on your API requirements.

Let's go through each example - GET, POST, PATCH, and DELETE using Axios in a React component

First, make sure you have the necessary imports in your React component:

```typescript
import React, { useState } from 'react';
import axios from 'axios';
```

**1.GET Request:**

```javascript
const DataFetcher = () => {
  const [data, setData] = useState([]);
  const [loading, setLoading] = useState(true);

  // Function to fetch data from the server using GET request
  const fetchData = async () => {
    try {
      setLoading(true);
      const response = await axios.get('https://api.example.com/data'); // Replace with your API endpoint

      setData(response.data);
      setLoading(false);
    } catch (error) {
      console.error('Error fetching data:', error);
      setLoading(false);
    }
  };

  return (
    <div>
      <h2>Data fetched from the server:</h2>
      {loading ? (
        <div>Loading...</div>
      ) : (
        <ul>
          {data.map(item => (
            <li key={item.id}>{item.name}</li>
          ))}
        </ul>
      )}
      <button onClick={fetchData}>Fetch Data</button>
    </div>
  );
};

export default DataFetcher;
```

[**2.POST**](http://2.POST) **Request:**

```javascript
const DataFetcher = () => {
  const [data, setData] = useState([]);
  const [loading, setLoading] = useState(true);

  // Function to add data to the server using POST request
  const addData = async () => {
    try {
      setLoading(true);
      const response = await axios.post('https://api.example.com/data', {
        name: 'John Doe',
        age: 30,
        email: 'john.doe@example.com',
      });

      setData(prevData => [...prevData, response.data]);
      setLoading(false);
    } catch (error) {
      console.error('Error adding data:', error);
      setLoading(false);
    }
  };

  return (
    <div>
      <button onClick={addData}>Add Data</button>
    </div>
  );
};

export default DataFetcher;
```

**3.PATCH Request:**

```javascript
const DataFetcher = () => {
  const [data, setData] = useState([]);
  const [loading, setLoading] = useState(true);

  // Function to update data on the server using PATCH request
  const updateData = async () => {
    try {
      setLoading(true);
      const response = await axios.patch('https://api.example.com/data/1', { // Replace '1' with the ID of the data you want to update
        name: 'Updated John Doe',
        age: 31,
        email: 'updated.john.doe@example.com',
      });

      setData(response.data);
      setLoading(false);
    } catch (error) {
      console.error('Error updating data:', error);
      setLoading(false);
    }
  };

  return (
    <div>
      <button onClick={updateData}>Update Data</button>
    </div>
  );
};

export default DataFetcher;
```

**4.DELETE Request:**

```javascript
const DataFetcher = () => {
  const [data, setData] = useState([]);
  const [loading, setLoading] = useState(true);

  // Function to delete data from the server using DELETE request
  const deleteData = async () => {
    try {
      setLoading(true);
      const response = await axios.delete('https://api.example.com/data/1'); // Replace '1' with the ID of the data you want to delete

      setData(prevData => prevData.filter(item => item.id !== 1)); // Assuming the data is an array with 'id' property
      setLoading(false);
    } catch (error) {
      console.error('Error deleting data:', error);
      setLoading(false);
    }
  };

  return (
    <div>
      <button onClick={deleteData}>Delete Data</button>
    </div>
  );
};

export default DataFetcher;
```

## GraphQL:

If you're working with a GraphQL API, you can use libraries like Apollo Client or Relay to make API calls. These libraries provide powerful features for working with GraphQL, including caching, optimistic updates, and subscription support.

Here's an example of using Apollo Client in a React component:

```typescript
import { useQuery } from '@apollo/client';
import { GET_DATA } from './queries';

const MyComponent = () => {
  const { loading, error, data } = useQuery(GET_DATA);

  if (loading) {
    return <p>Loading...</p>;
  }

  if (error) {
    return <p>Error: {error.message}</p>;
  }

  // Handle the data
  return (
    <div>
      <h1>{data.title}</h1>
      {/* Render the rest of the component */}
    </div>
  );
};
```

In this example, GET\_DATA is a GraphQL query defined using the GraphQL Tag library. The useQuery hook executes the query and provides the loading state, error, and data in the component.

Let's go through each example - **GET, POST, PATCH, and DELETE** using GraphQL with Apollo Client in a React component:

First, make sure you have the necessary imports and dependencies in your React component:

```javascript
npm install @apollo/client graphql
```

Now, let's go through each example using GraphQL with Apollo Client in a React component:

```javascript
import React from 'react';
import { ApolloClient, InMemoryCache, ApolloProvider, useQuery, gql } from '@apollo/client';

const API_URL = 'https://api.example.com/graphql'; // Replace with your GraphQL server URL

// Initialize ApolloClient
const client = new ApolloClient({
  uri: API_URL,
  cache: new InMemoryCache(),
});

const DataFetcher = () => {
  // GraphQL query for fetching data
  const GET_DATA = gql`
    query {
      getData {
        id
        name
      }
    }
  `;

  // GraphQL mutation for adding data
  const ADD_DATA = gql`
    mutation {
      createData(input: {
        name: "John Doe"
        age: 30
        email: "john.doe@example.com"
      }) {
        id
        name
      }
    }
  `;

  // GraphQL mutation for updating data
  const UPDATE_DATA = gql`
    mutation {
      updateData(id: 1, input: {
        name: "Updated John Doe"
        age: 31
        email: "updated.john.doe@example.com"
      }) {
        id
        name
      }
    }
  `;

  // GraphQL mutation for deleting data
  const DELETE_DATA = gql`
    mutation {
      deleteData(id: 1) {
        id
        name
      }
    }
  `;

  // Fetch data using useQuery hook
  const { loading, error, data } = useQuery(GET_DATA);

  // Add data using useMutation hook
  const [addData] = useMutation(ADD_DATA);

  // Update data using useMutation hook
  const [updateData] = useMutation(UPDATE_DATA);

  // Delete data using useMutation hook
  const [deleteData] = useMutation(DELETE_DATA);

  return (
    <div>
      <h2>Data fetched from the server:</h2>
      {loading ? (
        <div>Loading...</div>
      ) : (
        <ul>
          {data.getData.map(item => (
            <li key={item.id}>{item.name}</li>
          ))}
        </ul>
      )}
      <button onClick={() => addData()}>Add Data</button>
      <button onClick={() => updateData()}>Update Data</button>
      <button onClick={() => deleteData()}>Delete Data</button>
    </div>
  );
};

const App = () => {
  return (
    <ApolloProvider client={client}>
      <DataFetcher />
    </ApolloProvider>
  );
};

export default App;
```

These are just a few examples of how you can make API calls in React. Depending on your specific needs, you might explore other libraries or frameworks like SWR, Superagent, or the built-in XMLHttpRequest. Choose the approach that best fits your project requirements and preferences.

## Realtime example

%[https://codesandbox.io/embed/api-call-methods-in-react-mkyw8w?fontsize=14&hidenavigation=1&theme=dark] 

  
Thanks for reading :)

---

**My cool articles list:**  
[15 Advanced TypeScript Tips for Development](https://lakshmananarumugam.com/15-advanced-typescript-tips-for-development)

[Architecture: Web app\[front-end\] from scratch](https://lakshmananarumugam.com/architecture-web-appfront-end-from-scratch-2021)

[Beyond Tradition: Innovating with Component-Driven Development](https://lakshmananarumugam.com/beyond-tradition-innovating-with-component-driven-development-in-react-typescript)