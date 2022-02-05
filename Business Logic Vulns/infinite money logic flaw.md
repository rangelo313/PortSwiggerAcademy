Goal: This lab has a logic flaw in its purchasing workflow. To solve the lab, exploit this flaw to buy a "Lightweight l33t leather jacket".

In this lab, I found that I am able to use a 30% off coupon code to purchase a giftcard worth $10. However, the logic here is theres no limits to the amount of times we can use this coupon so we can get $3 off of each purchase.

1.  Go to “Project options” > “Sessions”. In the “Session handling rules” panel, click “Add”. The “Session handling rule editor” dialog opens.  
    
2.  In the dialog, go to the “Scope” tab. Under “URL Scope”, select “Include all URLs”.  
    
3.  Go back to the “Details” tab. Under “Rule actions”, click “Add” > “Run a macro”. Under “Select macro”, click “Add” again to open the Macro Recorder.  
    
4.  Select the following sequence of requests. Then, click “OK”. The Macro Editor opens.  
    `POST /cart`  
    `POST /cart/coupon`  
    `POST /cart/checkout`  
    `GET /cart/order-confirmation?order-confirmed=true`  
    `POST /gift-card`  
    
5.  In the list of requests, select `GET /cart/order-confirmation?order-confirmed=true`. Click “Configure item”. In the dialog that opens, click “Add” to create a custom parameter. Name the parameter `gift-card` and highlight the gift card code at the bottom of the response. Click “OK” twice to go back to the Macro Editor.  
    
6.  Select the `POST /gift-card` request and click “Configure item” again. In the “Parameter handling” section, use the drop-down menus to specify that the `gift-card` parameter should be derived from the prior response (response 4). Click “OK”.  
    
7.  In the Macro Editor, click “Test macro”. Look at the response to `GET /cart/order-confirmation?order-confirmation=true` and note the gift card code that was generated. Look at the `POST /gift-card` request. Make sure that the `gift-card` parameter matches and confirm that it received a `302` response. Keep clicking “OK” until you get back to the main Burp window.  
    
8.  Send the `GET /my-account` request to Burp Intruder. Use the “Sniper” attack type and clear the default payload positions.  
    
9.  On the “Payloads” tab, select the payload type “Null payloads”. Under “Payload options”, choose to generate `412` payloads. On the “Options” tab, set the thread count to `1`. Start the attack.  
    
10.  When the attack finishes, you will have enough store credit to buy the jacket and solve the lab.