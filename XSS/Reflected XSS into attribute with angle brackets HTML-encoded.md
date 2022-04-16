XSS in HTML tag attributes
When the XSS context is into an HTML tag attribute value, you might sometimes be able to terminate the attribute value, close the tag, and introduce a new one. For example:

"><script>alert(document.domain)</script>
More commonly in this situation, angle brackets are blocked or encoded, so your input cannot break out of the tag in which it appears. Provided you can terminate the attribute value, you can normally introduce a new attribute that creates a scriptable context, such as an event handler. For example:

" autofocus onfocus=alert(document.domain) x="
The above payload creates an onfocus event that will execute JavaScript when the element receives the focus, and also adds the autofocus attribute to try to trigger the onfocus event automatically without any user interaction. Finally, it adds x=" to gracefully repair the following markup.


" autofocus onfocus=alert(document.domain) x="'
"onmouseover="alert(1)



1. So for this lab I was a little bit confused about what it meant to perform reflected xss into attribute so I took a stab
2. The recommneded approach is to use the search utility to look for anything you'd like in this regard I did "foo"
3. After this, if you search and view the src code of the website- it will set the variable in doublequotes like so:
4.  value="foo"
5.   <input type=text placeholder='Search the blog...' name=search value="FOO">
6.  we need to close double-quotes value “ and after that, we can use any event we need like onmouseover , onclick etc, you can found this event in the Cross-site scripting (XSS) cheat sheet.
7.  "onmouseover="alert(1)
