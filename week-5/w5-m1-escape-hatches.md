# Module 4: Escape Hatches

## **Referencing Values with Refs**

1. **Introduction to Refs**
    - **Description**: Learn how to use the **`useRef`** hook to reference values that do not cause re-renders when changed.
    - **Example**:

        ```jsx
        
        import React, { useRef } from 'react';
        
        function RefExample() {
          const inputRef = useRef(null);
        
          const focusInput = () => {
            inputRef.current.focus();
          };
        
          return (
            <div>
              <input ref={inputRef} type="text" />
              <button onClick={focusInput}>Focus Input</button>
            </div>
          );
        }
        
        ```

2. **Hands-on Exercise**: Create a component that uses a ref to focus an input field when a button is clicked.
    - **Instructions**:
        1. Create a file named **`FocusInput.js`** in the **`src`** folder.
        2. In this file, create a functional component called **`FocusInput`** that uses the **`useRef`** hook.
        3. Add a button that focuses the input field when clicked.
        4. Import and render the **`FocusInput`** component in the **`App`** component.
    - **Starter Code** (**`FocusInput.js`**):

        ```jsx
        
        import React, { useRef } from 'react';
        
        function FocusInput() {
          const inputRef = useRef(null);
        
          const focusInput = () => {
            // TODO: Use the ref to focus the input field
          };
        
          return (
            <div>
              <input ref={inputRef} type="text" />
              <button onClick={focusInput}>Focus Input</button>
            </div>
          );
        }
        
        export default FocusInput;
        
        ```

    - **App Component** (**`App.js`**):

        ```jsx
        
        import React from 'react';
        import FocusInput from './FocusInput';
        
        function App() {
          return (
            <div className="App">
              <FocusInput />
            </div>
          );
        }
        
        export default App;
        
        ```

## **Sub-Module 2: Manipulating the DOM with Refs**

1. **Introduction to DOM Manipulation with Refs**
    - **Description**: Learn how to manipulate the DOM directly using refs in React.
    - **Example**:

        ```jsx
        import React, { useRef } from 'react';
        
        function DomManipulation() {
          const divRef = useRef(null);
        
          const changeColor = () => {
            divRef.current.style.backgroundColor = 'yellow';
          };
        
          return (
            <div>
              <div ref={divRef} style={{ width: '100px', height: '100px', backgroundColor: 'blue' }}></div>
              <button onClick={changeColor}>Change Color</button>
            </div>
          );
        }
        
        ```

2. **Hands-on Exercise**: Create a component that changes the background color of a div when a button is clicked.
    - **Instructions**:
        1. Create a file named **`ChangeColor.js`** in the **`src`** folder.
        2. In this file, create a functional component called **`ChangeColor`** that uses the **`useRef`** hook.
        3. Add a button that changes the background color of the div when clicked.
        4. Import and render the **`ChangeColor`** component in the **`App`** component.
    - **Starter Code** (**`ChangeColor.js`**):

        ```jsx
        
        import React, { useRef } from 'react';
        
        function ChangeColor() {
          const divRef = useRef(null);
        
          const changeColor = () => {
            // TODO: Use the ref to change the background color of the div
          };
        
          return (
            <div>
              <div ref={divRef} style={{ width: '100px', height: '100px', backgroundColor: 'blue' }}></div>
              <button onClick={changeColor}>Change Color</button>
            </div>
          );
        }
        
        export default ChangeColor;
        
        ```

    - **App Component** (**`App.js`**):

        ```jsx
        
        import React from 'react';
        import ChangeColor from './ChangeColor';
        
        function App() {
          return (
            <div className="App">
              <ChangeColor />
            </div>
          );
        }
        
        export default App;
        
        ```

## **Sub-Module 3: Synchronizing with Effects**

1. **Introduction to Effects**
    - **Description**: Learn how to use the **`useEffect`** hook to synchronize with external systems.
    - **Example**:

        ```jsx
        
        import React, { useState, useEffect } from 'react';
        
        function EffectExample() {
          const [count, setCount] = useState(0);
        
          useEffect(() => {
            document.title = `Count: ${count}`;
          }, [count]);
        
          return (
            <div>
              <p>Count: {count}</p>
              <button onClick={() => setCount(count + 1)}>Increment</button>
            </div>
          );
        }
        
        ```

2. **Hands-on Exercise**: Create a component that updates the document title with the current count.
    - **Instructions**:
        1. Create a file named **`TitleUpdater.js`** in the **`src`** folder.
        2. In this file, create a functional component called **`TitleUpdater`** that uses the **`useEffect`** hook.
        3. Update the document title with the current count.
        4. Import and render the **`TitleUpdater`** component in the **`App`** component.
    - **Starter Code** (**`TitleUpdater.js`**):

        ```jsx
        
        import React, { useState, useEffect } from 'react';
        
        function TitleUpdater() {
          const [count, setCount] = useState(0);
        
          useEffect(() => {
            // TODO: Update the document title with the current count
          }, [count]);
        
          return (
            <div>
              <p>Count: {count}</p>
              <button onClick={() => setCount(count + 1)}>Increment</button>
            </div>
          );
        }
        
        export default TitleUpdater;
        
        ```

    - **App Component** (**`App.js`**):

        ```jsx
        
        import React from 'react';
        import TitleUpdater from './TitleUpdater';
        
        function App() {
          return (
            <div className="App">
              <TitleUpdater />
            </div>
          );
        }
        
        export default App;
        
        ```

## **Sub-Module 4: Lifecycle of Reactive Effects**

1. **Understanding the Lifecycle of Effects**
    - **Description**: Learn about the lifecycle of effects and how to manage them in functional components.
    - **Example**:

        ```jsx
        
        import React, { useState, useEffect } from 'react';
        
        function LifecycleExample() {
          const [data, setData] = useState(null);
        
          useEffect(() => {
            console.log('Effect runs on mount');
        
            fetch('https://jsonplaceholder.typicode.com/posts/1')
              .then(response => response.json())
              .then(json => setData(json));
        
            return () => {
              console.log('Effect cleanup on unmount');
            };
          }, []);
        
          return (
            <div>
              <pre>{JSON.stringify(data, null, 2)}</pre>
            </div>
          );
        }
        
        ```

2. **Hands-on Exercise**: Create a component that fetches data on mount and cleans up on unmount.
    - **Instructions**:
        1. Create a file named **`DataFetcher.js`** in the **`src`** folder.
        2. In this file, create a functional component called **`DataFetcher`** that uses the **`useEffect`** hook.
        3. Fetch data on mount and log a cleanup message on unmount.
        4. Import and render the **`DataFetcher`** component in the **`App`** component.
    - **Starter Code** (**`DataFetcher.js`**):

        ```jsx
        
        import React, { useState, useEffect } from 'react';
        
        function DataFetcher() {
          const [data, setData] = useState(null);
        
          useEffect(() => {
            // TODO: Fetch data on mount and log a cleanup message on unmount
          }, []);
        
          return (
            <div>
              <pre>{JSON.stringify(data, null, 2)}</pre>
            </div>
          );
        }
        
        export default DataFetcher;
        
        ```

    - **App Component** (**`App.js`**):

        ```jsx
        
        import React from 'react';
        import DataFetcher from './DataFetcher';
        
        function App() {
          return (
            <div className="App">
              <DataFetcher />
            </div>
          );
        }
        
        export default App;
        
        ```
