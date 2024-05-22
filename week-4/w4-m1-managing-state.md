# Module 1: Managing State

## **Reacting to Input with State**

1. **Introduction to Reacting to Input with State**
    - **Description**: Learn how to manage state in response to user inputs such as form elements and buttons.
    - **Example**:

        ```jsx
        
        import React, { useState } from 'react';
        
        function NameForm() {
          const [name, setName] = useState('');
        
          const handleChange = (event) => {
            setName(event.target.value);
          };
        
          return (
            <form>
              <label>
                Name:
                <input type="text" value={name} onChange={handleChange} />
              </label>
              <p>Hello, {name}!</p>
            </form>
          );
        }
        
        ```

2. **Hands-on Exercise**: Create a form that updates the state based on user input.
    - **Instructions**:
        1. Create a file named **`NameForm.js`** in the **`src`** folder.
        2. In this file, create a functional component called **`NameForm`** that contains a text input field.
        3. Update the state based on user input and display the input value.
        4. Import and render the **`NameForm`** component in the **`App`** component.
    - **Starter Code** (**`NameForm.js`**):

        ```jsx
        
        import React, { useState } from 'react';
        
        function NameForm() {
          const [name, setName] = useState('');
        
          const handleChange = (event) => {
            // TODO: Update the state based on user input
          };
        
          return (
            <form>
              <label>
                Name:
                <input type="text" value={name} onChange={handleChange} />
              </label>
              <p>Hello, {name}!</p>
            </form>
          );
        }
        
        export default NameForm;
        
        ```

    - **App Component** (**`App.js`**):

        ```jsx
        
        import React from 'react';
        import NameForm from './NameForm';
        
        function App() {
          return (
            <div className="App">
              <NameForm />
            </div>
          );
        }
        
        export default App;
        
        ```

### **Choosing the State Structure**

1. **Introduction to Choosing the State Structure**
    - **Description**: Learn how to decide the best structure for your state based on your application's requirements.
    - **Example**:

        ```jsx
        import React, { useState } from 'react';
        
        function Form() {
          const [formData, setFormData] = useState({
            firstName: '',
            lastName: '',
            email: ''
          });
        
          const handleChange = (event) => {
            const { name, value } = event.target;
            setFormData((prevFormData) => ({
              ...prevFormData,
              [name]: value
            }));
          };
        
          return (
            <form>
              <label>
                First Name:
                <input type="text" name="firstName" value={formData.firstName} onChange={handleChange} />
              </label>
              <label>
                Last Name:
                <input type="text" name="lastName" value={formData.lastName} onChange={handleChange} />
              </label>
              <label>
                Email:
                <input type="email" name="email" value={formData.email} onChange={handleChange} />
              </label>
              <p>{formData.firstName} {formData.lastName} ({formData.email})</p>
            </form>
          );
        }
        
        ```

2. **Hands-on Exercise**: Create a form that uses a structured state to manage multiple input fields.
    - **Instructions**:
        1. Create a file named **`UserForm.js`** in the **`src`** folder.
        2. In this file, create a functional component called **`UserForm`** that uses a structured state to manage multiple input fields.
        3. Update the state based on user input and display the input values.
        4. Import and render the **`UserForm`** component in the **`App`** component.
    - **Starter Code** (**`UserForm.js`**):

        ```jsx
        import React, { useState } from 'react';
        
        function UserForm() {
          const [formData, setFormData] = useState({
            firstName: '',
            lastName: '',
            email: ''
          });
        
          const handleChange = (event) => {
            const { name, value } = event.target;
            // TODO: Update the state based on user input
          };
        
          return (
            <form>
              <label>
                First Name:
                <input type="text" name="firstName" value={formData.firstName} onChange={handleChange} />
              </label>
              <label>
                Last Name:
                <input type="text" name="lastName" value={formData.lastName} onChange={handleChange} />
              </label>
              <label>
                Email:
                <input type="email" name="email" value={formData.email} onChange={handleChange} />
              </label>
              <p>{formData.firstName} {formData.lastName} ({formData.email})</p>
            </form>
          );
        }
        
        export default UserForm;
        
        ```

    - **App Component** (**`App.js`**):

        ```jsx
        jsxCopy code
        import React from 'react';
        import UserForm from './UserForm';
        
        function App() {
          return (
            <div className="App">
              <UserForm />
            </div>
          );
        }
        
        export default App;
        
        ```

### **Sub-Module 3: Sharing State Between Components**

1. **Introduction to Sharing State Between Components**
    - **Description**: Learn how to share state between multiple components using props and lifting state up.
    - **Example**:

        ```jsx
        jsxCopy code
        import React, { useState } from 'react';
        
        function ChildComponent({ formData, handleChange }) {
          return (
            <form>
              <label>
                First Name:
                <input type="text" name="firstName" value={formData.firstName} onChange={handleChange} />
              </label>
              <label>
                Last Name:
                <input type="text" name="lastName" value={formData.lastName} onChange={handleChange} />
              </label>
              <label>
                Email:
                <input type="email" name="email" value={formData.email} onChange={handleChange} />
              </label>
              <p>{formData.firstName} {formData.lastName} ({formData.email})</p>
            </form>
          );
        }
        
        function ParentComponent() {
          const [formData, setFormData] = useState({
            firstName: '',
            lastName: '',
            email: ''
          });
        
          const handleChange = (event) => {
            const { name, value } = event.target;
            setFormData((prevFormData) => ({
              ...prevFormData,
              [name]: value
            }));
          };
        
          return (
            <div>
              <ChildComponent formData={formData} handleChange={handleChange} />
            </div>
          );
        }
        
        ```

2. **Hands-on Exercise**: Create a parent component that shares state with a child component.
    - **Instructions**:
        1. Create files named **`ParentComponent.js`** and **`ChildComponent.js`** in the **`src`** folder.
        2. In these files, create functional components called **`ParentComponent`** and **`ChildComponent`**.
        3. Share state between **`ParentComponent`** and **`ChildComponent`** using props.
        4. Import and render the **`ParentComponent`** in the **`App`** component.
    - **Starter Code** (**`ParentComponent.js`**):

        ```jsx
        
        import React, { useState } from 'react';
        import ChildComponent from './ChildComponent';
        
        function ParentComponent() {
          const [formData, setFormData] = useState({
            firstName: '',
            lastName: '',
            email: ''
          });
        
          const handleChange = (event) => {
            const { name, value } = event.target;
            // TODO: Update the state based on user input and pass it to ChildComponent
          };
        
          return (
            <div>
              <ChildComponent formData={formData} handleChange={handleChange} />
            </div>
          );
        }
        
        export default ParentComponent;
        
        ```

    - **Starter Code** (**`ChildComponent.js`**):

        ```jsx
        
        import React from 'react';
        
        function ChildComponent({ formData, handleChange }) {
          return (
            <form>
              <label>
                First Name:
                <input type="text" name="firstName" value={formData.firstName} onChange={handleChange} />
              </label>
              <label>
                Last Name:
                <input type="text" name="lastName" value={formData.lastName} onChange={handleChange} />
              </label>
              <label>
                Email:
                <input type="email" name="email" value={formData.email} onChange={handleChange} />
              </label>
              <p>{formData.firstName} {formData.lastName} ({formData.email})</p>
            </form>
          );
        }
        
        export default ChildComponent;
        
        ```

    - **App Component** (**`App.js`**):

        ```jsx
        
        import React from 'react';
        import ParentComponent from './ParentComponent';
        
        function App() {
          return (
            <div className="App">
              <ParentComponent />
            </div>
          );
        }
        
        export default App;
        
        ```
