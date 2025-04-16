# Views-in-Databricks

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
