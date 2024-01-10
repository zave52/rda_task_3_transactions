# Working With Transactions


Transactions allow us to ensure that data in the database is always consistent and complies with business rules. Let's practice working with them! In this task, you will work with a `ShopDB` online shop database, which has the following tables:


    - `Products`, which has the following columns: `ID`, `Name`, `Description`, `Price`, and `WarehouseAmount`. 
    - `Customers`, which has the following columns: `ID`, `FirstName`, `LastName`, `Email`, and `Address`. 
    - `Orders`, which has the following columns: `ID`, `CustomerID`, and `Date`.
    - `OrderItems`, which has the following columns: `ID`, `OrderID`, and `ProductID`.


The `ShopDB` is used by the web application. Each time a customer orders, the application creates a new transaction to update the database according to the business rules.  


Currently, our shop has only 1 product, called `AwersomeProduct`.


## Online Shop Business Rules


- Customers can create new orders. 
- Order information is stored in the `Orders` table. 
- When created, a new order is empty.
- Information about products added to the order is stored in the `OrderItems` table: each item in the `OrderItems` stores information about the product (`ProductID`), its quantity in the order (`Count`), and a corresponding order number (`OrderID`).
- When a new `OrderItem` is being created, corresponding quantities (`WarehouseAmount`) of products in the `Products` table should be updated. For example, if an order contains `5` items of the `AwersomeProduct` product, when this order is created, `WarehouseAmount` of `AwersomeProduct` in the `Products` table should be decreased by `5`. 


## Task


### Prerequisites


1. Install and configure a MySQL database server on a Virtual Machine, connect to it with the MySQL client.
2. Fork this repository.


### Requirements


In this task, you need to analyze the shop business rules and, based on that, create an SQL code that creates a new order and adds a product to it:
  
- Connect to your database server, and create the `ShopDB` database using SQL script in the `create-database.sql` file.
- If you already have the `ShopDB` database on your database server from the previous tasks, delete it using the "DROP DATABASE ShopDB;"  statement and create it from scratch using SQL query from this repository.  
- Analyze the business rules and decide which data in the database should be updated inside a transaction and which data can be created without a transaction.
- Create an SQL code to create a new order in the database. 
- Order should have one order item: `AwersomeProduct` (*ID: 1, count: 1*).
- Order can be created using any date, for example, `2023-01-01`.
- Order is created by customer with `ID 1`.
- Put the solution code into the `task.sql` file in this repository and submit a pull request for a review.


### How to Test Yourself


Just in case you want to test your script on your database before submitting a pull request, you can do it by performing the following actions: 


1. Run the script you wrote in the `task.sql` on your database server.
2. Make sure all tables in the database are empty.
3. Run the `test.sql` script on your database. If the script execution is finished without errors, you are ready to submit a pull request. 
4. If you want to rerun tests, you need to recreate the database to be able to use the `test.sql` file.
