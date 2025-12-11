Use Scapy

****Enter the scapy** **command in a terminal window to load the Python
interpreter.****

****

****Use the sudo su ****c****ommand to obtain root privileges before
starting Scapy.****

****

****└─****\$ **sudo su**

\[sudo\] password for kali:

┌──(root㉿kali)-\[/home/kali\]

└─#

****After Enter scapy****

****

****└─****\# **scapy**

****

****

**Output:**

![](Pictures/100000000000042C000002963CF4CAF4.png){width="17cm"
height="10.536cm"}

At the \>\>\> prompt within the Scapy shell, enter the **ls()** function
to list all of the available default formats and protocols included with
the tool. The list is quite extensive and will fill multiple screens.

\>\>\> **ls()**

  
The **ls() **function can also be used to list details of the fields and
options available in each protocol header. The syntax to use a function
in Scapy is ********function_name(arguments). ********Use the **ls(IP)
**function to list the available fields in an IP packet header.

**\>\>\> ls(IP)**

Output:

![](Pictures/100000000000034B0000018B0835F04F.png){width="17cm"
height="7.964cm"}

### **Use the sniff() function**

### Use the **sniff() **function to collect traffic using the default eth0 interface of your VM. Start the capture with the **sniff() **function without specifying any arguments. {#use-the-sniff-function-to-collect-traffic-using-the-default-eth0-interface-of-your-vm.-start-the-capture-with-the-sniff-function-without-specifying-any-arguments.}

\>\>\> **sniff()**

**THEN**

****Open a second terminal window and **ping **an internet address, such
as **www.cisco.com**. Remember to specify the count using the **-c
**argument.****

****

**└─**\$ **ping -c 5 www.cisco.com**

**Output**

![](Pictures/10000000000002460000006803D5CC70.png){width="12.321cm"
height="2.201cm"}

### 

![](Pictures/10000000000004030000016C5D054236.png){width="17cm"
height="6.024cm"}

View the captured traffic using the **summary() **function. The **s=\_
**assigns the variable **s **to hold the output of the **sniff()
**function. The underscore ( \_ ) in Python is used to temporarily hold
the output of the last function executed.

\>\>\>**** **a=\_**

\>\>\>**** **a.summary()**

![](Pictures/10000000000003A0000002FDAA683000.png){width="17cm"
height="12.497cm"}

### Sniff Filters

To collected traffic to include only ICMP traffic, limit the number of
packets being collected, and view the individual packet details.

Use interface ID associated with 10.6.6.1 (br-internal) to capture ten
ICMP packets sent and received on the internal virtual network. The
syntax is **sniff(iface=\"****interface name****\", filter =
"****protocol****\", count =** i******nteger****)**.

\>\>\> **sniff(iface=\"br-internal\",filter = "icmp\",count = 10)**

** **Open a second terminal window and ping the host at 10.6.6.23.

┌──(kali㉿Kali)-\[\~\]

└─\$ **ping --c 10 10.6.6.23**

![](Pictures/100000000000037300000060AAA37924.png){width="17cm"
height="1.847cm"}

![](Pictures/100000000000076F0000018AB8648E22.png){width="17cm"
height="3.519cm"}

View the captured traffic with line numbers using the **nsummary()
**function.

\>\>\> **a=\_ **

\>\>\>**** **a.nsummary()**

Use the **wrpcap() **function to save the captured data to a pcap file
that can be opened by Wireshark and other applications. The syntax is
**wrpcap("****filename**.**pcap**\", **variable name****), **in this
example the variable that you stored the output is "**a**\".

\>\>\> **wrpcap("capture1.pcap\", a)**

## Create and Send an ICMP Packet

In a Scapy terminal window, enter the command to sniff traffic from the
interface connected to the 10.6.6.0/24 network.

\>\>\> **sniff(iface=\"br-internal\")**

2.  Open another terminal window, enter **sudo su **to perform packet
    crafting as root. Start a second instance of Scapy. Enter the
    **send**() function to send a packet to 10.6.6.23 with a modified
    ICMP payload.

┌──(kali㉿kali)-\[\~\]

└─\$ **sudo su**

\[sudo\] password for kali:

┌──(root㉿kali)-\[/home/kali\]

└─# **scapy**

\>\>\> **send(IP(dst=\"10.6.6.23\")/ICMP()/\"This is a test\")**

Response

Sent 1 packet

3.  Return to the first terminal window and press **CTRL-C**. You should
    receive a response similar to this:

\^C\<Sniffed: TCP:0 UDP:0 ICMP:2 Other:0\>

4.  Enter the summary command to display the summary with packet
    numbers.

\>\>\> **a=\_**

\>\>\> **a.nsummary()**

## Create and Send a TCP SYN Packet

a.  In the original Scapy terminal window, begin a packet capture on the
    internal interface attached to the 10.6.6.0/24 network. Use the
    interface name that you obtained previously.
b.  Navigate to the second terminal window. Create and send a TCP SYN
    packet using the commad shown.

> \>\>\> **send(IP(dst=\"10.6.6.23\")/TCP(dport=445, flags=\"S\"))**

> 1 packet sent

> This command sent an IP packet to the host with IP address 10.6.6.23.
> The packet is addressed to TCP port 445 and has the S (SYN) flag set.

c.  Close the terminal window.

### 

###  Review the captured packets. {#review-the-captured-packets.}

a.  In the original Scapy terminal window, stop the packet capture by
    pressing **CTRL-C**. The output should be similar to that shown.

> \^C\<Sniffed: TCP:3 UDP:0 ICMP:0 Other:0\>

b.  View the captured TCP packets using the **nsummary()** function.
    Display the detail of the TCP packet that was returned from the
    target computer at 10.6.6.23.

> \>\>\> **a\[******packet number******\]**
