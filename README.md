<p align="center">
<img src="https://imgur.com/fxZWPHg.png"/>
</p>

<h1>NMAP Host Scannning On a Kali Linux MV </h1>
This tutorial outlines the process of creating resource groups, virtual networks, network security groups, and subnets in Azure. <br />


<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines)
- Remote Desktop
- Azure Network Security Groups
-Wireshark

<h2>Operating Systems Used </h2>

- Windows 10</b> (version 22H2)
-Windows and Linux (Ubuntu) for Azure Virtual Machines.
-Wireshark

<h2> Video </h2>
https://clipchamp.com/watch/Wn8LPzyR6YQ
<h2>Installation Steps</h2>


<p>  
<img src = "https://imgur.com/XwWlhWr.png " height="80%" width="80%" alt="Disk Sanitization Steps"/>

</p>

<p>Overview</p>

<p>
<img src = "https://imgur.com/mCtRKHz.png" " height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
 <p>
1. Create a resource group in Azure. Mine is called "network group".
</p>                                                                                                 
                                                                                                     
<p>
<img src= "https://imgur.com/SKRHp7D.png" " height="80%" width="80%" alt="Disk Sanitization Steps" />
</p>

<p>
                                                                                                 
                                                                                                 
                                                                                                 
2. Create a Windows 10 Virtual Machine (VM). This virtual machine will be connected to the resource group we previously created.

</p>
<br />

<p>
<img src="https://imgur.com/xGqRr8p.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>

<p>
3. Create a Linux Ubuntu VM. While creating the VM, select the previously created resource group and vnet.


<p>
<img src="https://imgur.com/xGqRr8p.png
" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>


</p>
<br />

<p>
<img src="https://imgur.com/47CBowj.png" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
4. Observe the network you created within Network Watcher
</p>
<br />

<p>
<img src="https://imgur.com/PSMZPGv.png" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
5. Use Remote Desktop to connect to your Windows 10 Virtual Machine

</p>
<br />

<p>
<img src="https://imgur.com/ftWznpL.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
6. Within your Windows 10 Virtual Machine, Install Wireshark

</p>
<br />

<p>
<img src="https://imgur.com/YS2MA3u.png" alt="Disk Sanitization Steps"/>
</p>


7. Open Wireshark and filter for ICMP traffic only

</p>
<br />

<p>
<img src="https://imgur.com/P1ZcQuW.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
8. Retrieve the private IP address of the Ubuntu VM and attempt to ping it from within the Windows 10 VM. Observe your ping requests and replies within Wireshark.
</p>
<br />

<p>
<img src="https://imgur.com/TTstJ26.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>


9. From The Windows 10 VM, open the command line or PowerShell and attempt to ping a public website (such as www.google.com) and observe the traffic in Wireshark.


</p>
<br />

<p>
<img src="https://imgur.com/e2HbX69.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>

10. Initiate a perpetual/non-stop ping from your Windows 10 VM to your Ubuntu VM. Try disabling incoming ICMP traffic from the Network Security Group your Ubuntu uses. Then, try enabling the traffic once more.


<p>
<img src="https://imgur.com/tPMcOrQ.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>

11. Back in Wireshark, filter for SSH traffic only


<p>
<img src="https://imgur.com/kODyfJQ.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>

12. From your Windows 10 VM, “SSH into” your Ubuntu Virtual Machine (via its private IP address)
Type commands (ls, pwd, etc) into the linux SSH connection and observe SSH traffic spam in WireShark
Exit the SSH connection by typing ‘exit’ and pressing [Enter].

-SSH traffic commands to try out: pw,ls.

<p>
<img src="https://imgur.com/8RzNxG4.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>

13. Back in Wireshark, filter for DHCP traffic only. Observe the DHCP traffic appearing in Wireshark.

14. From your Windows 10 VM, attempt to issue your VM a new IP address from the command line (ipconfig/renew). Observe the DHCP traffic appearing in Wireshark.



<p>
<img src="https://imgur.com/SuPhxqh.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>


15. Back in Wireshark, filter for DNS traffic only


16. From your Windows 10 VM within a command line, use nslookup to see what google.com and disney.com’s IP addresses are



<p>
<img src="https://imgur.com/ym4QKCZ.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>

17.Back in Wireshark, filter for RDP traffic only (tcp.port == 3389)


18. Observe the immediate non-stop spam of traffic. This traffic seems to be nonstop because the RDP (protocol) is constantly showing you a live stream from one computer to another, therefore traffic is always being transmitted


19. Close your Remote Desktop and delete your resource group and all other resources used in the lab.
