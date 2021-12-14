In this lab, the goal is to return the number of columns with a query.

The category parameter is deemed to be vulnerable to UNION based sql injection- so I selected a category intercepted the request with Burpsuite Pro.

I modified the category parameter according to the list provided by PortSwigger's notes. This will assist by returning a 200 OK when the correct number of columns is returned.

```
?category=Gifts'+UNION+SELECT+null--            500 Internal Server Error
?category=Gifts'+UNION+SELECT+null,null--       500 Internal Server Error
?category=Gifts'+UNION+SELECT+null,null,null--  200 OK
```



As we can see the: category=Gifts'+UNION+SELECT+null,null,null--  200 OK
Is the correct query chosen.
