# Information Gathering

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
   - [CRT.sh](https://crt.sh/)

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
   - Burp
     - Intruder
       - ```GET /$$ HTTP/1.0``` 
       - Wordlist: /usr/share/wordlists/dirb/common.txt
     - Crawling
       - a 
   - Dirbuster
     - Enter the target URL and select “Auto Switch” in Work Method
     - Click on the “Browse” button to select the wordlist => /usr/share/wordlists/dirb/common.txt
     - Click on the Start button
     - Click on the "Results - List Views" button in order to see the results
     - Click on the "Results - Tree View" to get the results in tree format
     - Increase the threads up to 30 to get results faster. Enter 30 in the "Current number of threads" & Click on the Change button
     - Click on the dropdown button to get the contents inside the data directory
   - Gobuster
     - ```gobuster dir -u http://192.156.207.3 -w /usr/share/wordlists/dirb/common.txt```
     - ```gobuster dir -u http://192.156.207.3 -w /usr/share/wordlists/dirb/common.txt -b 403,404```
       - ```-b```: specify the status codes which has to be ignored
     - ```gobuster dir -u http://192.156.207.3 -w /usr/share/wordlists/dirb/common.txt -b 403,404 -x .php,.xml,.txt -r```
       - ```-x```: find the files which have the specified extensions
       - ```-r```: follow any redirects or 302 status code pages 
     - ```gobuster dir -u http://192.156.207.3/data -w /usr/share/wordlists/dirb/common.txt -b 403,404 -x .php,.xml,.txt -r``` 
       - start scanning from the ```/data``` directory
   - Opendoor
     - 
   - ZAProxy
     - 
   - d   
   - [dirb](/Tools/dirb.md)
   - Crawling with [Burp](/Tools/burp.md)
   - [PentestTools](https://pentest-tools.com/) 
   - Sensitive files: ```phpinfo.php``` & ```robots.txt```

## Search engine
- [Google](https://www.google.com/)
  - site:gm.com -s -"search-careers" -www ext:jsp
  - site:gm.com -s -"search-careers" -www inurl:admin
  - site:gm.com -s -"search-careers" -www inurl:login 
  - site:gm.com -s -"search-careers" -www intitle:admin

- [Shodan](https://www.shodan.io/)
  - ```hostname:gm.com```
  - ```net:"193.8.138.0/24" port:443```
  - ```net:"193.8.138.0/24" apache```
  - ```net:"193.8.138.0/24" iis```
  - ELK Misconfiguration: ```country:ir port:5601```
  - MongoDB Misconfiguration: ```country:ir port:27017```

- [Censys](https://censys.io/)
  - ```location.country.code:US and tags:scada```

## Maltego
- Add entity
  - Palette -> Infrastructure -> Domain
- Discover
  - Right-click on the entity and select a transform

