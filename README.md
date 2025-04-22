# Databricks with sparkSQL
## Views
<b> Views </b> contains query definition. <br>
<br>
There are mainly three types of Views:<br>
1.<b> Stored View/ View </b>:<br>
  a. Persisted in database. <br>
  b. Syntax: CREATE VIEW View_name AS Query <br>
  c. Dropped only by "DROP VIEW" command.<br>
<br>
2.<b> Temporary View</b> <br>
   a. Session scoped view <br>
   b. CREATE TEMP VIEW View_Name AS Query <br>
   c. Dropped when session ends. - Session refers to Opening a new notebook, detaching and reattaching to a cluster, Installing a python package and Restarting a cluster.<br>
<br>
3. <b> Global Temporary View </b> <br>
  a. Cluster scoped view <br>
  b. CREATE GLOBAL TEMP VIEW View_Name AS QUERY<br>
  c. Dropped when cluster ends.<br>
## Operations with Tables
<b> Overwritting Coomands </b> 
<br>
1. CREATE or REPLACE TABLE Table_name <br>
   SELECT * FROM file_format.`/path/` <br>
2. INSERT OVERWRITE table_name <br>
   SELECT * FROM  file_format.`/path/` <br>

<b> Appending Commands </b> 
<br> Note: While using the Append operation, there is always a chance of duplicate records being inserted. 
<br>
1. INSERT INTO table_name <br>
    SELECT * FROM  file_format.`/path/` <br>

<b> Merging Command </b>
<br> Note: While using Merge, duplicate records are not inserted, and also when performing merge, with one transaction update, insert, and delete (UPSERT) 
all three operations are performed during a single merge transaction. <br> <br>
MERGE INTO table_name1 t1 <br>
USING table_name2 t2 <br>
on t1.id == t2.id <br>
WHEN MATACHED {....do....} <br>
WHEN NOT MATCHED {....do....}  <br>

## Advanced Transformations using SparkSQL

<b> Scenario 1: When there is a column in dataset that contains JSON string, then that can be </b>
<br>
1. Accessed using ":" sign for example: SELECT customer_id, profile:first_name, profile:address:country FROM customers; <br>
2. Can be converted to struct type using: <br>
   CREATE OR REPLACE TEMP VIEW parsed_customers AS <br>
   SELECT customer_id, from_json(profile, schema_of_json('{"first_name":"Thomas","last_name":"Lane","gender":"Male","address":{"street":"06 Boulevard Victor Hugo","city":"Paris","country":"France"}}')) AS profile_struct <br>
   FROM customers; <br>
3. After converting to struct type, nested values can be accessed using '.'. <br>
For example: SELECT customer_id, profile_struct.first_name, profile_struct.address.country FROM parsed_customers <br>
<br>
<br>
<b> Scenario 2: Splitting the collection of arrays using explode function: </b>
<br> Syntax: SELECT order_id, customer_id, explode(books) AS book FROM orders
<br>
<br>
<b> Scenario 3: Use of collect set function:</b>
<br> Syntax: SELECT customer_id,   collect_set(order_id) AS orders_set,   collect_set(books.book_id) AS books_set FROM orders GROUP BY customer_id
<br> <br>
<b> Scenario 4: use of Flatten Arrays </b>
<br> Syntax: SELECT customer_id,
  collect_set(books.book_id) As before_flatten,   array_distinct(flatten(collect_set(books.book_id))) AS after_flatten FROM orders GROUP BY customer_id

