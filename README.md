<p align="center">
<img src="https://imgur.com/fxZWPHg.png"/>
</p>

<h1>NMAP Host Scanning On a Kali Linux VM </h1>
This walkthrough demonstrates some basic scans using Nmap on Kali Linux against Windows XP, a vulnerable version of Windows.. <br />


<h2>Environments and Technologies Used</h2>

- VMWare
- Remote Desktop
- NMAP
-Window XP


<h2>Operating Systems Used </h2>

- Kali Linix</b> (version 22H2)
- Windows XP


<p>  
<img src = "https://imgur.com/6zeEWr6.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>

</p>

 <p>
1. Open VMWare and click on the Kali Linux ISO to configure its virtual machine. On Kali Linux, click on the command line and then click on the 'Terminal Emulator". 


<p>
<img src="https://imgur.com/xY9CsCt.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>

<p>
2. Before the Windows XP ISO is scanned by NMAP, we need to identify the IP address of the Windows XP virtual machine. To find the IP address, on the Windows XP VM, go to "Start", then "Run". In the terminal lime, type ipconfig to receive the IP address.

</p>
<br />

<p>
<img src="https://imgur.com/LJblN6C.png" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
 3. In the Kali Linux VM, type "nmap -sV -O [ip address of Windows XP]"  into the command line. The services that the Windows XP VM runs will be listed by using the command -sV. The operating system used in the Windows XP VM will be stated when using the command -O. 
</p>


4. When analyzing the results from the Nmap scan, we can see some vulnerabilities in the Windows XP VM. First, there is the vulnerability of Microsoft Windows RPC that runs on TCP port 135.  Windows RPC is 
susceptible to buffer overflow attacks and malware such as trojan horses, and worms. Additionally, Microsoft XP -ds over TCP 445 is another  vulnerable service. SMB allows for the execution of arbitrary commands over a network. 

<p>
<img src="https://imgur.com/IZqiDYL.png" width="80%" alt="Disk Sanitization Steps"/>
</p>

5. Next, the command -sA can be used to detect firewall rules by sending ACK messages to the target host. If this specific scan returns an RST packet, then the port is closed and no services are listening on that port. If the target host returns a SYN/ACK, then the port is open a service is listening on the host. Additionally, if no response is returned by the scan, then the port is filtered by the firewall. According to the scan done against the Windows XP VM, the host is down which means that ports are most likely being blocked by its firewall.
