# Brute Force

## Exploit
- بررسی می کنیم که پیغام خطای نام کاربری اشتباه و پسورد اشتباه، یکسان می باشد یا خیر
- برای یافتن user/pass درست از موارد زیر استفاده می کنیم
  - کد پاسخ redirect مانند 302
  - طول متفاوت در response
  - بخش Grep-Match که به دنبال یک string درون پاسخ می گردد
  - بخش Grep-Extract که response را fetch کرده و همان جا می توانیم بخشی که می خواهیم را هایلایت کنیم
    - ممکن است این تفاوت جزئی باشد، مثلا در یک نقطه انتهای عبارت invalid username and password. برای بررسی این حالت از بخش Grep-Extract استفاده می  کنیم و با زدن Add، بخش خطای صادر شده را هایلات کرده و درون Warning ها به دنبال تفاوت می گردیم



## Burp
- Send request to Intruder
- Decode user/pass in the request
  - Right-click on the value and select "Convert selection > Base64 > Base64-decode"
  - The credentials passed to the login prompt are shown => test:123
- Replace the credentials with a parameter to be substituted => creds
- Click on the Add$ Button on the right side
- Navigate to the Payloads tab and load the 100-common-passwords.txt list
- In the Payload Processing section click on the "Add" button
- Select "Add Prefix" & Set the Prefix to "admin:"
  - Now "admin:" would be appended to each password from the list 
- Add another Payload Processing option to encode the payload to base64 
  - Select the Encode Rule as Base64-encode 
- Click on the "Start Attack" button 
- Check the Status codes of the requests and check the payload for the request with a different status code => 301
- Double click on the request entry
- Select the credentials in the Authorization header field and send them to the Decoder tab

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
