## EX.NO : 05
## DATE : 21.9.2023
# <p align="center"> Metasploit-for-reconnaissance</p>



## AIM:
To get introduced to Metasploit Framework and to perform reconnaissance in pentesting .

## DESIGN STEPS:
1.Install kali linux either in partition or virtual box or in live mode

2.Investigate on the various categories of tools as follows

3.Open terminal and try execute some kali linux commands
## EXECUTION STEPS AND ITS OUTPUT:
Find out the ip address of the attackers system
![272230672-20bda294-8613-41d0-b892-72b3f686ab92](https://github.com/durga46/Metasploit-for-reconnaissance/assets/75235704/d5b7c194-04a5-4020-b7b9-668845c48e49)



Invoke msfconsole:
![272230712-53946bb3-25e2-4886-b545-26b514f5ff55](https://github.com/durga46/Metasploit-for-reconnaissance/assets/75235704/a42425d6-4d0b-4008-825b-cfdf940a7ef2)



Type help or a question mark "?" to see the list of all available commands you can use inside msfconsole.
![272230751-47c9c3b4-71be-44e7-bfe3-8da20d0853c5](https://github.com/durga46/Metasploit-for-reconnaissance/assets/75235704/a52dbd84-54b0-46e8-bf63-0c6631efe236)



## Port Scanning:

Following command is executed for scanning the systems on our local area network with a TCP scan (-sT) looking for open ports between 1 and 1000 (-p1-1000). msf > nmap -sT 192.168.1810/24 -p1-1000

## OUTPUT:
![272230791-2df3e285-33ed-4502-8a95-682b35b951f2](https://github.com/durga46/Metasploit-for-reconnaissance/assets/75235704/93247277-a833-4694-9657-fd05a7111a17)


USE the db-nmap command to scan and save the results into Metasploit's postgresql attached database. In that way, you can use those results in the exploitation stage later.

scan the targets with the command db_nmap as follows. msf > db_nmap 192.168.181.0/24

## OUTPUT:

![272230835-1a8a103e-cab4-40e4-aaf7-0f5f3a3769e8](https://github.com/durga46/Metasploit-for-reconnaissance/assets/75235704/cbd28361-4816-4b7d-a4ae-f49e7499a502)

Metasploit has a multitude of scanning modules built in. If we open another terminal, we can navigate to Metasploit's auxiliary modules and list all the scanner modules. cd /usr/share /metasploit-framework/modules/auxiliary kali > ls -l

## OUTPUT:

![272230890-7c9cd001-0036-468f-902e-5a17885992eb](https://github.com/durga46/Metasploit-for-reconnaissance/assets/75235704/1c2b9001-51f3-44f7-b1fa-df26dac8fe39)

Search is a powerful command in Metasploit that you can use to find what you want to locate. msf >search name:Microsoft type:exploit

The info command provides information regarding a module or platform,

## OUTPUT

![272230939-421046b4-4b96-45cb-801a-91ea0e7f992d](https://github.com/durga46/Metasploit-for-reconnaissance/assets/75235704/0d9cbaa2-7d8f-49d1-b58d-09b47598a5d8)

Before beginning, set up the Metasploit database by starting the PostgreSQL server and initialize msfconsole database as follows: systemctl start postgresql msfdb init

## MYSQL ENUMERATION
Find the IP address of the Metasploitable machine first. Then, use the db_nmap command in msfconsole with Nmap flags to scan the MySQL database at 3306 port. db_nmap -sV -sC -p 3306 <metasploitable_ip_address>
![272230995-c10cdeca-4b89-41d8-84b3-e247c6e35fe6](https://github.com/durga46/Metasploit-for-reconnaissance/assets/75235704/bf891cd9-126a-468f-9539-aaa00335418a)



Use the search option to look for an auxiliary module to scan and enumerate the MySQL database. search type:auxiliary mysql


![272231020-4a7f9869-48cf-467f-afd3-4d6239bbc199](https://github.com/durga46/Metasploit-for-reconnaissance/assets/75235704/ba32d8c8-951c-4208-9283-648d159d1b32)

use the auxiliary/scanner/mysql/mysql_version module by typing the module name or associated number to scan MySQL version details. use 11 Or: use auxiliary/scanner/mysql/mysql_version

![272231090-358798e5-fe3f-40a5-be2b-dde671890c6e](https://github.com/durga46/Metasploit-for-reconnaissance/assets/75235704/fae99e7a-c5c1-4614-9c01-eddf0d26eb8d)


Use the set rhosts command to set the parameter and run the module, as follows:


![272231061-0255fdae-ea6d-43bd-8e73-6a4b970bb9f2](https://github.com/durga46/Metasploit-for-reconnaissance/assets/75235704/2fdbc4aa-1573-4877-9a7b-e77de24f050b)

After scanning, you can also brute force MySQL root account via Metasploit's auxiliary(scanner/mysql/mysql_login) module.


![272231138-cd66b841-bd11-4b24-910f-9d0bd137eef9](https://github.com/durga46/Metasploit-for-reconnaissance/assets/75235704/14af2dca-0494-430c-8002-32b364cc9f7a)

set the PASS_FILE parameter to the wordlist path available inside /usr/share/wordlists: set PASS_FILE /usr/share/wordlistss/rockyou.txt Then, specify the IP address of the target machine with the RHOSTS command. set RHOSTS Set BLANK_PASSWORDS to true in case there is no password set for the root account. set BLANK_PASSWORDS true


![272231156-ef8720da-118d-49aa-84e3-9c6fba2df3df](https://github.com/durga46/Metasploit-for-reconnaissance/assets/75235704/a1f9f361-c9f9-486f-a484-e2b8192bc415)

## RESULT:
The Metasploit framework for reconnaissance is examined successfully
