# E-Commerce Database

In this homework, you are going to work with an ecommerce database. In this database, you have `products` that `consumers` can buy from different `suppliers`. Customers can create an `order` and several products can be added in one order.

## Submission

Below you will find a set of tasks for you to complete to set up a database for an e-commerce app.

To submit this homework write the correct commands for each question here:
```sql


```

When you have finished all of the questions - open a pull request with your answers to the `Databases-Homework` repository.

## Setup

To prepare your environment for this homework, open a terminal and create a new database called `cyf_ecommerce`:

```sql
createdb cyf_ecommerce
```

Import the file [`cyf_ecommerce.sql`](./cyf_ecommerce.sql) in your newly created database:

```sql
\include cyf_ecommerce.sql
```

Open the file `cyf_ecommerce.sql` in VSCode and examine the SQL code. Take a piece of paper and draw the database with the different relationships between tables (as defined by the REFERENCES keyword in the CREATE TABLE commands). Identify the foreign keys and make sure you understand the full database schema.

## Task

Once you understand the database that you are going to work with, solve the following challenge by writing SQL queries using everything you learned about SQL:

1. Retrieve all the customers' names and addresses who live in the United States
SELECT name, address FROM customers WHERE country='United States';

2. Retrieve all the customers in ascending name sequence
 

3. Retrieve all the products whose name contains the word `socks`
SELECT * FROM products WHERE product_name LIKE '%socks'

4. Retrieve all the products which cost more than 100 showing product id, name, unit price and supplier id.
SELECT id, product_name, unit_price, supp_id FROM products INNER JOIN product_availability ON prod_id=id WHERE unit_price > 100;

5. Retrieve the 5 most expensive products
SELECT TOP 5 product_name FROM products INNER JOIN product_availability ON prod_id=id ORDER BY unit_price DESC;

6. Retrieve all the products with their corresponding suppliers. The result should only contain the columns `product_name`, `unit_price` and `supplier_name`
SELECT product_name, unit_price, supplier_name FROM product_availability INNER JOIN suppliers ON supp_id=supp_id INNER JOIN products ON prod_id=prod_id;

7. Retrieve all the products sold by suppliers based in the United Kingdom. The result should only contain the columns `product_name` and `supplier_name`.
 SELECT product_name, supplier_name FROM product_availability INNER JOIN suppliers ON supp_id=supp_id INNER JOIN products ON prod_id=prod_id WHERE country='United Kingdom';

8. Retrieve all orders, including order items, from customer ID `1`. Include order id, reference, date and total cost (calculated as quantity * unit price).


9. Retrieve all orders, including order items, from customer named `Hope Crosby`
SELECT * FROM ((orders INNER JOIN customers ON customer_id=customer_id) INNER JOIN order_items ON order_id=order_id) WHERE name LIKE '%Hope Crosby%';

10. Retrieve all the products in the order `ORD006`. The result should only contain the columns `product_name`, `unit_price` and `quantity`.
SELECT product_name, unit_price, quantity FROM (((order_items INNER JOIN products ON product_id=prod_id) INNER JOIN product_availability ON product_id=prod_id) INNER JOIN orders ON order_id=order_id) WHERE order_reference LIKE '%ORD006'

11. Retrieve all the products with their supplier for all orders of all customers. The result should only contain the columns `name` (from customer), `order_reference`, `order_date`, `product_name`, `supplier_name` and `quantity`.

12. Retrieve the names of all customers who bought a product from a supplier based in China.
13. List all orders giving customer name, order reference, order date and order total amount (quantity * unit price) in descending order of total.

