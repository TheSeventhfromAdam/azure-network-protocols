<p align="center">
<img src="https://i.imgur.com/Ua7udoS.png" alt="Traffic Examination"/>
</p>

<h1>Network Security Groups (NSGs) and Inspecting Traffic Between Azure Virtual Machines</h1>
In this tutorial, we observe various network traffic to and from Azure Virtual Machines with Wireshark as well as experiment with Network Security Groups. <br />


<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Various Command-Line Tools
- Various Network Protocols (SSH, RDH, DNS, HTTP/S, ICMP)
- Wireshark (Protocol Analyzer)

<h2>Operating Systems Used </h2>

- Windows 10 (21H2)
- Ubuntu Server 20.04

<h2>Key Points</h2>

- Create Resource Group
- Create two VMs (Windows and Ubuntu)
- SSH into Ubuntu VM 
- Install Wireshark to observe network traffic

<h2>Actions and Observations</h2>

<p>
<img src="https://i.imgur.com/1XiQB4R.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<img src="https://i.imgur.com/5dN540d.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<img src="https://i.imgur.com/rMqK7wl.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<img src="https://i.imgur.com/0o93DbD.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<img src="https://i.imgur.com/wanmfan.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<img src="https://i.imgur.com/n0wPwlo.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<img src="https://i.imgur.com/uvUKykZ.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<img src="https://i.imgur.com/D8oDLkG.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<img src="https://i.imgur.com/K8nzRCo.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<img src="https://i.imgur.com/FpGUR5F.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<img src="https://i.imgur.com/ALWIAUk.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<img src="https://i.imgur.com/awrjzi3.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Step 1
Create a Resource Group
Create a Windows 10 Virtual Machine (VM)
While you create your VM, select the previously created Resource Group
While you create the VM, allow it to create a new Virtual Network (Vnet) and Subnet
Create a Linux (Ubuntu) VM
When creating the VM, select the previously created Resource Group and Vnet
Observe Your Virtual Network within Network Watcher
</p>
<br />

<p>
<img src="https://i.imgur.com/osrh689.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<img src="https://i.imgur.com/WQysofa.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<img src="https://i.imgur.com/7NrsXPV.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<img src="https://i.imgur.com/3tDik7M.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<img src="https://i.imgur.com/CytXK8X.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<img src="https://i.imgur.com/8QirIqu.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<img src="https://i.imgur.com/V4sArMp.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Step 2
Use Remote Desktop to connect to your Windows 10 Virtual Machine
While in your Windows 10 Virtual Machine, Install Wireshark
Open Wireshark and filter for ICMP traffic only
Get the private IP address of the Ubuntu VM and try to ping it from inside the Windows 10 VM
Observe ping requests and replies on WireShark
From The Windows 10 VM, open command line or PowerShell and try to ping a public website (such as www.google.com) and observe the traffic in WireShark
</p>
<br />

<p>
<img src="https://i.imgur.com/2vPTXb3.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<img src="https://i.imgur.com/X6E7nc7.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<img src="https://i.imgur.com/8NwrrfS.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<img src="https://i.imgur.com/Crx6xMY.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<img src="https://i.imgur.com/xM9drJZ.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Step 3
Start a perpetual/non-stop ping from your Windows 10 VM to your Ubuntu VM
Open the Network Security Group  that your Ubuntu VM is using and disable incoming (inbound) ICMP traffic
Go to the Windows 10 VM, observe the ICMP traffic in WireShark and the command line Ping activity
Re-enable ICMP traffic for the Network Security Group that your Ubuntu VM is using
Go to your the Windows 10 VM, watch the ICMP traffic in WireShark and the command line Ping activity ( it should start working)
Stop the ping activity
</p>
<br />

<p>
<img src="https://i.imgur.com/62GwsYj.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<img src="https://i.imgur.com/VPejhGD.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<img src="https://i.imgur.com/jGtNpu8.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<img src="https://i.imgur.com/2IRkaZr.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<img src="https://i.imgur.com/dkuYIQV.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Step 4
Go to Wireshark and filter for SSH traffic only
From your Windows 10 VM, “SSH into” your Ubuntu Virtual Machine (using its private IP address)
Type commands (username, pwd, etc) into the linux SSH connection and observe SSH traffic spam in WireShark
Exit the SSH connection by typing ‘exit’ and pressing [Enter]
</p>
<br />

<p>
<img src="https://i.imgur.com/UBCpBZz.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<img src="https://i.imgur.com/4RVEgjQ.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<img src="https://i.imgur.com/DUqjerC.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Step 5
Back in Wireshark, filter for DHCP traffic only
From your Windows 10 VM, attempt to issue your VM a new IP address from the command line (ipconfig /renew)
Observe the DHCP traffic appearing in WireShark
</p>
<br />

<p>
<img src="https://i.imgur.com/LsgcdS9.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<img src="https://i.imgur.com/Bw5kjAi.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Step 6
Back in Wireshark, filter for DNS traffic only
From your Windows 10 VM within a command line, use nslookup to see what google.com or disney.com’s IP addresses are
Observe the DNS traffic being show in WireShark
</p>
<br />

<p>
<img src="https://i.imgur.com/343itn2.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Step 7
Back in Wireshark, filter for RDP traffic only (tcp.port == 3389)
Observe the immediate non-stop spam of traffic.
</p>
<br />

<p>
<img src="https://i.imgur.com/EWZwKt1.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<img src="https://i.imgur.com/uLJDZrZ.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<img src="https://i.imgur.com/Zpx5QBF.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Step 8
Close your Remote Desktop connection session
Delete the Resource Group or groups created at the start of this project
Verify if the Resource Groups have been deleted from Azure to ensure no additional charges
</p>
<br />
