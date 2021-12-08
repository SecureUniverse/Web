# Broken Access Control

## IDOR - Insecure Direct Object Reference
- ```?customer_number=132354```

## Missing Functional Level Access Control
- http://example.com/app/getappinfo => http://example.com/app/admin_getappinfo
- GHDB
  - site:ir inurl:editform.aspx
  - site:ir inurl:editprofile.php
- Login => Visit & save all pages => Logout => Check access to all pages


## File Access Attach
- [File Inclusion](Attacks/file-inclusion.md)
