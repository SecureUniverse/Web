# Broken Access Control

## Concept
- باید robots.txt را برای وجود مسیرهایی که ممکن است روی آن ها Authentication وجود نداشته باشد، بررسی کنیم
- 

## GHDB
  - site:ir inurl:editform.aspx
  - site:ir inurl:editprofile.php

# Payload
- Login => Visit & save all pages => Logout => Check access to all pages
- http://example.com/app/getappinfo => http://example.com/app/admin_getappinfo
