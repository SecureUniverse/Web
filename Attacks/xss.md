# XSS

## Types
- Reflected
- Stored
- DOM Based
  - هیچ اطلاعاتی به سمت سرور ارسال نمی شود که این در Burp قابل بررسی است
  
  - Javascript functions types
    - source
      - ```?name=alireza => document.url()```
    - sink 
      -  ```getElementById()```
      - ```document.write()```


## Exploitation
- Session Hijacking
- Fake Page
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
