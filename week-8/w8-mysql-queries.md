### **1. Creating a Database**

First, create a database for your products.

```sql
CREATE DATABASE example_database;

```

### **2. Creating a Table**

Create a table named **`products`** with fields for product details.

```sql
sqlCopy code
CREATE TABLE products (
    product_id INT AUTO_INCREMENT PRIMARY KEY,
    product_name VARCHAR(100),
    category VARCHAR(50),
    price DECIMAL(10, 2),
    quantity INT,
    date_added DATE
);

```

### **3. Inserting Data into a Table**

Insert some records into the **`products`** table.

```sql
INSERT INTO products (product_name, category, price, quantity, date_added) VALUES
('Laptop', 'Electronics', 1200.00, 30, '2023-04-20'),
('Smartphone', 'Electronics', 800.00, 50, '2023-04-22'),
('Desk Chair', 'Furniture', 150.00, 20, '2023-04-25');

```

### **4. Selecting Data**

Retrieve all records from the **`products`** table.

```sql

SELECT * FROM products;

```

### **5. Updating Data**

Update a record in the **`products`** table, such as changing the quantity.

```sql

UPDATE products SET quantity = 25 WHERE product_id = 3;

```

### **6. Deleting Data**

Delete a record from the **`products`** table.

```sql

DELETE FROM products WHERE product_id = 3;

```

### **7. Filtering Data**

Select records with specific criteria, such as all electronics.

```sql

SELECT * FROM products WHERE category = 'Electronics';

```

### **8. Sorting Data**

Sort data by price in descending order.

```sql

SELECT * FROM products ORDER BY price DESC;

```

### **9. Counting Rows**

Count the number of products in a specific category.

```sql

SELECT COUNT(*) FROM products WHERE category = 'Electronics';

```

### **10. Grouping Data**

Group data and calculate total quantities by category.

```sql

SELECT category, SUM(quantity) AS total_quantity FROM products GROUP BY category;

```

### **11. Joining Tables**

If you have another table related to **`products`**, like **`suppliers`**, you can join them to see more comprehensive data.

First, create the **`suppliers`** table and insert data:

```sql

CREATE TABLE suppliers (
    supplier_id INT AUTO_INCREMENT PRIMARY KEY,
    supplier_name VARCHAR(100),
    contact_name VARCHAR(100)
);

INSERT INTO suppliers (supplier_name, contact_name) VALUES
('TechGadgets Inc.', 'John Doe'),
('OfficeComfort Ltd.', 'Jane Smith');

SELECT p.product_name, p.category, p.price, s.supplier_name
FROM products p
JOIN suppliers s ON p.product_id = s.supplier_id;

```