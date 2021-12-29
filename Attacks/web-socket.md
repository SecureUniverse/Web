# Web Socket

## Concept
- برخی ترافیک ها (مانند Chat های وبسایت ها) از جنس WebSocket می باشند، که ترافیک آن های از بخش Proxy > WebSockets history قابل مشاهده است.

## Exploit
- **دستکاری message**
  - با ارسال پیام در بخش چت وبسایت، مشاهده می شود که ترافیک URL-Encode می گردد
  - باید ترافیک را intercept کرده و payload را در Burp وارد کنیم
```HTML
<img src=1 onerror='alert(1)'>
```

- **دستکاری handshake**
  -  
