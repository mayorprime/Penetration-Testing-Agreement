**Host discovery**

The command is use toperform a discovery scan. In a discovery scan, the
scanning host sends an ICMP echo request (ping)

**nmap -sn 10.6.6.0/24**

**Output:**
<img width="831" height="468" alt="image" src="https://github.com/user-attachments/assets/190c7435-2ea5-44c1-ad81-ee0d42dc629d" />


### Obtain additional information about the host and services

You can use ****-v****, ****-p****, and ****-sV**** to find additional
information about the services running on the open ports.

**Operating System Discovery**

The ****-O**** option can be used to further determine information about
the operating system running on the target host.

**sudo nmap -O 10.6.6.23**

Some Nmap options require additional permissions and must be run as
****root**** or using the ****sudo**** command. To find operating system
information on the target host, use the ****nmap -O**** command. Enter
the password of ****kali**** when prompted.

Output:

<img width="1108" height="562" alt="image" src="https://github.com/user-attachments/assets/1b9125cb-0e1e-455a-b591-b6261e426484" />


Find more information on these ports using the ****-A**** and ****-p****
command options. The ****-A**** option executes several functions
including running the default scripts. Specify more than one port to
scan by listing them separately with a comma between them.

**nmap -A -p139,445 10.6.6.23**

Output
<img width="1147" height="851" alt="image" src="https://github.com/user-attachments/assets/ea74f36d-06cd-4fce-91ca-ba23b1c680e8" />



### SMB Services with Scripts

The Server Message Block (SMB) protocol is a network file sharing
protocol supported on Windows computers and by SAMBA on Linux. SMB
enables applications to read and write files or request services over a
network. Open public shares or shared devices such as print servers on a
network, can be accessed through SMB.

Nmap contains the powerful Nmap Scripting Engine (NSE), which enables
the programming of various Nmap options and conditional actions to be
taken as a result of the responses. NSE has built-in scripts that
enumerate users, groups, and network shares. One of the more commonly
used scripts for SMB discovery is the **smb-enum-users.nse** script. Use
the Nmap NSE script with the command:

**nmap \--script smb-enum-users.nse -p139,445 10.6.6.23**

Output
<img width="996" height="605" alt="image" src="https://github.com/user-attachments/assets/21ea1e08-d569-46a1-a489-0362ced6992b" />



You can enumerate the network shares using another NSE script,
****smb-enum-shares.nse.**** To discover shared directories on the
target computer. Use the Nmap share enumeration script with the command:

**nmap \--script smb-enum-shares.nse -p445 10.6.6.23**

Output:

<img width="893" height="844" alt="image" src="https://github.com/user-attachments/assets/97845f5c-2637-49cb-bab1-d5cdc73be501" />


Other networking commands:

└─\$ ifconfig

Determine the IP address of the Kali Ethernet interface

**└─\$ ip route** 

****Determine the default gateway assigned to the Kali host using the**
**ip route** **command****

\$ **cat /etc/resolv.conf**

Determine the address of the configured default DNS server by displaying
the contents of the ****/etc/resolv.conf**** file. You can view the file
using the ****cat \<file name\>**** command.\
