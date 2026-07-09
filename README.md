# network-security-<p align="center">
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

<h2>Part 1: Azure Resource Creation and Network Configuration</h2>

- Create a Resource Group in Microsoft Azure make sure it is assigned to the designated subscription as well as the same region as our virtual machine we will be creating.
<img width="1087" height="620" alt="12335" src="https://github.com/user-attachments/assets/613f143f-54e2-409e-9308-6609f8318efc" />

- Deployed a Windows 10 Virtual Machine (VM) within the newly created Resource Group to serve as a client or administrative host.
<img width="1617" height="455" alt="6666666" src="https://github.com/user-attachments/assets/0058a52b-7ceb-42f9-8ede-b71ffad51ae1" />


- Provisioned a Linux (Ubuntu) Virtual Machine (VM) using the same Resource Group and Virtual Network for cross-platform connectivity and testing.
<img width="1101" height="920" alt="777777" src="https://github.com/user-attachments/assets/27d25cd0-4980-4b5e-8943-5e7e2849f24b" />

- Configured a new Virtual Network (VNet) and Subnet during the Windows VM setup to establish secure network segmentation and communication pathways.
<img width="1207" height="781" alt="88888" src="https://github.com/user-attachments/assets/b0f4825e-64db-48c6-b540-f15303773381" />
<img width="1181" height="843" alt="99999" src="https://github.com/user-attachments/assets/b00e5baa-4a89-49bd-a6c3-51a7b5d1c613" />


<h2>Part 2: Network Connectivity Testing and Traffic Analysis</h2

- Now we connect to the Windows 10 Virtual Machine via Remote Desktop to perform network monitoring and diagnostic tasks we do that by taking the I.P adress from the azure portal like so .
- <img width="1877" height="555" alt="dayy66666" src="https://github.com/user-attachments/assets/ce9955b5-7c93-4834-8816-f4252439276d" />
<img width="1827" height="621" alt="dayyyyy77777" src="https://github.com/user-attachments/assets/78e8e87f-af18-430e-a2f3-24b52e51a2cd" />

- Install and configure Wireshark within the Windows VM to capture and analyze network packets in real time.
  
- <img width="950" height="685" alt="Screenshot 2026-07-02 152416" src="https://github.com/user-attachments/assets/4f4e1f72-1341-4e56-922d-c2a8946c3111" />

After starting wireshark we can observe all the traffic on the backend of this virtual machine.
<img width="1918" height="986" alt="Screenshot 2026-07-02 153412" src="https://github.com/user-attachments/assets/de9f7abc-ce63-4a39-a8fa-1820d12b1c01" />


- Applied ICMP filters in Wireshark to isolate and monitor ping traffic between virtual machines and external networks.

- <img width="1939" height="1022" alt="Screenshot 2026-07-02 154001" src="https://github.com/user-attachments/assets/2193adab-95a0-4bb5-8f46-1776736fa7a0" />


- Next we Retrieve the private IP address of the linux VM from our azure portal and conducted ping tests from the Windows VM to verify internal network connectivity by opening up windows powershell and using the ping command.
<img width="1267" height="886" alt="summm" src="https://github.com/user-attachments/assets/72b915d0-426a-4d12-9f4e-dca613e0e8dc" />
<img width="1801" height="997" alt="Screenshot 2026-07-08 134559" src="https://github.com/user-attachments/assets/49ab5b29-1629-4c62-b70d-17e7459978e7" />

- Observed ICMP request and reply packets in Wireshark, confirming successful communication between the Windows and Ubuntu VMs.

- Next i Initiated a continuous ping session from the Windows VM to the Ubuntu VM to monitor sustained ICMP traffic.
- <img width="1805" height="1032" alt="new day" src="https://github.com/user-attachments/assets/788e6f15-7f6c-445a-a228-e14da1f43888" />


- Modified Network Security Group (NSG) rules in Azure to disable inbound ICMP traffic for the Ubuntu VM, demonstrating controlled traffic blocking.
<img width="1922" height="1012" alt="ttttt" src="https://github.com/user-attachments/assets/33c1c55f-a8bd-42d4-9c62-79553b073e98" />

  -Now we can see the request has timed out due to our new inbound rule we set through the azure portal settings.
<img width="1482" height="1016" alt="gggggg" src="https://github.com/user-attachments/assets/e95aca75-6072-4a57-ae4b-6a12bdc2ddf5" />

- Re-enabled inbound ICMP traffic within the NSG by simply deletting the rule we set earlier to restore network connectivity and confirmed successful packet transmission in Wireshark.<img width="1953" height="982" alt="sssss" src="https://github.com/user-attachments/assets/a8e0ca03-ac71-4785-84a5-3c6d0add7c80" />

-Here we can see that we are once again getting a reply from our linux VM
<img width="1918" height="806" alt="kkkkkk" src="https://github.com/user-attachments/assets/6c10e281-9f32-4afe-a9d9-5390cbd7abab" />

 <h2>Part 3: Secure Shell (SSH) Traffic Monitoring</h2>

- Configured Wireshark filters to capture and analyze SSH (Secure Shell) traffic between virtual machines we did that by opening up windows powershell and prompting the following command : ssh labuser@<private IP address>
Type commands (username, pwd, etc) into the linux SSH connection.
<img width="1530" height="837" alt="lllllllll" src="https://github.com/user-attachments/assets/59769704-3e01-43f0-9160-25687b434326" />

<img width="1614" height="902" alt="lmllllmk" src="https://github.com/user-attachments/assets/2a76f155-5ca2-480e-a511-f88f853a165d" />

<img width="1645" height="865" alt="yeeeeerrrrr" src="https://github.com/user-attachments/assets/57e346c6-6dbe-4982-9814-cc3cba6634ca" />

- Terminated the SSH session by exiting the terminal, confirming the closure of the secure connection in Wireshark traffic logs.
  
<img width="1589" height="849" alt="logout" src="https://github.com/user-attachments/assets/e5cfdb45-3d9e-412c-aa47-75af4bb414c8" />


<h2>Part 4: DHCP Traffic Analysis</h2>

- Applied Wireshark filters to capture and monitor DHCP (Dynamic Host Configuration Protocol) traffic on the network.

- Executed the ipconfig /renew command on the Windows 10 VM to request a new IP address from the DHCP server.

- Observed and analyzed DHCP negotiation packets in Wireshark, verifying communication between the VM and the DHCP server during IP lease renewal.

<h2>Part 5: DNS Traffic Capture and Analysis</h2>

- Applied Wireshark filters to capture DNS (Domain Name System) query and response traffic.

- Executed nslookup commands on the Windows 10 VM to resolve domain names such as google.com and disney.com.

- Monitored DNS query and response packets in Wireshark to verify successful domain name resolution and network communication.


<h2>Part 6: RDP Traffic Monitoring</h2>

- Configured Wireshark with filters to capture RDP (Remote Desktop Protocol) traffic using tcp.port == 3389.

- Monitored continuous RDP data streams between the local machine and the Windows 10 VM during an active remote session.

- Analyzed RDP behavior showing consistent data transmission to maintain session connectivity and provide real-time screen updates, even during idle periods.


