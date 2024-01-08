# Working with transactions

Transactions is a very mechanisms, which allows to make sure, that data in the database is always consitent and comply with business rules. Let's practice working with transactions! 

In this task you will work with a online shop database. The shop database is called "ShopDB", and it has the following tables:
    - "Products", which has the following columns: ID, Name, Description, Price, WarehouseAmount. 
    - "Customers", which has the following columns: ID, FirstName, LastName, Email, Address. 
    - "Orders", which has the following columtns: ID, CustomerID, Date. 
    - "OrderItems", which has the following columns: ID, OrderID, ProductID, Count.

The "ShopDB" is used by the web application. Each time customer makes a new order - application creates a new transaction to update the database according to the business rules. 

Currently, our shop has only 1 product, called "AwersomeProduct". 

## Online shop business rules 
- Customer can create new orders. 
- Order information is stored in the "Orders" table. 
- When created, order is empty
- Information about producs, added to the order is stored in the "OrderItems" table: each item in the "OrderItems" stores infomation about Product (ProductID), it's quantity in the order (Count), and a corresponding Order number (OrderID).
- When new OrderItem is being created - corresponding quantities (WarehouseAmount) of products in "Products" table should be updated. Ex. if Order contains 5 items of product "AwersomeProduct", when this order is created, "WarehouseAmount" of "AwersomeProduct" in the "Products" table should be decreased by 5. 


## Task
#### Prerequisites
- Install and confiture a MySQL database server on a Virtual Machine, connect to it with the MySQL client
- Fork this repository

#### Requirements
In this task you need to analyse the shop busines rules, and based on that, create a SQL code which creates a new order and adds product to it:  
- Connect to your database server, and create the "ShopDB" database using SQL script in the file "create-database.sql"
- If you have the "ShopDB" database on your database server already from the previous tasks - delete it using SQL statement "DROP DATABASE ShopDB;" and create it from scratch using sql query from this repository.  
- Analyse the busines rules, and decide which data in the database should be updated inside a transaction, and which data can be created without transaction
- Create a SQL code for creation of a new order in the database. 
- Order should have 1 order item: "AwersomeProduct" (ID: 1, count: 1)
- Order can be created using any date (ex. '2023-01-01')
- Order is created by customer with ID 1
- Put the solution code into the "task.sql" file, located in this repository, and submit a PR for a review.  

#### How test yourself 
Just in case you want to test your script on your own DB before submitting a PR, you can do it by performing the following actions: 
1. Run the script you wrote in the "task.sql" against your database server 
2. Make sure all tables in the database it created are empty 
3. Run script "test.sql" against your database. If the sctip execution finished without errors - you are ready to submit a PR. 
4. If you want to run tests again - you need to re-create the database in order to be able to use the "test.sql"