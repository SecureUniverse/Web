# Brute Force

## Burp
- Intruder

## ZAProxy
- Click on "Manual Explore", enter the target IP address in the Input field and click on "Launch Browser" => A browser session will be started with ZAP HUD
- Click on "Continue to your target"
- Attempt login with invalid credentials => The website and the login page action will be added to the sitemap
- Click on the POST request from the sitemap and click on the "Request" tab
- Right click on the POST request, navigate to Attack and click on "Fuzz" => The Fuzzer window will appear
- Select the entered username "john" and click on the Add button => The payloads window will appear
- Click on the Add button, enter the payloads for username. Click on the Add button => Payloads: admin,bee 
- Click on the "OK" button => The payload will appear in the Fuzz Locations
- Similarly, select the entered password "doe" and click on the Add button => The payloads window will appear
- Click on the Add button, enter the payloads for password. Click on the Add button => Payloads: admin, password, adminpasswd, cookie, hello, world, bug, bee
- Click on the OK button => The payload will appear in the Fuzz Locations
- Click on Start Fuzzer. Upon completion of the attack, compare the status code => One of the status code will be 302


## Hydra (Brute force)
- ```hydra -L usernames -P passwords 192.208.137.3 http-post-form "/login.php:login=^USER^&password=^PASS^&security_level=0&form=submit:Invalid credentials or user not activated!"```
  - ```-L```: usernames file
  - ```-P```: password file 
  - ```^USER^``` placeholder will take in the username from the list
  - ```^PASS^``` placeholder will take in the password from the list

## Crunch (Wordlist generator)
- Syntax
  - ```crunch [min]  [max] [characters] -t [pattern] -o [filename]```
- Example
  - ```crunch 6 8 123abc$ -i wordlist -t a@@@@b```
  - ```crunch 6 8 abc12 -o test.txt```

## Wordlists
- ftp://ftp.openwall.com/pub/wordlists/
- https://github.com/berzerk0/Probable-Wordlists
- http://www.openwall.com/mirrors/
- http://www.outpost9.com/files/WordLists.html
- http://www.vulnerabilityassessment.co.uk/passwords.htm
- http://packetstormsecurity.org/Crackers/wordlists/
- http://www.ai.uga.edu/ftplib/natural-language/moby/
- http://wordlist.sourceforge.net/
