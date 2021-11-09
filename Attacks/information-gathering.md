# Infrmation Gathering

## Steps
1. **IP address**
   - ```ping``` command

2. **Domain name info**
   - [whois](https://whois.domaintools.com/)

3. **Technologies used**
   - Web server
     - [Netcraft](https://sitereport.netcraft.com/?url=)
     - nc
       - ```nc www.nooranet.com 80```
       - ```GET / HTTP/1.1```
     - Check Response with Burp
     - ```nmap -p 80,443 -sV abc.ed```  
   - Web application
     - Review page source
     - Check cookies
     - Browser addon (Wappalyzer)  

4. **DNS records**
   - [Robtex](https://www.robtex.com/)
   - nslookup
   - [dig](/Tools/dig.md)
   - Reverse IP lookup zone
     - ```for ip in $(seq 1 254); do host 193.8.139.$ip; done | grep -v "not found"``` 

5. **Other websites on the same server**
   - [Robtex](https://www.robtex.com/)
   - [Bing](https://www.bing.com/): ```ip:[target ip]```
   - [YouGetSignal](https://www.yougetsignal.com/): Reverse IP Domain Check
   - [FomainTools](https://reverseip.domaintools.com/): accept IP range 

6. **Subdomains**
   - [knock](https://github.com/guelfoweb/knock)
   - [Google](https://www.google.com/): ```site:nasa.gov -site:www.nasa.gov```
   - [Netcraft](https://searchdns.netcraft.com/): site ends with *".mci.ir"* 
   - Dictionary attack: ```for ip in $(cat subdomain.txt); do host $ip.megacorpone.com; done | grep -v "not found"```

7. **Unlisted files, directories**
   - [dirb](/Tools/dirb.md)
   - Crawling with [Burp](/Tools/burp.md)
   - [PentestTools](https://pentest-tools.com/) 
   - Sensitive files: ```phpinfo.php``` & ```robots.txt```

## Search engine
- [Google](https://www.google.com/)
  - s

- [Shodan](https://www.shodan.io/)
  - ```net:"193.8.138.0/24" port:443```
  - ```net:"193.8.138.0/24" apache```
  - ```net:"193.8.138.0/24" iis```

- [Censys](https://censys.io/)
  - ```location.country.code:US and tags:scada```

## Framework
[Maltego](/Tools/maltego.md)

