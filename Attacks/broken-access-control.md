# Broken Access Control

## Exploit
- باید robots.txt را برای وجود مسیرهایی که ممکن است روی آن ها authentication وجود نداشته باشد، بررسی کنیم (مانند پنل ادمین)
- درون source code صفحه به دنبال javascript هایی می گردیم که ممکن است درون آن، مسیرهایی باشد که روی آن ها authentication ای وجود نداشته باشد 
- درون کوکی هایی که از سمت سرور تنظیم می شود، به دنبال مقادیری مانند admin=false می گردیم و آن را به true تغییر می دهیم تا به صفحاتی مانند adminpanel دسترسی یابیم

## GHDB
  - site:ir inurl:editform.aspx
  - site:ir inurl:editprofile.php

# Payload
- Login => Visit & save all pages => Logout => Check access to all pages
- http://example.com/app/getappinfo => http://example.com/app/admin_getappinfo
