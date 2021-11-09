# Infrmation Gathering

## Steps
1. IP address
   - ```ping``` command

2. Domain name info
   - [whois](https://whois.domaintools.com/)

3. Technologies used
   - [Netcraft](https://sitereport.netcraft.com/?url=)

4. DNS records
   - [Robtex](https://www.robtex.com/)
   - nslookup
   - dig
     - ```dig +short ns megacorpone.com```
     - ```dig +short mx megacorpone.com```
     - ```dig +short a megacorpone.com```
   - Reverse IP lookup zone
     - ```for ip in $(seq 1 254); do host 193.8.139.$ip; done | grep -v "not found"``` 

5. Other websites on the same server
   - [Robtex](https://www.robtex.com/)
   - Use ```ip:[target ip]``` in *"bing.com"*

6. Subdomains
   - [knock](https://github.com/guelfoweb/knock)
   - [Google](https://www.google.com/)
     - ```site:nasa.gov -site:www.nasa.gov```
   - [Netcraft](https://searchdns.netcraft.com/)
     - site ends with *".mci.ir"* 
   - Dictionary attack 
     -  ```for ip in $(cat subdomain.txt); do host $ip.megacorpone.com; done | grep -v "not found"```

7. Unlisted files, directories
   - [dirb](/Tools/dirb.md)
   - Sensitive files
     - phpinfo.php
     - robots.txt 

## Search engine
- [Google](https://www.google.com/)
  - s

- [Shodan](https://www.shodan.io/)
  - ```net: “193.8.138.0/24” port:443```
  - ```net: “193.8.138.0/24” apache```
  - ```net: “193.8.138.0/24” iis```

- [Censys](https://censys.io/)
  - ```location.country.code:US and tags:scada```

## Framework
[Maltego](/Tools/maltego.md)

