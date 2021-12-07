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
- ممکن است در بخش Edit Profile بتوانیم مکانیزم های امنیتی ای که در بخش Create Profile وجود دارد را دور بزنیم

## Defenses Against Application Mis-Use
- بلاک کردن کاربری که از کاراکترهای غیرمجاز استفاده کرده است، برای یک زمان مشخص
- معادل OWASP A10 با نام Insufficient Logging and Monitoring می باشد

## Upload of Unexpected File Types
- فایل های با پسوندهای غیرمجاز نباید آپلود شوند، مانند Shell ای که به صورت mypic.php.gif آپلود کردیم

## Upload of Malicious Files
- Upload an image with PHP code in comment part
- File signature should be checked
