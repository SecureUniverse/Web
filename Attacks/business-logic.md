# Business Logic


## Business Logic Data Validation
- چک کردن صحت کدملی، ایمیل، کدپستی
- هدف کاهش حجم دیتابیس است تا دیتای فیک نداشته باشیم

## Ability to forge Request
- اضافه کردن فیلد discount=10% و گرفتن تخفیف زمانی که زمان تخفیف به پایان رسیده است

## Integrity Check
- فیلدهای مخفی شده نباید در سمت سرور پردازش شوند و بر اساس آن ها تصمیمی گرفته شود

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
- محتوای فایل هم علاوه بر extension باید چک شود که از طریق signature می باشد
- مانند قرار دادن کد PHP در بخش comment عکس