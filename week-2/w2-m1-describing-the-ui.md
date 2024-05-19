# Module 1: Describing the UI

## **Components**

1. **What are Components?**
    - **Definition and Role in React**: Components are the building blocks of a React application. They encapsulate the UI logic, allowing for reusable and manageable code.
    - **Difference Between Class and Functional Components**: Introduction to both types of components, highlighting the advantages of functional components with hooks.
    - **Example**:

        ```jsx
        // Functional Component
        function Welcome(props) {
          return <h1>Hello, {props.name}</h1>;
        }
        
        // Class Component
        class Welcome extends React.Component {
          render() {
            return <h1>Hello, {this.props.name}</h1>;
          }
        }
        
        ```

2. **Creating a Simple Component**
    - **Hands-on Exercise**: Create a functional component that displays a greeting message.
        - **Instructions**:
            1. Create a file named **`Greeting.js`** in the **`src`** folder.
            2. In this file, create a functional component called **`Greeting`** that returns a JSX element displaying "Hello, World!".
            3. Import and render the **`Greeting`** component in the **`App`** component.
        - **Starter Code** (**`Greeting.js`**):

            ```jsx
            
            import React from 'react';
            
            function Greeting() {
              // TODO: return a JSX element that displays "Hello, World!"
            }
            
            export default Greeting;
            
            ```

        - **App Component** (**`App.js`**):

            ```jsx
            
            import React from 'react';
            import Greeting from './Greeting';
            
            function App() {
              return (
                <div className="App">
                  <Greeting />
                </div>
              );
            }
            
            export default App;
            
            ```

## **Importing and Exporting Components**

1. **Importing Components**
    - **Syntax and Examples**:

        ```jsx
        jsxCopy code
        import React from 'react';
        import Welcome from './Welcome';
        
        ```

    - **Best Practices**: Organizing imports, using relative vs. absolute paths.
2. **Exporting Components**
    - **Default vs. Named Exports**:

        ```jsx
        
        // Default Export
        export default function Welcome() {
          return <h1>Hello, World!</h1>;
        }
        
        // Named Export
        export function Welcome() {
          return <h1>Hello, World!</h1>;
        }
        
        ```

    - **Examples and Use Cases**: When to use default exports vs. named exports.
3. **Hands-on Exercise**
    - Import and export components in a small project, ensuring proper usage and organization.
        - **Instructions**:
            1. Create a file named **`Welcome.js`** in the **`src`** folder.
            2. In this file, create a functional component called **`Welcome`** that returns a JSX element displaying "Hello, React!".
            3. Export the **`Welcome`** component as a default export.
            4. Import and render the **`Welcome`** component in the **`App`** component.
        - **Starter Code** (**`Welcome.js`**):

            ```jsx
            
            import React from 'react';
            
            function Welcome() {
              // TODO: return a JSX element that displays "Hello, React!"
            }
            
            export default Welcome;
            
            ```

        - **App Component** (**`App.js`**):

            ```jsx
            
            import React from 'react';
            import Welcome from './Welcome';
            
            function App() {
              return (
                <div className="App">
                  <Welcome />
                </div>
              );
            }
            
            export default App;
            
            ```

## **Writing Markup with JSX**

1. **Introduction to JSX**
    - **What is JSX?**: JSX is a syntax extension for JavaScript that looks similar to HTML and is used to describe what the UI should look like.
    - **Differences from HTML**: JSX elements must be properly closed, camelCase is used for attributes, and className is used instead of class.
2. **JSX Syntax and Rules**
    - **Embedding Expressions**:

        ```jsx
        
        const name = 'World';
        const element = <h1>Hello, {name}!</h1>;
        
        ```

    - **Common Pitfalls**: Understanding the difference between JSX and HTML, avoiding common syntax errors.
3. **Hands-on Exercise**
    - Write JSX to create a simple user profile component.
        - **Instructions**:
            1. Create a file named **`UserProfile.js`** in the **`src`** folder.
            2. In this file, create a functional component called **`UserProfile`** that returns a JSX element displaying the user's first name, last name, and avatar image.
            3. Import and render the **`UserProfile`** component in the **`App`** component.
        - **Starter Code** (**`UserProfile.js`**):

            ```jsx
            
            import React from 'react';
            
            function UserProfile() {
              const user = {
                firstName: 'John',
                lastName: 'Doe',
                avatarUrl: 'https://example.com/avatar.jpg'
              };
            
              return (
                <div>
                  {/* TODO: Add JSX to display user's first name, last name, and avatar */}
                </div>
              );
            }
            
            export default UserProfile;
            
            ```

        - **App Component** (**`App.js`**):

            ```jsx
            
            import React from 'react';
            import UserProfile from './UserProfile';
            
            function App() {
              return (
                <div className="App">
                  <UserProfile />
                </div>
              );
            }
            
            export default App;
            
            ```

## **JavaScript in JSX with Curly Braces**

1. **Using Curly Braces in JSX**
    - **Embedding JavaScript Expressions**: Using curly braces to include variables, functions, and expressions within JSX.

        ```jsx
        
        const user = { firstName: 'John', lastName: 'Doe' };
        const element = <h1>Hello, {user.firstName} {user.lastName}!</h1>;
        
        ```

2. **Practical Applications**
    - **Dynamic Values and Conditional Statements**:

        ```jsx
        
        const isLoggedIn = true;
        const greeting = <h1>{isLoggedIn ? 'Welcome back!' : 'Please sign up.'}</h1>;
        
        ```

3. **Hands-on Exercise**
    - Add dynamic content using JavaScript expressions within a JSX component.
        - **Instructions**:
            1. Create a file named **`Greeting.js`** in the **`src`** folder.
            2. In this file, create a functional component called **`Greeting`** that returns a greeting message based on the **`isLoggedIn`** prop.
            3. Import and render the **`Greeting`** component in the **`App`** component.
        - **Starter Code** (**`Greeting.js`**):

            ```jsx
            
            import React from 'react';
            
            function Greeting(props) {
              // TODO: Return a greeting message based on the isLoggedIn prop
            }
            
            export default Greeting;
            
            ```

        - **App Component** (**`App.js`**):

            ```jsx
            
            import React from 'react';
            import Greeting from './Greeting';
            
            function App() {
              return (
                <div className="App">
                  <Greeting isLoggedIn={true} />
                </div>
              );
            }
            
            export default App;
            
            ```

## **Props**

1. **Understanding Props**
    - **What are Props?**: Props are inputs to a React component. They are passed via HTML attributes and are used to pass data from one component to another.
    - **How to Pass Props to Components**:

        ```jsx
        
        function Welcome(props) {
          return <h1>Hello, {props.name}</h1>;
        }
        
        ```

2. **Default Props and PropTypes**
    - **Setting Default Props**:

        ```jsx
        
        Welcome.defaultProps = {
          name: 'Stranger'
        };
        
        ```

    - **Validating Props with PropTypes**:

        ```jsx
        
        Welcome.propTypes = {
          name: PropTypes.string
        };
        
        ```

3. **Hands-on Exercise**
    - Pass and use props in a simple greeting application, implementing default props and propTypes.
        - **Instructions**:
            1. Create a file named **`Welcome.js`** in the **`src`** folder.
            2. In this file, create a functional component called **`Welcome`** that returns a greeting message using **`props.name`**.
            3. Set default props to "Stranger" and validate props using PropTypes.
            4. Import and render the **`Welcome`** component in the **`App`** component.
        - **Starter Code** (**`Welcome.js`**):

            ```jsx
            
            import React from 'react';
            import PropTypes from 'prop-types';
            
            function Welcome(props) {
              // TODO: Return a greeting message using props.name
            }
            
            // TODO: Set default props for Welcome component
            
            // TODO: Validate props for Welcome component
            
            export default Welcome;
            
            ```

        - **App Component** (**`App.js`**):

            ```jsx
            
            import React from 'react';
            import Welcome from './Welcome';
            
            function App() {
              return (
                <div className="App">
                  <Welcome name="John" />
                </div>
              );
            }
            
            export default App;
            
            ```


