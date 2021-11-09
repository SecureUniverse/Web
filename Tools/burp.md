# Burp

## Crawling
- Send a request to Intruder
- Change *"position"*
  -  ```GET /$$ HTTP/1.1```
- Payload type: Bruteforcer
- Set *"min"* & *"max"*
- Add ```.txt``` for "*Suffix*"
- Filter with ```200``` Status code

## Sequencer
- Use to detect the ability to predict randomize (for example, Cookie)
1. Send a *"request"* (with cookie) to repeater
2. Clear the cookie and click on *"Go"*
3. Send the *"response"* to sequencer
4. Cookie is added to: *"Sequencer > Live capture > Token Location > Within Response"*
5. Click on *"Sequencer > Live capture > Select live Capture Request > Start live capture"*
6. After 200 requests, click on *"Analyze now"* to receive *"entropy"* report
7. Also we can save tokens in a file
 

## Intercept Mobile Traffic

#### Mobile
- Use Android 6.0.1 Build Number MMB29K from [here](https://developers.google.com/android/images#bullhead)
- Connect mobile wifi to same network as PC
- Add proxy: Wifi Setting -> Modify network config -> Show advanced options -> Manual
  -  Proxy hostname: 10.60.10.123
  -  Proxy port: 8082
- Add burp certificate to mobile
  - Enter burp address in browser of mobile
  - Change the extension from 'der' to 'cer' (just for android < 7) 
  - Setting -> Security -> Install from device storage
    - Certificate name: cacert
    - Credential use: VPN and apps
  - Check
    - User -> Trusted credentials -> PortSwigger 
  - Install a nossl version of android app to intercept traffic 

#### PC
- Burp -> Proxy -> Options -> Proxy Listeners -> Add
  - Bind to port: 8082
  - Bind to address: All interface
