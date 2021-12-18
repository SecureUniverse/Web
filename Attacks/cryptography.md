# Cryptography

## Character Sets
- ASCII: 7 bits (128 characters)
- UTF8: 8 bits (256 characters)
- UTF16/32: 16 bits 

## Symbols
- ```or```     =>    ||
- ```and```    =>    &&
- ```space```  =>    +

## Encoding
- URL Encode : ```%```
  - ```&&```    =>    %26%26
  - ```||```    =>    %7c%7c
  - ```space``` =>    %20
  - ```‘```     =>    %27
  - ```>```     =>    %3E
  - ```<```     =>    %3C
  - ```;```     =>    %3B
- Base64 : ```==``` ```\``` ```.```
- Gzip : geometrical shape
- Hex : ```0~9 a~F```



## Attacks (SSLv3 - TLS1.1)
- Heartbleed 
  - Metasploit: openssh_hearbleed
    - Auxiliary: ```use auxiliary/scanner/ssl/openssh_hearbleed```
    - Exploit: ```set verbose true```
- Poodle
  - Oracle Padding

## SSLyze
- Usage
  - ```sudo sslyze --regular ib.bki.ir```
  - Find ```vulnerable``` in output
