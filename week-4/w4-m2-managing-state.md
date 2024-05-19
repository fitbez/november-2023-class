# **Module 2: Managing State**

## **Preserving and Resetting State**

1. **Introduction to Preserving and Resetting State**
    - **Description**: Learn how to preserve and reset state in React components.
    - **Example**:

        ```jsx
        
        import React, { useState } from 'react';
        
        function PreserveStateComponent() {
          const [inputValue, setInputValue] = useState('');
          const [submittedValue, setSubmittedValue] = useState('');
        
          const handleChange = (event) => {
            setInputValue(event.target.value);
          };
        
          const handleSubmit = (event) => {
            event.preventDefault();
            setSubmittedValue(inputValue);
            setInputValue(''); // Reset input field
          };
        
          return (
            <div>
              <form onSubmit={handleSubmit}>
                <input type="text" value={inputValue} onChange={handleChange} />
                <button type="submit">Submit</button>
              </form>
              <p>Submitted Value: {submittedValue}</p>
            </div>
          );
        }
        
        ```

2. **Hands-on Exercise**: Create a component that preserves and resets state on form submission.
    - **Instructions**:
        1. Create a file named **`PreserveStateComponent.js`** in the **`src`** folder.
        2. In this file, create a functional component called **`PreserveStateComponent`** that preserves and resets state on form submission.
        3. Import and render the **`PreserveStateComponent`** in the **`App`** component.
    - **Starter Code** (**`PreserveStateComponent.js`**):

        ```jsx
        
        import React, { useState } from 'react';
        
        function PreserveStateComponent() {
          const [inputValue, setInputValue] = useState('');
          const [submittedValue, setSubmittedValue] = useState('');
        
          const handleChange = (event) => {
            // TODO: Update the input value based on user input
          };
        
          const handleSubmit = (event) => {
            event.preventDefault();
            // TODO: Update the submitted value and reset the input value
          };
        
          return (
            <div>
              <form onSubmit={handleSubmit}>
                <input type="text" value={inputValue} onChange={handleChange} />
                <button type="submit">Submit</button>
              </form>
              <p>Submitted Value: {submittedValue}</p>
            </div>
          );
        }
        
        export default PreserveStateComponent;
        
        ```

    - **App Component** (**`App.js`**):

        ```jsx
        
        import React from 'react';
        import PreserveStateComponent from './PreserveStateComponent';
        
        function App() {
          return (
            <div className="App">
              <PreserveStateComponent />
            </div>
          );
        }
        
        export default App;
        
        ```

### **Passing Data Deeply with Context**

1. **Introduction to Passing Data Deeply with Context**
    - **Description**: Learn how to use the Context API to pass data deeply through the component tree without prop drilling.
    - **Example**:

        ```jsx
        
        import React, { createContext, useState, useContext } from 'react';
        
        const UserContext = createContext();
        
        function UserProvider({ children }) {
          const [user, setUser] = useState({ name: 'John Doe', email: 'john@example.com' });
        
          return (
            <UserContext.Provider value={user}>
              {children}
            </UserContext.Provider>
          );
        }
        
        function UserProfile() {
          const user = useContext(UserContext);
          return (
            <div>
              <h1>{user.name}</h1>
              <p>{user.email}</p>
            </div>
          );
        }
        
        function App() {
          return (
            <UserProvider>
              <UserProfile />
            </UserProvider>
          );
        }
        
        export default App;
        
        ```

2. **Hands-on Exercise**: Create a context to pass user data deeply through the component tree.
    - **Instructions**:
        1. Create a file named **`UserContext.js`** to define the context and provider.
        2. Create a **`UserProvider`** component that uses the context to provide user data.
        3. Create a **`UserProfile`** component that consumes the context to display user data.
        4. Import and use the **`UserProvider`** and **`UserProfile`** components in the **`App`** component.
    - **Starter Code** (**`UserContext.js`**):

        ```jsx
        
        import React, { createContext, useState } from 'react';
        
        const UserContext = createContext();
        
        function UserProvider({ children }) {
          const [user, setUser] = useState({ name: 'John Doe', email: 'john@example.com' });
        
          return (
            <UserContext.Provider value={user}>
              {children}
            </UserContext.Provider>
          );
        }
        
        export { UserContext, UserProvider };
        
        ```

    - **Starter Code** (**`UserProfile.js`**):

        ```jsx
        
        import React, { useContext } from 'react';
        import { UserContext } from './UserContext';
        
        function UserProfile() {
          const user = useContext(UserContext);
          return (
            <div>
              <h1>{user.name}</h1>
              <p>{user.email}</p>
            </div>
          );
        }
        
        export default UserProfile;
        
        ```

- **App Component** (**`App.js`**):

    ```jsx
    
    import React from 'react';
    import { UserProvider } from './UserContext';
    import UserProfile from './UserProfile';
    
    function App() {
      return (
        <UserProvider>
          <UserProfile />
        </UserProvider>
      );
    }
    
    export default App;
    
    ```
