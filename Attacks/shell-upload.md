# Shell Upload

## Tool
- [Weevely](/Tools/weevely.md)

## Bypass
- Intercept request and modify headers
  - ```Content-Type: image/jpeg```
  - ```Content-Disposition: filename="shell.php.jpg"```

## Mitigation
- Never allow users to upload executable
- Check the file type & extension
- Analyze the uploaded file itself, recreate it and rename it (with library)


## Find Uploaded Shell
- Burp
  - Intruder > Payloads > Add Payload Processing > test
  - Suffix: ```.php```
- [Dirbuster](/Tools/dirbuster.md)
