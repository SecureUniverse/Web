# SQL Injection

## Exploit
- Login
  - username: ```admin'#``` 
  - password: ```1' or 1=1#``` 

## Mitigation
- Secure Code for login in PHP
```PHP
$query = "SELECT * FROM accounts WHERE username='".
$conn->real_escape_string($username).
"'AND password='".
$conn->real_escape_string($password).
"'"
```
