This lab blocks all HTML tags except custom ones.

To solve the lab, perform a cross-site scripting attack that injects a custom tag and automatically alerts document.cookie.

We first start off by going to the exploit server. Here we can craft a response.
Basically what this exploit server do is to craft a html file named ‘exploit ’, and when the victim click the URL link below: https://acbf1fbd1f0ce9db80d5084a016600ff.web-security-academy.net/exploit , it will execute the exploit html file.

The location variable inside the script tag, basically re-directs you to the website it is assigned with.
To show this, we can just insert the code:
<script>
location = “https://www.google.com"
</script>

Since we know what the location variable does let’s move on to the next part of the code.
'https://your-lab-id.web-security-academy.net/?search=

As for this lab, most of the tags have been blocked except customized ones.
id=x This is to add an id attribute named ‘x’ to the customized <xss> tag.
onfocus=alert(document.cookie) onfocus is an event attribute where it will execute the javascript code when the HTML element that it is assigned to gets focus. The javascript code:alert(document.cookie) , will be executed once the event happened.
  
  alert(document.cookie) This is just to pop up an alert showing the cookie on the particular website.
  
  tabindex=1 Tabindex attribute basically just specify the tab order of the HTML element when you use the ‘tab’ button to navigate.
  
  #x When you enter this code in the browser bar, it will focus on the html element which has the id of x, in this case, the cutomized xss was assigned the id=x.
  
  The code #x will cause the website to focus on the id ‘x’ which will trigger the event onfocus=alert(document.cookie) . This will execute the javascript alert(document.cookie) and pop-up a window showing the cookie of the webpage. Whenever you click on the URL bar and hit the tab button on your keyboard, the tabindex=1 will cause you to focus on the xss element again, thus triggering the onfocus event and execute the javascript again.
