# Business Logic


## Business Logic Data Validation
- 

## Ability to forge Request


## Integrity Check


## Process Timing
- حذف محصول از سبد خرید پس از زمان مشخص
- صدور خطا دیتابیس پس از ماندن طولانی مدت در یکی از مراحل فرآیند خرید

## Number of times a Function can be Used limits
- محدود نمودن فراخوانی تابع موجودی بیش از 5 بار برای جلوگیری از Dictionary Attack و Brute Force

## The circumvention of Workflows
- ممکن است در بخش Edit Profile بتوانیم مکانزم های امنیتی ای که در بخش Create Profile وجود دارد را دور بزنیم

## Defenses Against Application Mis-Use
- Block user for specific time after using illegal characters
- OWASP A10 => Insufficient Logging and Monitoring

## Upload of Unexpected File Types
- upload mypic.php.gif

## Upload of Malicious Files
- Upload an image with PHP code in comment part
- File signature shoudl be checked
