# CSRF

## Concepts
- اگر سرور بررسی نکند که آیا درخواست واقعا از کاربر آمده است یا نه، این حمله رخ می دهد
- از این آسیب پذیری برای تغییر رمز عبور ، ایمیل و ... قربانی استفاده می شود
- باید به دنبال CSRF Token درون Req و Resp  بگردیم و آن را حذف کنیم تا ببینیم کار می کند یا نه
- همچنین می توانیم CSRF Token یک کاربر دیگر را استاده مجدد کنیم تا نتیجه را بررسی کنیم

## Exploit
- در خواست تغییر ایمیل را به Burp می بریم، اگر CSRF Token نداشت، از طریق Burp یک PoC می سازیم
- اگر CSRF Token داشت از روش های زیر استفاده می کنیم :
  - متد را از POST به GET تغییر می دهیم
  - نام پارامتر و مقدار CSRF Token را از درخواست حذف می کنیم
  - اگر CSRF Token به هیچ مقداری درون کوکی tied نشده باشد
    - با کاربر A لاگین کرده و CSRF Token درخواست تغییر ایمیل را برمی داریم
    - در خواست تغییر ایمیل کاربر B را متوقف کرده و CSRF Token کاربر A را به جای CSRF Token آن قرار می دهیم و PoC را ایجاد می کنیم
    - نکته: از آنجائیکه CSRF Token یک بار مصرف است، باید درخواست تغییر ایمیل کاربر A را drop کرده باشیم
  - اگر CSRF Token به مقداری از Cookie، به جز SessionId وصل شده باشد (مثلا csrfkey)
    - بررسی می کنیم که در کجای سایت می شود این cookie را در مرورگر قربانی تزریق کرد (مثلا در بخش search ممکن است این cookie به همراه مقداری که جستجو کردیم، به cookie اضافه گردد) که نتیجه این کار یک URL می شود
```
/?search=test%0d%0aSet-Cookie:%20csrfKey=TwzBeSszkg9tjKT3u97crNV7yWLVl0iU
```
    - سشسی
  - س

## Burp
- Right-click on the Request > Engagement tools > Generate SCRF PoC
- Options > Choose "incluse auto-submit script"
- Click on Regenerate
- Click on Copy HTML
- Upload the HTML file in an exploit server and deliver it to victim

## Discovery
- Save *"change password"* request with Burp, in an HTML file, then open the HTML file in a new browser. Check if the password changed or not.

## Mitigation
- Generate an unpredictable token that can not be used (large value, random, unique)
- Embed the token in the HTML page in a hidden form
- Verify the token when the form is submitted 
- If there is no CSRF token, use *"Current Password"* fro change password
