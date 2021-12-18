# Apache

## Modify the Apache banner to hide version and OS information

## Modify the Server field in the response header to Microsoft IIS

## Disable Server Signature

## Disable Etags
 
## Disable the built-in icons alias

## Disable the directory listing for /resources directory

## Disable access to .git or .svn directories

## Disable non-essential HTTP methods and requests

## Disable the TRACE request support on the webserver

## Enable the built-in protections against XSS and Clickjacking

## Disable the support for HTTP 1.0 protocol

## Enable Basic authentication on /protect-basic directory. Use credentials admin:welcome

## Enable Digest authentication on protect-digest directory. Use credentials admin:thanks

## Disable access from IP range <range3 provided_in_lab> but allow access from <range2 provided_in_lab> and <range1 provided_in_lab>

## Enable TLS for all interactions with the portal
  
## Disable TLSv1.2 and enable TLSv1.3 on the portal
  
## Enable POST parameter logging and log those in /var/log/apache2/modsec_audit.log
  
## Disable the cache module
- Check the currently loaded modules : ```apache2ctl -M```
- Filter for cache-related modules : ```apache2ctl -M | grep cache```
- Disable cache modules : ```a2dismod cache_disk``` & ```a2dismod cache```
- Restart Apache : ``` /etc/init.d/apache2 restart```
- Verify if the modules are disabled : ``` apache2ctl -M | grep cache```
  
