# Build a REST API using Node, Express, and MySQL

### **Student Guide to Building a REST API**

### **Tools and Technologies**

- **Node.js**: A JavaScript runtime built on Chrome's V8 JavaScript engine.
- **Express**: A fast, unopinionated, minimalist web framework for Node.js.
- **Sequelize**: A promise-based Node.js ORM for Postgres, MySQL, MariaDB, SQLite, and Microsoft SQL Server.
- **MySQL**: A popular relational database management system.

### **Prerequisites**

- Install Node.js from [nodejs.org](https://nodejs.org/)
- Install MySQL from [MySQL's official site](https://dev.mysql.com/downloads/mysql/)
- Basic knowledge of JavaScript and SQL.

### **Step 1: Set Up Your Project Environment**

1. **Create a New Directory**:
Open your terminal or command prompt and run:
    
    ```bash
    
    mkdir my-api
    cd my-api
    ```
    
2. **Initialize a Node.js Project**:
Start a new Node.js project by running:
    
    ```bash
    
    npm init -y
    ```
    
    This creates a **`package.json`** file which will manage all your dependencies.
    
3. **Install Dependencies**:
Install Express, Sequelize, and MySQL driver by running:
    
    ```bash
    
    npm install express sequelize mysql2 body-parser
    ```
    

### **Step 2: Configure MySQL**

1. **Create a MySQL Database**:
Open MySQL command line or use a GUI like MySQL Workbench and run:
    
    ```sql
    
    CREATE DATABASE sampledb;
    
    ```
    
2. **Create a MySQL User** (optional):
For security, create a new user for your application.
    
    ```sql
    
    CREATE USER 'newuser'@'localhost' IDENTIFIED BY 'password';
    GRANT ALL PRIVILEGES ON sampledb.* TO 'newuser'@'localhost';
    
    ```
    

### **Step 3: Set Up Sequelize**

1. **Configure Sequelize**:
Create a file named **`database.js`** in your project directory:
    
    ```jsx
    
    const { Sequelize } = require('sequelize');
    
    const sequelize = new Sequelize('sampledb', 'newuser', 'password', {
        host: 'localhost',
        dialect: 'mysql'
    });
    
    sequelize.authenticate().then(() => console.log('Database connected.'))
    .catch(err => console.error('Unable to connect:', err));
    
    module.exports = sequelize;
    
    ```
    
2. **Define a Model**:
Create a model file **`user.js`**:
    
    ```jsx
    
    const { DataTypes } = require('sequelize');
    const sequelize = require('./database');
    
    const User = sequelize.define('User', {
        name: DataTypes.STRING,
        email: {
            type: DataTypes.STRING,
            unique: true
        }
    });
    
    User.sync(); // This line ensures the table is created if it doesn't exist already
    
    module.exports = User;
    
    ```
    

### **Step 4: Build Your API**

1. **Create an Express Server**:
In your project root, create **`app.js`**:
    
    ```jsx
    
    const express = require('express');
    const bodyParser = require('body-parser');
    const User = require('./user');
    
    const app = express();
    app.use(bodyParser.json());
    
    app.get('/users', async (req, res) => {
        const users = await User.findAll();
        res.json(users);
    });
    
    app.post('/users', async (req, res) => {
        try {
            const user = await User.create(req.body);
            res.status(201).send(user);
        } catch (error) {
            res.status(400).send(error);
        }
    });
    
    app.listen(3000, () => console.log('Server started on port 3000.'));
    
    ```
    
### **Step 5: Test Your API**

1. **Run Your Server**:
Start your server by running:
    
    ```bash
    
    node app.js
    
    ```
    
2. **Test API Endpoints**:
Use a tool like `Postman` or a VS code extension like `ThunderClient`