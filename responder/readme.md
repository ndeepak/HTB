# Responder
TARGET MACHINE IP ADDRESS
10.129.85.25

TASK 1
When visiting the web service using the IP address, what is the domain that we are being redirected to?

*****.**b
unika.htb

TASK 2
Which scripting language is being used on the server to generate webpages?
php

TASK 3
What is the name of the URL parameter which is used to load different language versions of the webpage?
page

TASK 4
Which of the following values for the `page` parameter would be an example of exploiting a Local File Include (LFI) vulnerability: "french.html", "//10.10.14.6/somefile", "../../../../../../../../windows/system32/drivers/etc/hosts", "minikatz.exe"

--> ../../../../../../../../windows/system32/drivers/etc/hosts

TASK 5
Which of the following values for the `page` parameter would be an example of exploiting a Remote File Include (RFI) vulnerability: "french.html", "//10.10.14.6/somefile", "../../../../../../../../windows/system32/drivers/etc/hosts", "minikatz.exe"
--> //10.10.14.6/somefile

TASK 6
What does NTLM stand for?
 New Technology LAN Manager

TASK 7
Which flag do we use in the Responder utility to specify the network interface?
-I

TASK 8
There are several tools that take a NetNTLMv2 challenge/response and try millions of passwords to see if any of them generate the same response. One such tool is often referred to as `john`, but the full name is what?.
john the ripper

TASK 9
What is the password for the administrator user?
┌──(root㉿kali)-[~]
└─# john --wordlist=/usr/share/wordlists/rockyou.txt hash 
Using default input encoding: UTF-8
Loaded 1 password hash (netntlmv2, NTLMv2 C/R [MD4 HMAC-MD5 32/64])
Will run 4 OpenMP threads
Press 'q' or Ctrl-C to abort, almost any other key for status
badminton        (Administrator)     
1g 0:00:00:00 DONE (2023-01-18 03:56) 100.0g/s 409600p/s 409600c/s 409600C/s slimshady..oooooo
Use the "--show --format=netntlmv2" options to display all of the cracked passwords reliably
Session completed. 
             

TASK 10
We'll use a Windows service (i.e. running on the box) to remotely access the Responder machine using the password we recovered. What port TCP does it listen on?
5985

SUBMIT FLAG

Submit root flag