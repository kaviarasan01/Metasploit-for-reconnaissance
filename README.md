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

Find out the ip address of the attackers system
## OUTPUT:



Invoke msfconsole:
## OUTPUT:

<img width="888" height="661" alt="Screenshot 2026-08-20 135621" src="https://github.com/user-attachments/assets/e2e5924b-1388-4ee2-844f-55a1a5c27d83" />



Type help or a question mark "?" to see the list of all available commands you can use inside msfconsole.

<img width="870" height="765" alt="exp 5 2" src="https://github.com/user-attachments/assets/dc770d3a-d0f0-4318-b042-ddf70b1d92bc" />



Port Scanning:
Following command is executed for scanning the systems on our local area network with a TCP scan (-sT) looking for open ports between 1 and 1000 (-p1-1000).
msf >  nmap -sT 192.168.1810/24 -p1-1000  (Replace with appropriate IP Address)
## OUTPUT:
<img width="850" height="632" alt="exp 5 3" src="https://github.com/user-attachments/assets/834be0f2-8482-4f0b-b923-2ab763137a36" />

step4:
use the db-nmap command to scan and save the results into Metasploit's postgresql attached database. In that way, you can use those results in the exploitation stage later.

scan the targets with the command db_nmap as follows.
msf > db_nmap 192.168.181.0/24
## OUTPUT:

<img width="706" height="542" alt="exp 5 4" src="https://github.com/user-attachments/assets/55280d6d-973b-44ec-80a4-780d88e9fe46" />


Metasploit has a multitude of scanning modules built in. If we open another terminal, we can navigate to Metasploit's auxiliary modules and list all the scanner modules.
cd /usr/share /metasploit-framework/modules/auxiliary
kali > ls -l
## OUTPUT:

<img width="706" height="552" alt="exp 5 5" src="https://github.com/user-attachments/assets/ac146972-4017-44c1-af46-9cca3a640ef6" />


Search is a powerful command in Metasploit that you can use to find what you want to locate. 
msf >search name:Microsoft type:exploit
## OUTPUT:

<img width="887" height="790" alt="exp 5 6" src="https://github.com/user-attachments/assets/c9586acd-0e6e-4016-a985-509736d6c926" />


The info command provides information regarding a module or platform,

Before beginning, set up the Metasploit database by starting the PostgreSQL server and initialize msfconsole database as follows:
systemctl start postgresql
msfdb init
## OUTPUT:
<img width="873" height="552" alt="exp 5 7" src="https://github.com/user-attachments/assets/6d881a63-5828-4624-b5cd-062e418c274f" />




## MYSQL ENUMERATION
Find the IP address of the Metasploitable machine first. Then, use the db_nmap command in msfconsole with Nmap flags to scan the MySQL database at 3306 port.
db_nmap -sV -sC -p 3306 <metasploitable_ip_address>

## OUTPUT:
<img width="838" height="127" alt="exp 5 8" src="https://github.com/user-attachments/assets/eae36f22-8962-4208-ba4f-dce39ba8b050" />

Use the search option to look for an auxiliary module to scan and enumerate the MySQL database.
search type:auxiliary mysql
## OUTPUT:
<img width="870" height="798" alt="exp 5 9" src="https://github.com/user-attachments/assets/970c204a-ede6-4fd7-b4e5-bfd60bef4ccf" />


use the auxiliary/scanner/mysql/mysql_version module by typing the module name or associated number to scan MySQL version details.
use 11
Or:
use auxiliary/scanner/mysql/mysql_version
## OUTPUT:
<img width="852" height="452" alt="image" src="https://github.com/user-attachments/assets/9e65818d-a75b-4131-af29-5aebe3fd816a" />





Use the set rhosts command to set the parameter and run the module, as follows:
## OUTPUT:

<img width="832" height="190" alt="Screenshot 2026-08-20 134922" src="https://github.com/user-attachments/assets/a37f3416-7c95-48eb-9c60-386a072ee7f6" />





After scanning, you can also brute force MySQL root account via Metasploit's auxiliary(scanner/mysql/mysql_login) module.
## OUTPUT:


<img width="874" height="781" alt="Screenshot 2026-08-20 135313" src="https://github.com/user-attachments/assets/9b0edd46-14bf-4972-8b4c-5b3cd9ca1802" />




set the PASS_FILE parameter to the wordlist path available inside /usr/share/wordlists:
set PASS_FILE /usr/share/wordlistss/rockyou.txt
Then, specify the IP address of the target machine with the RHOSTS command.
set RHOSTS <metasploitable-ip-address>
Set BLANK_PASSWORDS to true in case there is no password set for the root account.
set BLANK_PASSWORDS true
## OUTPUT:

<img width="836" height="315" alt="exp 5 11" src="https://github.com/user-attachments/assets/8f8f78c9-c00f-4ade-b0d5-82702bcc918a" />




## RESULT:
The Metasploit framework for reconnaissance is  examined successfully
