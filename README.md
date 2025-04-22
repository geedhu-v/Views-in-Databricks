# Views-in-Databricks and Different Operations with Tables
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
<br> all three operations are performed during a single merge transaction.
<br>
MERGE INTO table_name1 t1 <br>
USING table_name2 t2 <br>
on t1.id == t2.id <br>
WHEN MATACHED {....do....} <br>
WHEN NOT MATCHED {....do....}  <br>
