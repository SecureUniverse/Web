# CSRF

## Concepts
- اگر سرور بررسی نکند که آیا درخواست واقعا از کاربر آمده است یا نه، این حمله رخ می دهد
- از این آسیب پذیری برای تغییر رمز عبور ، ایمیل و ... قربانی استفاده می شود
- باید به دنبال CSRF Token درون Req و Resp  بگردیم و آن را حذف کنیم تا ببینیم کار می کند یا نه
- همچنین می توانیم CSRF Token یک کاربر دیگر را استاده مجدد کنیم تا نتیجه را بررسی کنیم

## Discovery
- Save *"change password"* request with Burp, in an HTML file, then open the HTML file in a new browser. Check if the password changed or not.

## Mitigation
- Generate an unpredictable token that can not be used (large value, random, unique)
- Embed the token in the HTML page in a hidden form
- Verify the token when the form is submitted 
- If there is no CSRF token, use *"Current Password"* fro change password
