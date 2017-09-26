## Windows Network Diagnostic Commands

The following are common Microsoft Windows [network](http://whirlpool.net.au/wiki/network) commands

**ipconfig**  
Ipconfig is a Console Command which can be issued to the Command Line Interpreter (or command prompt) to display the network settings currently assigned to any or all network adapters in the machine. This command can be utilised to verify a network connection as well as to verify your network settings.

[www.computerhope.com/ipconfig.htm](http://www.computerhope.com/ipconfig.htm)

For Windows 95,98,ME use winipcfg  
[http://support.microsoft.com/default.aspx?scid=kb;en-us;141698](http://support.microsoft.com/default.aspx?scid=kb;en-us;141698)

**netstat**  
Displays active TCP connections, ports on which the computer is listening, Ethernet statistics, the [IP](http://whirlpool.net.au/wiki/IP) routing table, IPv4 statistics (for the IP, ICMP, TCP, and UDP protocols), and IPv6 statistics (for the IPv6, ICMPv6, TCP over IPv6, and UDP over IPv6 protocols). Used without parameters, netstat displays active TCP connections.

[http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/netstat.mspx](http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/netstat.mspx)

**tracert**  
The tracert command is used to visually see a network packet being sent and received and the amount of hops required for that packet to get to its destination.

Users with Microsoft Windows 2000 and Windows XP who need additional information network latency and network loss should also consider using the pathping command.

[www.computerhope.com/tracert.htm](http://www.computerhope.com/tracert.htm)

**[ping](http://whirlpool.net.au/wiki/ping)**  
Helps in determining TCP/IP Networks IP address as well as determine issues with the network and assists in resolving them.

[www.computerhope.com/pinghlp.htm](http://www.computerhope.com/pinghlp.htm)

**pathping**  
Provides information about network latency and network loss at intermediate hops between a source and destination. Pathping sends multiple Echo Request messages to each router between a source and destination over a period of time and then computes results based on the packets returned from each router.

[www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/pathping.mspx?mfr=true](http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/pathping.mspx?mfr=true)

**telnet**  
Telnet is software that allows users to remotely access another computer such as a server, network device, or other computer. With telnet users can connect to a device or computer, manage a network device, setup a device, transfer files, etc.

[www.computerhope.com/software/telnet.htm#03](http://www.computerhope.com/software/telnet.htm#03)

**ftp**  
FTP is short for File Transfer Protocol, this page contains additional information about the FTP command and help using that command in Unix and MS-DOS (Windows).

[www.computerhope.com/software/ftp.htm](http://www.computerhope.com/software/ftp.htm)

**route**  
The function and syntax of the Windows ROUTE command is similar to the UNIX or Linux route command. Use the command to manually configure the routes in the routing table.

[www.computerhope.com/routehlp.htm](http://www.computerhope.com/routehlp.htm)

**arp**  
Displays, adds, and removes arp information from network devices.

[www.computerhope.com/arphlp.htm](http://www.computerhope.com/arphlp.htm)

**nslookup**  
Displays information that you can use to diagnose Domain Name System (DNS) infrastructure. Before using this tool, you should be familiar with how DNS works. The Nslookup command-line tool is available only if you have installed the TCP/IP protocol.

[http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/nslookup.mspx](http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/nslookup.mspx)

**nbtstat**  
MS-DOS utility that displays protocol statistics and current TCP/IP connections using NBT.

[www.computerhope.com/nbtstat.htm](http://www.computerhope.com/nbtstat.htm)

**netsh**  
[http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/netsh.mspx](http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/netsh.mspx)

One common way of using netsh is to reset the TCP/IP in Windows 2k/XP

Type this in Run or DOS Window – "netsh int ip reset"

In Windows XP you can run a graphical diagnostics by typing "netsh diag gui" into the run dialogue box. (This may take a little time to startup)

**getmac**

DOS command used to show both local and remote MAC addresses. When run with no parameters (ie. 

getmac) it displays MAC addresses for the local system. When run with the /s parameter (eg. 

getmac /s \\foo) it displays MAC addresses for the remote computer. When the /v parameter is used, it also displays the associated connection name and network adapter name.

Included with Windows XP, Windows 2003 Server, and Windows 2000 Resource Kit. Can be downloaded for the Windows 2000 here: [http://www.microsoft.com/windows2000/techinfo/reskit/tools/existing/getmac-o.asp](http://www.microsoft.com/windows2000/techinfo/reskit/tools/existing/getmac-o.asp)

[http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/getmac.mspx](http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/getmac.mspx)

**Find All Active/Used IP Addresses on Your Network**  
There is a really neat way that you can quite easily find all active/used IP Addresses on your network without the need for any third party applications or worse, pinging each IP Address individually.

Open the Command Prompt and type in the following:

FOR /L %i IN (1,1,254) DO ping **-n 1** 192.168.10.%i | FIND /i "Reply"&gt;&gt;c:\ipaddresses.txt

Change 192.168.10 to match you own network.