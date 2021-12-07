# XSS

## Types
- Reflected
- Stored
- DOM Based
  - Nothing send to server (check with Burp), instead use both Javascript functions types simultaneously:
    - source
      - ```?name=alireza => document.url()```
    - sink 
      -  ```getElementById()```
      - ```document.write()```

## Exploitation
- Session Hijacking (SEC542-4)
- Fake Page (SEC542-4)
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
