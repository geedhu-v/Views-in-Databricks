# Views-in-Databricks

<b> Views </b> contains query definition.

There are mainly three types of Views:
1. Stored View/ View:
  a. Persisted in database.
  b. Syntax: CREATE VIEW View_name AS Query
  c. Dropped only by "DROP VIEW" command.

3. Temporary View
   a. Session scoped view
   b. CREATE TEMP VIEW View_Name AS Query
   c. Dropped when session ends. - Session refers to Opening a new notebook, detaching and reattaching to a cluster, Installing a python package and Restarting a cluster.

5. Global Temporary View
  a. Cluster scoped view
  b. CREATE GLOBAL TEMP VIEW View_Name AS QUERY
  c. Dropped when cluster ends.
