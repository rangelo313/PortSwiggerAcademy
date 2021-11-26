Retrieving data from other database tables
in cases where the sql query results are reutrned iwthin the apps responses an attacker can leverage a sql injection vulnerabillity to retrieve data from other tables within the database. This is done using hte UNION keyword, which lets you execute and additonal SELECT query and append teh results to the original query. 

For example, if an application executes the following query containing the user input "Gifts":

`SELECT name, description FROM products WHERE category = 'Gifts'`

then an attacker can submit the input:

`' UNION SELECT username, password FROM users--`

**SQL Injection UNION Attacks**
When an application is vulnerable to SQL injection and the results of the query are returned within the application's responses, the `UNION` keyword can be used to retrieve data from other tables within the database. This results in an SQL injection UNION attack.

The `UNION` keyword lets you execute one or more additional `SELECT` queries and append the results to the original query. For example:

`SELECT a, b FROM table1 UNION SELECT c, d FROM table2`

