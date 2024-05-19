# Module 2: Describing the UI

## **Conditional Rendering**

1. **Basic Conditional Rendering**
    - **Using If-Else Statements**:

        ```jsx
        
        function Greeting(props) {
          if (props.isLoggedIn) {
            return <h1>Welcome back!</h1>;
          }
          return <h1>Please sign up.</h1>;
        }
        
        ```

    - **Ternary Operators in JSX**:

        ```jsx
        
        const greeting = props.isLoggedIn ? <h1>Welcome back!</h1> : <h1>Please sign up.</h1>;
        
        ```

2. **Advanced Conditional Rendering**
    - **Using Logical && Operator**:

        ```jsx
        
        const unreadMessages = ['React', 'Re: React', 'Re:Re: React'];
        const mailbox = (
          <div>
            <h1>Hello!</h1>
            {unreadMessages.length > 0 && <h2>You have {unreadMessages.length} unread messages.</h2>}
          </div>
        );
        
        ```

3. **Hands-on Exercise**
    - Implement conditional rendering in a login/logout application.
        - **Instructions**:
            1. Create a file named **`Greeting.js`** in the **`src`** folder.
            2. In this file, create a functional component called **`Greeting`** that returns a message based on the **`isLoggedIn`** prop.
            3. Import and render the **`Greeting`** component in the **`App`** component.
        - **Starter Code** (**`Greeting.js`**):

            ```jsx
            
            import React from 'react';
            
            function Greeting(props) {
              // TODO: Return a message based on props.isLoggedIn
            }
            
            export default Greeting;
            
            ```

        - **App Component** (**`App.js`**):

            ```jsx
            import React from 'react';
            import Greeting from './Greeting';
            
            function App() {
              const isLoggedIn = true; // Change to false to test the other condition
              return (
                <div className="App">
                  <Greeting isLoggedIn={isLoggedIn} />
                </div>
              );
            }
            
            export default App;
            
            ```

### **Rendering Lists**

1. **Rendering Lists in React**
    - **Using the map() Function**:

        ```jsx
        
        const numbers = [1, 2, 3, 4, 5];
        const listItems = numbers.map((number) =>
          <li key={number.toString()}>{number}</li>
        );
        
        ```

2. **Dynamic List Rendering**
    - **Handling Lists with Dynamic Data**: Fetching data from an API and rendering the list dynamically.

        ```jsx
        
        function NumberList(props) {
          const numbers = props.numbers;
          const listItems = numbers.map((number) =>
            <li key={number.toString()}>{number}</li>
          );
          return (
            <ul>{listItems}</ul>
          );
        }
        
        ```

3. **Hands-on Exercise**
    - Render a list of tasks from an array of data, including adding and removing tasks.
        - **Instructions**:
            1. Create a file named **`TaskList.js`** in the **`src`** folder.
            2. In this file, create a functional component called **`TaskList`** that maps over the **`tasks`** array and returns a list of task items.
            3. Import and render the **`TaskList`** component in the **`App`** component.
        - **Starter Code** (**`TaskList.js`**):

            ```jsx
            
            import React from 'react';
            
            function TaskList(props) {
              return (
                <ul>
                  {/* TODO: Map over tasks array and return a list of task items */}
                </ul>
              );
            }
            
            export default TaskList;
            
            ```

        - **App Component** (**`App.js`**):

            ```jsx
            
            import React from 'react';
            import TaskList from './TaskList';
            
            const tasks = [
              { id: 1, text: 'Learn React' },
              { id: 2, text: 'Build a project' },
              { id: 3, text: 'Apply for jobs' }
            ];
            
            function App() {
              return (
                <div className="App">
                  <TaskList tasks={tasks} />
                </div>
              );
            }
            
            export default App;
            
            ```

## **Keeping Components Pure**

1. **What is a Pure Component?**
    - **Definition and Benefits**: A pure component does not modify its props or state, ensuring predictable and testable behavior.
2. **Best Practices**
    - **Writing Pure Functional Components**: Avoid side-effects in rendering.

        ```jsx
        
        function PureComponent(props) {
          return <h1>{props.name}</h1>;
        }
        
        ```

3. **Hands-on Exercise**
    - Refactor a stateful component to be pure, ensuring no side-effects.
        - **Instructions**:
            1. Create a file named **`StatefulComponent.js`** in the **`src`** folder.
            2. In this file, create a functional component called **`StatefulComponent`** with a state that changes when a button is clicked.
            3. Refactor the **`StatefulComponent`** to be a pure functional component without state.
            4. Import and render the **`StatefulComponent`** in the **`App`** component.
        - **Starter Code** (**`StatefulComponent.js`**):

            ```jsx
            
            import React, { useState } from 'react';
            
            function StatefulComponent() {
              const [name, setName] = useState('John');
            
              return (
                <div>
                  <h1>{name}</h1>
                  <button onClick={() => setName('Jane')}>Change Name</button>
                </div>
              );
            }
            
            export default StatefulComponent;
            
            ```

        - **Refactored Code** (**`PureComponent.js`**):

            ```jsx
            
            import React from 'react';
            
            function PureComponent(props) {
              // TODO: Return a JSX element displaying the name prop
            }
            
            export default PureComponent;
            
            ```

        - **App Component** (**`App.js`**):

            ```jsx
            
            import React from 'react';
            import PureComponent from './PureComponent';
            
            function App() {
              return (
                <div className="App">
                  <PureComponent name="John" />
                </div>
              );
            }
            
            export default App;
            
            ```

## **Routing (React Router v6)**

1. **Introduction to React Router v6**
    - **Setting Up React Router**: Installation and basic setup.

        ```bash
        
        npm install react-router-dom
        
        ```

2. **Basic Routing Concepts**
    - **Creating Routes and Route Components**:

        ```jsx
        
        import { BrowserRouter as Router, Routes, Route } from 'react-router-dom';
        import Home from './Home';
        import About from './About';
        
        function App() {
          return (
            <Router>
              <Routes>
                <Route path="/" element={<Home />} />
                <Route path="about" element={<About />} />
              </Routes>
            </Router>
          );
        }
        
        ```

    - **Linking Between Routes**:

        ```jsx
        import { Link } from 'react-router-dom';
        
        function Navigation() {
          return (
            <nav>
              <Link to="/">Home</Link>
              <Link to="about">About</Link>
            </nav>
          );
        }
        
        ```

3. **Dynamic Routing**
    - **Route Parameters**:

        ```jsx
        
        import { useParams } from 'react-router-dom';
        
        function UserProfile() {
          const { id } = useParams();
          return <h1>User ID: {id}</h1>;
        }
        
        <Route path="user/:id" element={<UserProfile />} />
        
        ```

    - **Nested Routes**:

        ```jsx
        
        import { Outlet } from 'react-router-dom';
        
        function Topics() {
          return (
            <div>
              <h1>Topics</h1>
              <Outlet />
            </div>
          );
        }
        
        function TopicDetail() {
          const { topicId } = useParams();
          return <h2>Topic ID: {topicId}</h2>;
        }
        
        <Route path="topics" element={<Topics />}>
          <Route path=":topicId" element={<TopicDetail />} />
        </Route>
        
        ```

4. **Hands-on Exercise**
    - Implement routing in a sample application with multiple pages, dynamic routes, and nested routes.
        - **Instructions**:
            1. Create files named **`Home.js`**, **`About.js`**, and **`UserProfile.js`** in the **`src`** folder.
            2. In these files, create functional components called **`Home`**, **`About`**, and **`UserProfile`** that return simple JSX elements displaying their respective names.
            3. Set up routing in the **`App`** component to render these components based on the route.
            4. Add a **`Link`** component in the **`App`** component to navigate between the routes.
        - **Starter Code** (**`Home.js`**, **`About.js`**, **`UserProfile.js`**):

            ```jsx
            
            // Home.js
            import React from 'react';
            
            function Home() {
              return <h1>Home Page</h1>;
            }
            
            export default Home;
            
            ```

            ```jsx
            
            // About.js
            import React from 'react';
            
            function About() {
              return <h1>About Page</h1>;
            }
            
            export default About;
            
            ```

            ```jsx
            
            // UserProfile.js
            import React from 'react';
            import { useParams } from 'react-router-dom';
            
            function UserProfile() {
              const { id } = useParams();
              // TODO: Return a JSX element displaying the user ID
            }
            
            export default UserProfile;
            
            ```

        - **App Component** (**`App.js`**):

            ```jsx
            
            import React from 'react';
            import { BrowserRouter as Router, Routes, Route, Link } from 'react-router-dom';
            import Home from './Home';
            import About from './About';
            import UserProfile from './UserProfile';
            
            function App() {
              return (
                <Router>
                  <nav>
                    <Link to="/">Home</Link>
                    <Link to="about">About</Link>
                    <Link to="user/1">User Profile</Link>
                  </nav>
                  <Routes>
                    <Route path="/" element={<Home />} />
                    <Route path="about" element={<About />} />
                    <Route path="user/:id" element={<UserProfile />} />
                  </Routes>
                </Router>
              );
            }
            
            export default App;
            
            ```

## **Understanding the UI Tree**

1. **What is a UI Tree?**
    - **Definition and Importance**: The UI tree represents the hierarchical structure of React components.
2. **Component Hierarchy**
    - **Parent and Child Components**: Understanding relationships between components.
    - **Prop Drilling and State Management**: Techniques to manage state and pass props through the component tree.
3. **Hands-on Exercise**
    - Visualize and manage the UI tree in a sample project, ensuring efficient state management.
        - **Instructions**:
            1. Create files named **`ParentComponent.js`** and **`ChildComponent.js`** in the **`src`** folder.
            2. In these files, create functional components called **`ParentComponent`** and **`ChildComponent`**. **`ParentComponent`** should have a state variable called **`message`** and pass it as a prop to **`ChildComponent`**.
            3. Import and render the **`ParentComponent`** in the **`App`** component.
        - **Starter Code** (**`ParentComponent.js`**, **`ChildComponent.js`**):

            ```jsx
            
            // ChildComponent.js
            import React from 'react';
            
            function ChildComponent({ message }) {
              // TODO: Return a JSX element displaying the message prop
            }
            
            export default ChildComponent;
            
            ```

            ```jsx
            
            // ParentComponent.js
            import React, { useState } from 'react';
            import ChildComponent from './ChildComponent';
            
            function ParentComponent() {
              const [message, setMessage] = useState('Hello from Parent');
            
              return (
                <div>
                  <h1>Parent Component</h1>
                  <ChildComponent message={message} />
                </div>
              );
            }
            
            export default ParentComponent;
            
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
