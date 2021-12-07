# Business Logic


## Business Logic Data Validation
- 

## Ability to forge Request


## Integrity Check


## Process Timing
- حذف محصول از سبد خرید پس از زمان مشخص
- صدور خطا دستابیس پس از ماندن طولانی مدت در یکی از مراحل فرآیند خرید

## Number of times a Function can be Used limits
- Restrict calling `موجودی` more than 5 times in banking app to prevent Brute Force & Dictionary Attack

## The circumvention of Workflows
- Check `Edit Profile` to bypass security role of `Create Profile`

## Defenses Against Application Mis-Use
- Block user for specific time after using illegal characters
- OWASP A10 => Insufficient Logging and Monitoring

## Upload of Unexpected File Types
- upload mypic.php.gif

## Upload of Malicious Files
- Upload an image with PHP code in comment part
- File signature shoudl be checked
