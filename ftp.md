## Połączenie
ftp IP
# user: anonymous / pass: (puste)

## Komendy
ls                    # lista plików
cd katalog            # zmiana katalogu
get plik              # pobierz plik
mget *                # pobierz wszystko
put plik              # wyślij plik
help                  # pomoc

## Brute-force
medusa -u user -P /usr/share/wordlists/rockyou.txt -h IP -M ftp
hydra -l user -P /usr/share/wordlists/rockyou.txt ftp://IP

## Nmap
nmap -sC -sV -p 21 IP
