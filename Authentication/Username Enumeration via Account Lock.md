Goal: This lab is vulnerable to username enumeration. It uses account locking but it contains a logic flaw so to solve this lab, enumerate a valid username and bruteforce the user's password then access their account.

(1). My first step is to determine the behavior of the application. I took a username from the list with a password and intentionally entered it in so it would be incorrect.

For this, I then went with Cluster Bomb and set the payload 1 equal to my user list and payload 2 equal to a null string (generate 5 payloads) after setting the username position to all of the candidate usernames provided by PortSwigger and the password list.

You can also do as the second payload password="pw"&count:
Numbers From 1-5

what it basically does is it checks username 3-4 attempts and if it is a valid username it will get locked.

(2) Evaluate the responses:
From the responses one can deduce that the correct username is arcsight because the response length is longer- and if you analyze the response- you will see that the account was locked out after too many incorrect login attempts.

(3)  I then went to Sniper and set the password as the position and ran the list of passwords provided by PortSwigger.

The only one I found to be of different length than the others is shadow.

So I then attempted to login as arcsight:shadow and I was successful.
