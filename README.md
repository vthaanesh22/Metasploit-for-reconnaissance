# Metasploit-for-reconnaissance
# Metasploit
Metasploit for reconnaissance in pentesting

# AIM:

To get introduced to Metasploit Framework and to  perform reconnaissance  in pentesting .

## DESIGN STEPS:

### Step 1:

Install kali linux either in partition or virtual box or in live mode

### Step 2:

Investigate on the various categories of tools as follows:

### Step 3:

Open terminal and try execute some kali linux commands

## EXECUTION STEPS AND ITS OUTPUT:
## PROGRAM:

Find out the ip address of the attackers system

## OUTPUT:
![image](https://github.com/AmirthaRoopaS/Metasploit-for-reconnaissance/assets/143496311/e78836ff-3a02-4474-9d98-ff90b8c2f719)

## Invoke msfconsole:


## OUTPUT:

![image](https://github.com/AmirthaRoopaS/Metasploit-for-reconnaissance/assets/143496311/e466e06d-81ea-4478-ac63-68b697e13909)

Type help or a question mark "?" to see the list of all available commands you can use inside msfconsole.

## OUTPUT:
![image](https://github.com/AmirthaRoopaS/Metasploit-for-reconnaissance/assets/143496311/1fd66a50-f9d1-4ad8-b53a-a516e495cb0a)

## Port Scanning:
Following command is executed for scanning the systems on our local area network with a TCP scan (-sT) looking for open ports between 1 and 1000 (-p1-1000).
msf >  nmap -sT 192.168.1810/24 -p1-1000

## OUTPUT:
![image](https://github.com/AmirthaRoopaS/Metasploit-for-reconnaissance/assets/143496311/df7d774d-f7b1-471b-8d6b-eabf9b472517)

## step4:
use the db-nmap command to scan and save the results into Metasploit's postgresql attached database. In that way, you can use those results in the exploitation stage later.

scan the targets with the command db_nmap as follows.
msf > db_nmap 192.168.181.0/24

## OUTPUT:
![image](https://github.com/AmirthaRoopaS/Metasploit-for-reconnaissance/assets/143496311/64fb43ae-877d-4f4c-baf9-2cc5ff2456c3)

Metasploit has a multitude of scanning modules built in. If we open another terminal, we can navigate to Metasploit's auxiliary modules and list all the scanner modules.
cd /usr/share /metasploit-framework/modules/auxiliary
kali > ls -l

## OUTPUT:
![image](https://github.com/AmirthaRoopaS/Metasploit-for-reconnaissance/assets/143496311/065dd682-6b33-4cf4-b5a8-c1091569234a)

Search is a powerful command in Metasploit that you can use to find what you want to locate. 
msf >search name:Microsoft type:exploit

## OUTPUT:
![image](https://github.com/AmirthaRoopaS/Metasploit-for-reconnaissance/assets/143496311/e1739073-b837-494f-bebd-bd44ddf8b01a)

The info command provides information regarding a module or platform,

## OUTPUT:
![image](https://github.com/AmirthaRoopaS/Metasploit-for-reconnaissance/assets/143496311/3ac8e1fb-0fb5-4454-ae6c-8970bd9a0a53)

Before beginning, set up the Metasploit database by starting the PostgreSQL server and initialize msfconsole database as follows:
systemctl start postgresql
msfdb init
## MYSQL ENUMERATION
Find the IP address of the Metasploitable machine first. Then, use the db_nmap command in msfconsole with Nmap flags to scan the MySQL database at 3306 port.
db_nmap -sV -sC -p 3306 <metasploitable_ip_address>

## OUTPUT:
![image](https://github.com/AmirthaRoopaS/Metasploit-for-reconnaissance/assets/143496311/bd8b69cc-127b-4cdb-a901-0ec46bc2a537)

Use the search option to look for an auxiliary module to scan and enumerate the MySQL database.
search type:auxiliary mysql

## OUTPUT:
![image](https://github.com/AmirthaRoopaS/Metasploit-for-reconnaissance/assets/143496311/5849cbc8-5ed7-45fe-9e6a-4b67c7ddebc0)

use the auxiliary/scanner/mysql/mysql_version module by typing the module name or associated number to scan MySQL version details.
use 11
Or:
use auxiliary/scanner/mysql/mysql_version

## OUTPUT:
![image](https://github.com/AmirthaRoopaS/Metasploit-for-reconnaissance/assets/143496311/da227f4e-8bdc-4bbc-81e9-71dd6cc00a53)

Use the set rhosts command to set the parameter and run the module, as follows:

## OUTPUT:
![image](https://github.com/AmirthaRoopaS/Metasploit-for-reconnaissance/assets/143496311/28993d34-f443-474b-96b6-7f9af29d830b)


After scanning, you can also brute force MySQL root account via Metasploit's auxiliary(scanner/mysql/mysql_login) module.

## OUTPUT:
![image](https://github.com/AmirthaRoopaS/Metasploit-for-reconnaissance/assets/143496311/a2926f7f-bfd0-4af6-aae3-22e6e7be9866)

set the PASS_FILE parameter to the wordlist path available inside /usr/share/wordlists:
set PASS_FILE /usr/share/wordlistss/rockyou.txt
Then, specify the IP address of the target machine with the RHOSTS command.
set RHOSTS <metasploitable-ip-address>
Set BLANK_PASSWORDS to true in case there is no password set for the root account.
set BLANK_PASSWORDS true

## OUTPUT:
![image](https://github.com/AmirthaRoopaS/Metasploit-for-reconnaissance/assets/143496311/27925562-58ac-4784-8793-53ee611d02d7)

## RESULT:
The Metasploit framework for reconnaissance is  examined successfully
