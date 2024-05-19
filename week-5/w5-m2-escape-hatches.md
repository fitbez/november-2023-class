# Module 2: Escape Hatches

## **Removing Effect Dependencies**

1. **Understanding Effect Dependencies**
    - **Description**: Learn how to manage dependencies in the **`useEffect`** hook to avoid unnecessary re-renders.
    - **Example**:

        ```jsx
        
        import React, { useState, useEffect } from 'react';
        
        function DependencyExample() {
          const [count, setCount] = useState(0);
          const [data, setData] = useState(null);
        
          useEffect(() => {
            fetch(`https://jsonplaceholder.typicode.com/posts/${count}`)
              .then(response => response.json())
              .then(json => setData(json));
          }, [count]);
        
          return (
            <div>
              <button onClick={() => setCount(count + 1)}>Fetch Next Data</button>
              <pre>{JSON.stringify(data, null, 2)}</pre>
            </div>
          );
        }
        
        ```

2. **Hands-on Exercise**: Create a component that fetches data based on a dependency array.
    - **Instructions**:
        1. Create a file named **`DependencyFetcher.js`** in the **`src`** folder.
        2. In this file, create a functional component called **`DependencyFetcher`** that uses the **`useEffect`** hook.
        3. Fetch data based on a dependency array.
        4. Import and render the **`DependencyFetcher`** component in the **`App`** component.
    - **Starter Code** (**`DependencyFetcher.js`**):

        ```jsx
        
        import React, { useState, useEffect } from 'react';
        
        function DependencyFetcher() {
          const [count, setCount] = useState(0);
          const [data, setData] = useState(null);
        
          useEffect(() => {
            // TODO: Fetch data based on the count value
          }, [count]);
        
          return (
            <div>
              <button onClick={() => setCount(count + 1)}>Fetch Next Data</button>
              <pre>{JSON.stringify(data, null, 2)}</pre>
            </div>
          );
        }
        
        export default DependencyFetcher;
        
        ```

    - **App Component** (**`App.js`**):

        ```jsx
        
        import React from 'react';
        import DependencyFetcher from './DependencyFetcher';
        
        function App() {
          return (
            <div className="App">
              <DependencyFetcher />
            </div>
          );
        }
        
        export default App;
        
        ```

## **Sub-Module 6: Reusing Logic with Custom Hooks**

1. **Introduction to Custom Hooks**
    - **Description**: Learn how to create and use custom hooks to reuse logic across multiple components.
    - **Example**:

        ```jsx
        
        import React, { useState, useEffect } from 'react';
        
        function useFetch(url) {
          const [data, setData] = useState(null);
        
          useEffect(() => {
            fetch(url)
              .then(response => response.json())
              .then(json => setData(json));
          }, [url]);
        
          return data;
        }
        
        function CustomHookExample() {
          const data = useFetch('https://jsonplaceholder.typicode.com/posts/1');
        
          return (
            <div>
              <pre>{JSON.stringify(data, null, 2)}</pre>
            </div>
          );
        }
        
        ```

2. **Hands-on Exercise**: Create a custom hook to fetch data and use it in a component.
    - **Instructions**:
        1. Create a file named **`useFetch.js`** in the **`src`** folder.
        2. In this file, create a custom hook called **`useFetch`** that fetches data from a given URL.
        3. Create a component that uses the **`useFetch`** hook to display data.
        4. Import and render the component in the **`App`** component.
    - **Starter Code** (**`useFetch.js`**):

        ```jsx
        
        import { useState, useEffect } from 'react';
        
        function useFetch(url) {
          const [data, setData] = useState(null);
        
          useEffect(() => {
            // TODO: Fetch data from the given URL
          }, [url]);
        
          return data;
        }
        
        export default useFetch;
        
        ```

    - **Starter Code** (**`CustomHookComponent.js`**):

        ```jsx
        
        import React from 'react';
        import useFetch from './useFetch';
        
        function CustomHookComponent() {
          const data = useFetch('https://jsonplaceholder.typicode.com/posts/1');
        
          return (
            <div>
              <pre>{JSON.stringify(data, null, 2)}</pre>
            </div>
          );
        }
        
        export default CustomHookComponent;
        
        ```

    - **App Component** (**`App.js`**):

        ```jsx
        
        import React from 'react';
        import CustomHookComponent from './CustomHookComponent';
        
        function App() {
          return (
            <div className="App">
              <CustomHookComponent />
            </div>
          );
        }
        
        export default App;
        
        ```

## **Sub-Module 7: Integrating UI with Backend Server**

1. **Introduction to Integrating UI with Backend Server**
    - **Description**: Learn how to integrate a React application with a backend server to fetch and send data.
    - **Example**:

        ```jsx
        
        import React, { useState, useEffect } from 'react';
        
        function BackendIntegration() {
          const [data, setData] = useState(null);
        
          useEffect(() => {
            fetch('https://jsonplaceholder.typicode.com/posts')
              .then(response => response.json())
              .then(json => setData(json));
          }, []);
        
          return (
            <div>
              <ul>
                {data && data.map(post => (
                  <li key={post.id}>{post.title}</li>
                ))}
              </ul>
            </div>
          );
        }
        
        ```

2. **Hands-on Exercise**: Create a component that fetches data from a backend server and displays it in a list.
    - **Instructions**:
        1. Create a file named **`PostList.js`** in the **`src`** folder.
        2. In this file, create a functional component called **`PostList`** that fetches data from a backend server.
        3. Display the fetched data in a list.
        4. Import and render the **`PostList`** component in the **`App`** component.
    - **Starter Code** (**`PostList.js`**):

        ```jsx
        
        import React, { useState, useEffect } from 'react';
        
        function PostList() {
          const [posts, setPosts] = useState([]);
        
          useEffect(() => {
            // TODO: Fetch data from the backend server and update the state
          }, []);
        
          return (
            <div>
              <ul>
                {posts.map(post => (
                  <li key={post.id}>{post.title}</li>
                ))}
              </ul>
            </div>
          );
        }
        
        export default PostList;
        
        ```

    - **App Component** (**`App.js`**):

        ```jsx
        
        import React from 'react';
        import PostList from './PostList';
        
        function App() {
          return (
            <div className="App">
              <PostList />
            </div>
          );
        }
        
        export default App;
        
        ```


