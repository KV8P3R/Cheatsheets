## Podstawowe skany
nmap -sC -sV IP                    # domyślne skrypty + wersja
nmap -sC -sV -p- IP                # wszystkie porty
nmap -sC -sV -p 80,443,445 IP      # konkretne porty
nmap -sU IP                        # UDP
nmap -O IP                         # wykryj OS

## Szybkie skany
nmap -T4 -F IP                     # szybki, top 100 portów
nmap -p- --min-rate 5000 IP        # szybki pełny skan

## Skrypty
nmap --script vuln IP              # skan podatności
nmap --script ftp-anon IP          # anonymous FTP
nmap --script smb-enum-shares IP   # SMB shares
