# Broken Access Control

## Exploit
- باید robots.txt را برای وجود مسیرهایی که ممکن است روی آن ها authentication وجود نداشته باشد، بررسی کنیم (مانند پنل ادمین)
- درون source code صفحه به دنبال javascript هایی می گردیم که ممکن است درون آن، مسیرهایی باشد که روی آن ها authentication ای وجود نداشته باشد 
- درون کوکی هایی که از سمت سرور تنظیم می شود، به دنبال مقادیری مانند admin=false می گردیم و آن را به true تغییر می دهیم تا به صفحاتی مانند adminpanel دسترسی یابیم
- اگر درون Response بخش هایی از سایت مانند تغییر ایمیل،  ```roleid=1``` مشاهده شود، می توانیم آن را ```roleid=2``` درون Request  قرار دهیم، تا نقش خود را از کاربر معمولی به ادمین تغییر دهیم
  - این اطلاعات معمولا به صورت JSON هستند، دقت شود که مقادیر JSON باید با ```,``` از یکدیگر جدا شوند 
- هدر ```X-Original-URL: /invalid``` را به درخواست اضافه می کنیم، اگر خطای Not found بدهد یعنی این مقدار در سمت سرور پردازش می گردد. با افزودن هدر ```X-Original-URL: /admin``` می توانیم به صفحات و متدهایی که نیاز به دسترسی ادمین دارند، دسترسی یابیم
```HTML
Source code
   => <a href="/admin/delete?username=carlos">Delete</a>
Request changes to delete a user
   => GET /?username=carlos HTTP/1.1
   => X-Original-URL: /admin/delete
```
- پس از لاگین، با رفتن به صفحه حساب کاربری خودمان، وجود  username درون request ارسالی و یا URL را بررسی می کنیم. در صورت وجود آن را تغییر می دهیم تا امکان horizontal privilege escalation و امکان دست یابی به حساب کاربری دیگر کاربران را بررسی کنیم
  - اگر به جای نام کاربری از GUID استفاده شده باشد، برای پیدا کردن GUID دیگر کاربران بخش های دیگر سایت را جستجو می کنیم، مثلا در وبلاگ اگر پستی توسط دیگر کاربران نوشته شده باشد، ممکن است GUID آن کاربر به جای نام او درون URL آن پست باشد.
  - اگر پس از تغییر نام کاربری redirect شدیم، باید response را به Burp ببریم تا وجود data leakage را بررسی کنیم
    - مثلا ممکن است API key کاربر قربانی نمایش داده شود
    - یا با تغییر نام کاربری در بخش تغییر پسورد، رمز عبور قربانی نمایش داده شود 

## GHDB
  - site:ir inurl:editform.aspx
  - site:ir inurl:editprofile.php

# Payload
- Login => Visit & save all pages => Logout => Check access to all pages
- http://example.com/app/getappinfo => http://example.com/app/admin_getappinfo
