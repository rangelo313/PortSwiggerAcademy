Goal: The lab's two factor authentication is vulnerable due to its flawed logic. To solve the lab, access Carlos's acount page. 

The following credentials were provided:
wiener:peter

With this lab- I began by investigating the 2 Factor Authentication process. In the POST /login2 request the verify parameter is set by the username.

after reading flawed 2FA verification logic by PortSwigger- I noticed this lab was similar: 

 Sometimes flawed logic in two-factor authentication means that after a user has completed the initial login step, the website doesn't adequately verify that the same user is completing the second step.
 
 As a result. I noticed that the same /login2 request is sent for MFA and aligned this with PortSwigger's notes: 
 
 This is extremely dangerous if the attacker is then able to brute-force the verification code as it would allow them to log in to arbitrary users' accounts based entirely on their username

So as a result- I sent the /login2 request to repeater and changed the verify parameter username value to carlos and sent the request to generate a MFA code for Carlos. 

I then logged into my wiener:peter account and when prompted for an MFA code I submitted an invalid code and sent the request to burpsuite.

From here, I was able to set the MFA code as a an $argument$ and bruteforce it using intruder accordingly after setting the erify parameter to carlos. I noticed when the 302 response popped up, I was able to go to the account page for carlos and solve the lab.