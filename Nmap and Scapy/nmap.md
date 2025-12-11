**Host discovery**

The command is use toperform a discovery scan. In a discovery scan, the
scanning host sends an ICMP echo request (ping)

**nmap -sn 10.6.6.0/24**

![](Pictures/100000000000033F000001D49D2504A0.png){width="15.265cm"
height="8.595cm"}**Output:**

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

![](Pictures/100000000000045400000232339C2F20.png){width="17cm"
height="8.622cm"}

Find more information on these ports using the ****-A**** and ****-p****
command options. The ****-A**** option executes several functions
including running the default scripts. Specify more than one port to
scan by listing them separately with a comma between them.

**nmap -A -p139,445 10.6.6.23**

![](Pictures/100000000000047B00000353FA57C70E.png){width="17cm"
height="11.649cm"}Output

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

![](Pictures/10000000000003E40000025DA774DC73.png){width="17cm"
height="10.324cm"}

You can enumerate the network shares using another NSE script,
****smb-enum-shares.nse.**** To discover shared directories on the
target computer. Use the Nmap share enumeration script with the command:

**nmap \--script smb-enum-shares.nse -p445 10.6.6.23**

Output:

![](Pictures/100000000000037D0000034CD7060EFF.png){width="17cm"
height="13.986cm"}

Other networking commands:

└─\$ ifconfig

Determine the IP address of the Kali Ethernet interface

**└─\$ ip route**

****Determine the default gateway assigned to the Kali host using the**
**ip route** **command****

\$ ******cat /etc/resolv.conf**

Determine the address of the configured default DNS server by displaying
the contents of the ****/etc/resolv.conf**** file. You can view the file
using the ****cat \<file name\>**** command.\
