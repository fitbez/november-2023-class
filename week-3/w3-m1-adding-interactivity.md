# **Module 1: Adding Interactivity**

## **Handling Events**

1. **Introduction to Events**
    - **Description**: Understand how to handle events in React. Events are actions taken by the user or browser, such as clicks, form submissions, or keyboard inputs.
    - **Example**:

        ```jsx
        
        function handleClick() {
          alert('Button was clicked!');
        }
        
        function App() {
          return (
            <button onClick={handleClick}>
              Click me
            </button>
          );
        }
        
        ```

2. **Hands-on Exercise**: Create a button that displays an alert when clicked.
    - **Instructions**:
        1. Create a file named **`AlertButton.js`** in the **`src`** folder.
        2. In this file, create a functional component called **`AlertButton`** that renders a button.
        3. Add an **`onClick`** event handler to the button that displays an alert with a message.
        4. Import and render the **`AlertButton`** component in the **`App`** component.
    - **Starter Code** (**`AlertButton.js`**):

        ```jsx
        
        import React from 'react';
        
        function AlertButton() {
          const handleClick = () => {
            alert('Button was clicked!');
          };
        
          return (
            <button onClick={handleClick}>
              Click Me
            </button>
          );
        }
        
        export default AlertButton;
        
        ```

    - **App Component** (**`App.js`**):

        ```jsx
        import React from 'react';
        import AlertButton from './AlertButton';
        
        function App() {
          return (
            <div className="App">
              <AlertButton />
            </div>
          );
        }
        
        export default App;
        
        ```

## **State Management**

1. **Introduction to State**
    - **Description**: State is a built-in object that is used to store property values that belong to a component. When the state object changes, the component re-renders.
    - **Example**:

        ```jsx
        
        import React, { useState } from 'react';
        
        function Counter() {
          const [count, setCount] = useState(0);
        
          return (
            <div>
              <p>You clicked {count} times</p>
              <button onClick={() => setCount(count + 1)}>
                Click me
              </button>
            </div>
          );
        }
        
        ```

2. **Hands-on Exercise**: Create a component with a state variable that changes when a button is clicked.
    - **Instructions**:
        1. Create a file named **`StateComponent.js`** in the **`src`** folder.
        2. In this file, create a functional component called **`StateComponent`** that uses the **`useState`** hook.
        3. Add a button that updates the state variable when clicked.
        4. Import and render the **`StateComponent`** in the **`App`** component.
    - **Starter Code** (**`StateComponent.js`**):

        ```jsx
        
        import React, { useState } from 'react';
        
        function StateComponent() {
          const [count, setCount] = useState(0);
        
          return (
            <div>
              <p>You clicked {count} times</p>
              <button onClick={() => setCount(count + 1)}>
                Click me
              </button>
            </div>
          );
        }
        
        export default StateComponent;
        
        ```

    - **App Component** (**`App.js`**):

        ```jsx
        
        import React from 'react';
        import StateComponent from './StateComponent';
        
        function App() {
          return (
            <div className="App">
              <StateComponent />
            </div>
          );
        }
        
        export default App;
        
        ```

## **Render and Commit**

1. **Understanding Render and Commit Phases**
    - **Description**: React works in two phases: render and commit. The render phase calculates the changes needed, and the commit phase updates the DOM.
    - **Example**:

        ```jsx
        
        // Render phase: React calculates what needs to change
        // Commit phase: React updates the DOM with the changes
        
        ```

2. **Hands-on Exercise**: Analyze the lifecycle of a component during rendering and committing.
    - **Instructions**:
        1. Create a file named **`LifecycleComponent.js`** in the **`src`** folder.
        2. In this file, create a class component called **`LifecycleComponent`** that logs messages during different lifecycle methods.
        3. Import and render the **`LifecycleComponent`** in the **`App`** component.
    -
    - **Starter Code** (**`LifecycleComponent.js`**):

        ```jsx
        
        import React, { useEffect } from 'react';
        
        function LifecycleComponent() {
          useEffect(() => {
            console.log('Component mounted');
        
            return () => {
              console.log('Component will unmount');
            };
          }, []);
        
          useEffect(() => {
            console.log('Component updated');
          });
        
          return <div>Check the console for lifecycle messages.</div>;
        }
        
        export default LifecycleComponent;
        
        ```

    - **App Component** (**`App.js`**):

        ```jsx
        
        import React from 'react';
        import LifecycleComponent from './LifecycleComponent';
        
        function App() {
          return (
            <div className="App">
              <LifecycleComponent />
            </div>
          );
        }
        
        export default App;
        
        ```

## **State as Snapshot**

1. **Understanding State as Snapshot**
    - **Description**: State in React is treated as a snapshot of the component's state at a given time. When state changes, React creates a new snapshot and re-renders the component.
    - **Example**:

        ```jsx
        
        import React, { useState } from 'react';
        
        function SnapshotExample() {
          const [count, setCount] = useState(0);
        
          const increment = () => {
            setCount(count + 1);
            console.log('Count after increment:', count);
          };
        
          return (
            <div>
              <p>Count: {count}</p>
              <button onClick={increment}>Increment</button>
            </div>
          );
        }
        
        ```

2. **Hands-on Exercise**: Create a component that demonstrates state snapshots by logging state before and after updates.
    - **Instructions**:
        1. Create a file named **`SnapshotComponent.js`** in the **`src`** folder.
        2. In this file, create a functional component called **`SnapshotComponent`** that updates state and logs the state before and after the update.
        3. Import and render the **`SnapshotComponent`** in the **`App`** component.
    - **Starter Code** (**`SnapshotComponent.js`**):

        ```jsx
        
        import React, { useState } from 'react';
        
        function SnapshotComponent() {
          const [count, setCount] = useState(0);
        
          const increment = () => {
            console.log('Count before increment:', count);
            setCount(count + 1);
            console.log('Count after increment:', count);
          };
        
          return (
            <div>
              <p>Count: {count}</p>
              <button onClick={increment}>Increment</button>
            </div>
          );
        }
        
        export default SnapshotComponent;
        
        ```

    - **App Component** (**`App.js`**):

        ```jsx
        
        import React from 'react';
        import SnapshotComponent from './SnapshotComponent';
        
        function App() {
          return (
            <div className="App">
              <SnapshotComponent />
            </div>
          );
        }
        
        export default App;
        
        ```
