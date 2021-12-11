# Broken Access Control

## Missing Functional Level Access Control
- http://example.com/app/getappinfo => http://example.com/app/admin_getappinfo
- GHDB
  - site:ir inurl:editform.aspx
  - site:ir inurl:editprofile.php
- Login => Visit & save all pages => Logout => Check access to all pages
