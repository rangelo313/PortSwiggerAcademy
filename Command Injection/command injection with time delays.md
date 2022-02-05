Goal: To solve the lab, exploit the blind OS [command injection](https://portswigger.net/web-security/os-command-injection) vulnerability to cause a 10 second delay.

1.) To test for command injection, my first step is to use the "||" characters in each field possible.

When sending a request through the feedback forum, you can see that there are three parameters. One being "name" another "email" and lastly "subject"

My first step was to use the "||" characters on the name parameter.

I realized this immediately didn't work so I tried it on the email param and got an appropriate response.

As a result, I used PortSwigger's payload using ping to make the response take 10 seconds- and crafted it accordingly to solve the lab: 

csrf=2sD5171sBdcuLREHSMQhXn6RXdpUfwMq&name=John&email=john%40gmail.com || ping+-c+10+127.0.0.1||&subject=john&message=john