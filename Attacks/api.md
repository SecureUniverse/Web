# API

## Web service attack types
- SQL Injection
- Command Injection
- Code Execution
- XXE
- Broken Access Control
- XML Bombing

## Recon
  - ```site:ir inurl:?wsdl```

## SoapUI
- Rest API
  - Define URI
  - Select Method
  - Paste JSON in left-bottom part

- Load Test
  - Right-click on Request & select "Add to TestCase"
  - Right-click on TestCase & select "New LoadTest"

- penetration steps
  - File > New Soap Project
    - Project Name : shaparak
    - Initial WSDL : https://sep.shaparak.ir/payments/referencepayment.asmx?WSDL
  - Open functions and check Requests
    - Replace ? with parameters
  - Check Response in right window

## Buggy Framework
- WebGoat
