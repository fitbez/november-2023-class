# **Module 1: Adding Interactivity**

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

## **Queueing a Series of State Updates**

1. **Understanding Queueing State Updates**
    - **Description**: React batches state updates for performance optimization. Understanding how multiple state updates are queued and processed is crucial.
    - **Example**:

        ```jsx
        
        import React, { useState } from 'react';
        
        function QueueUpdates() {
          const [count, setCount] = useState(0);
        
          const handleClick = () => {
            setCount(count + 1);
            setCount(count + 2);
            setCount(count + 3);
          };
        
          return (
            <div>
              <p>Count: {count}</p>
              <button onClick={handleClick}>Update Count</button>
            </div>
          );
        }
        
        ```

2. **Hands-on Exercise**: Create a component that demonstrates how React queues and processes state updates.
    - **Instructions**:
        1. Create a file named **`QueueUpdatesComponent.js`** in the **`src`** folder.
        2. In this file, create a functional component called **`QueueUpdatesComponent`** that queues multiple state updates and logs the state before and after the updates.
        3. Import and render the **`QueueUpdatesComponent`** in the **`App`** component.
    - **Starter Code** (**`QueueUpdatesComponent.js`**):

        ```jsx
        
        import React, { useState } from 'react';
        
        function QueueUpdatesComponent() {
          const [count, setCount] = useState(0);
        
          const handleClick = () => {
            console.log('Count before updates:', count);
            setCount(count + 1);
            setCount(count + 2);
            setCount(count + 3);
            console.log('Count after updates:', count);
          };
        
          return (
            <div>
              <p>Count: {count}</p>
              <button onClick={handleClick}>Update Count</button>
            </div>
          );
        }
        
        export default QueueUpdatesComponent;
        
        ```

    - **App Component** (**`App.js`**):

        ```jsx
        
        import React from 'react';
        import QueueUpdatesComponent from './QueueUpdatesComponent';
        
        function App() {
          return (
            <div className="App">
              <QueueUpdatesComponent />
            </div>
          );
        }
        
        export default App;
        
        ```

## **Updating Objects in State**

1. **Understanding Updating Objects in State**
    - **Description**: Learn how to update objects within the state without mutating the original state directly.
    - **Example**:

        ```jsx
        
        import React, { useState } from 'react';
        
        function UpdateObject() {
          const [user, setUser] = useState({ name: 'John', age: 30 });
        
          const updateAge = () => {
            setUser(prevUser => ({ ...prevUser, age: prevUser.age + 1 }));
          };
        
          return (
            <div>
              <p>Name: {user.name}</p>
              <p>Age: {user.age}</p>
              <button onClick={updateAge}>Increase Age</button>
            </div>
          );
        }
        
        ```

2. **Hands-on Exercise**: Create a component that updates an object in state.
    - **Instructions**:
        1. Create a file named **`UpdateObjectComponent.js`** in the **`src`** folder.
        2. In this file, create a functional component called **`UpdateObjectComponent`** that updates an object in state.
        3. Import and render the **`UpdateObjectComponent`** in the **`App`** component.
    - **Starter Code** (**`UpdateObjectComponent.js`**):

        ```jsx
        
        import React, { useState } from 'react';
        
        function UpdateObjectComponent() {
          const [user, setUser] = useState({ name: 'John', age: 30 });
        
          const updateAge = () => {
            // TODO: Update the user's age without mutating the original state
          };
        
          return (
            <div>
              <p>Name: {user.name}</p>
              <p>Age: {user.age}</p>
              <button onClick={updateAge}>Increase Age</button>
            </div>
          );
        }
        
        export default UpdateObjectComponent;
        
        ```

    - **App Component** (**`App.js`**):

        ```jsx
        
        import React from 'react';
        import UpdateObjectComponent from './UpdateObjectComponent';
        
        function App() {
          return (
            <div className="App">
              <UpdateObjectComponent />
            </div>
          );
        }
        
        export default App;
        
        ```

### **Updating Arrays in State**

1. **Understanding Updating Arrays in State**
    - **Description**: Learn how to update arrays within the state without mutating the original state directly.
    - **Example**:

        ```jsx
        
        import React, { useState } from 'react';
        
        function UpdateArray() {
          const [items, setItems] = useState([1, 2, 3]);
        
          const addItem = () => {
            setItems([...items, items.length + 1]);
          };
        
          return (
            <div>
              <ul>
                {items.map(item => (
                  <li key={item}>{item}</li>
                ))}
              </ul>
              <button onClick={addItem}>Add Item</button>
            </div>
          );
        }
        
        ```

2. **Hands-on Exercise**: Create a component that updates an array in state.
    - **Instructions**:
        1. Create a file named **`UpdateArrayComponent.js`** in the **`src`** folder.
        2. In this file, create a functional component called **`UpdateArrayComponent`** that updates an array in state.
        3. Import and render the **`UpdateArrayComponent`** in the **`App`** component.
    - **Starter Code** (**`UpdateArrayComponent.js`**):

        ```jsx
        
        import React, { useState } from 'react';
        
        function UpdateArrayComponent() {
          const [items, setItems] = useState([1, 2, 3]);
        
          const addItem = () => {
            // TODO: Add a new item to the items array without mutating the original state
          };
        
          return (
            <div>
              <ul>
                {items.map(item => (
                  <li key={item}>{item}</li>
                ))}
              </ul>
              <button onClick={addItem}>Add Item</button>
            </div>
          );
        }
        
        export default UpdateArrayComponent;
        
        ```

    - **App Component** (**`App.js`**):

        ```jsx
       
        import React from 'react';
        import UpdateArrayComponent from './UpdateArrayComponent';
        
        function App() {
          return (
            <div className="App">
              <UpdateArrayComponent />
            </div>
          );
        }
        
        export default App;
        
        ```
