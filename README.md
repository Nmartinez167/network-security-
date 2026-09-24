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

Part 1:
   Observing ICMP Traffic**
  
- Install Microsoft Remote Desktop on your Mac and connect to the Windows 10 VM.

- Install [Wireshark](https://www.wireshark.org) within the Windows 10 VM.

- Open Wireshark and start a packet capture.
- 
- Filter for ICMP traffic in Wireshark.
- Retrieve the private IP address of the Ubuntu VM and attempt to ping it from the Windows 10 VM.
- Observe ping requests and replies in Wireshark.
- From the Windows 10 VM, open Command Line or PowerShell, and ping a public website (e.g., `www.google.com`).
- Observe the ICMP traffic in Wireshark.

Part 2: **2. Configuring a Firewall (Network Security Group)**
  
- Initiate a perpetual/non-stop ping from the Windows 10 VM to the Ubuntu VM.
 
- Open the Network Security Group (NSG) associated with the Ubuntu VM and disable inbound ICMP traffic.
 
- Return to the Windows 10 VM and observe the ICMP traffic and command line ping activity in Wireshark.
- Re-enable inbound ICMP traffic in the NSG.
- Back in the Windows 10 VM, observe the ICMP traffic and ping activity resuming in Wireshark.
- Stop the ping activity.


- <img width="50%" height="50%" alt="dayy66666" src="https://github.com/user-attachments/assets/ce9955b5-7c93-4834-8816-f4252439276d" />
<img width="50%" height="50%" alt="dayyyyy77777" src="https://github.com/user-attachments/assets/78e8e87f-af18-430e-a2f3-24b52e51a2cd" />

- Install and configure Wireshark within the Windows VM to capture and analyze network packets in real time.
  
- <img width="50%" height="50%" alt="Screenshot 2026-07-02 152416" src="https://github.com/user-attachments/assets/4f4e1f72-1341-4e56-922d-c2a8946c3111" />

After starting wireshark we can observe all the traffic on the backend of this virtual machine.
<img width="50%" height="50%" alt="Screenshot 2026-07-02 153412" src="https://github.com/user-attachments/assets/de9f7abc-ce63-4a39-a8fa-1820d12b1c01" />


- Applied ICMP filters in Wireshark to isolate and monitor ping traffic between virtual machines and external networks.

- <img width="50%" height="50%" alt="Screenshot 2026-07-02 154001" src="https://github.com/user-attachments/assets/2193adab-95a0-4bb5-8f46-1776736fa7a0" />


- Next we Retrieve the private IP address of the linux VM from our azure portal and conducted ping tests from the Windows VM to verify internal network connectivity by opening up windows powershell and using the ping command.
<img width="50%" height="50%" alt="summm" src="https://github.com/user-attachments/assets/72b915d0-426a-4d12-9f4e-dca613e0e8dc" />
<img width="50%" height="50%" alt="Screenshot 2026-07-08 134559" src="https://github.com/user-attachments/assets/49ab5b29-1629-4c62-b70d-17e7459978e7" />

- Observed ICMP request and reply packets in Wireshark, confirming successful communication between the Windows and Ubuntu VMs.

- Next i Initiated a continuous ping session from the Windows VM to the Ubuntu VM to monitor sustained ICMP traffic.
- <img width="50%" height="50%" alt="new day" src="https://github.com/user-attachments/assets/788e6f15-7f6c-445a-a228-e14da1f43888" />


- Modified Network Security Group (NSG) rules in Azure to disable inbound ICMP traffic for the Ubuntu VM, demonstrating controlled traffic blocking.
<img width="50%" height="50%" alt="ttttt" src="https://github.com/user-attachments/assets/33c1c55f-a8bd-42d4-9c62-79553b073e98" />

  -Now we can see the request has timed out due to our new inbound rule we set through the azure portal settings.
<img width="50%" height="50%" alt="gggggg" src="https://github.com/user-attachments/assets/e95aca75-6072-4a57-ae4b-6a12bdc2ddf5" />

- Re-enabled inbound ICMP traffic within the NSG by simply deletting the rule we set earlier to restore network connectivity and confirmed successful packet transmission in Wireshark.<img width="50%" height="50%" alt="sssss" src="https://github.com/user-attachments/assets/a8e0ca03-ac71-4785-84a5-3c6d0add7c80" />

-Here we can see that we are once again getting a reply from our linux VM
<img width="50%" height="50%" alt="kkkkkk" src="https://github.com/user-attachments/assets/6c10e281-9f32-4afe-a9d9-5390cbd7abab" />

 <h2>Part 3: Secure Shell (SSH) Traffic Monitoring</h2>

- In the Windows 10 VM, open Wireshark and start a packet capture.

- Filter for SSH traffic in Wireshark.

- Using PowerShell in the Windows 10 VM, SSH into the Ubuntu VM using its private IP address:
  - `ssh labuser@<private IP address>`
- Type commands (e.g., username, password) in the Linux SSH session and observe SSH traffic in Wireshark.
- Exit the SSH connection by typing `exit` and pressing [Enter].

<img width="50%" height="50%" alt="lllllllll" src="https://github.com/user-attachments/assets/59769704-3e01-43f0-9160-25687b434326" />

<img width="50%" height="50%" alt="lmllllmk" src="https://github.com/user-attachments/assets/2a76f155-5ca2-480e-a511-f88f853a165d" />

<img width="50%" height="50%" alt="yeeeeerrrrr" src="https://github.com/user-attachments/assets/57e346c6-6dbe-4982-9814-cc3cba6634ca" />

- Terminated the SSH session by exiting the terminal, confirming the closure of the secure connection in Wireshark traffic logs.
  
<img width="50%" height="" alt="logout" src="https://github.com/user-attachments/assets/e5cfdb45-3d9e-412c-aa47-75af4bb414c8" />


<h2>Part 4: DHCP Traffic Analysis</h2>

- Back in Wireshark, filter for DHCP traffic.
  
- In the Windows 10 VM, attempt to issue a new IP address using the Command Line:
  - `ipconfig /renew`
- Observe DHCP traffic appearing in Wireshark.

<img width="737" alt="Screenshot 2025-01-23 at 8 53 19 PM" src="https://github.com/user-attachments/assets/d1918c31-508f-4f35-b7c5-f179827af4f1" />
<img width="910" alt="Screenshot 2025-01-23 at 8 53 42 PM" src="https://github.com/user-attachments/assets/e4daa4b5-fff0-4e7f-9738-6feecbb805cf" />


<h2>Part 5: DNS Traffic Capture and Analysis</h2>
- Back in Wireshark, filter for DNS traffic.

- In the Windows 10 VM, use `nslookup` to resolve the IP addresses of `google.com` and `disney.com`:
  - `nslookup google.com`
  - `nslookup disney.com`
- Observe DNS traffic in Wireshark.



<img width="50%" height="50%" alt="disneyyyy" src="https://github.com/user-attachments/assets/9f7589f0-051b-4077-a9c3-25f44dc2b953" />

- Executed nslookup commands on the Windows 10 VM to resolve domain names such as google.com and disney.com.

<img width="1713" height="946" alt="dassssssssssss" src="https://github.com/user-attachments/assets/a3803c3e-cf5e-4702-9a8e-179e9ff35f09" />
-

<h2>Part 6: RDP Traffic Monitoring</h2>

- Configured Wireshark with filters to capture RDP (Remote Desktop Protocol) traffic using tcp.port == 3389.

- Monitored continuous RDP data streams between the local machine and the Windows 10 VM during an active remote session.

- Analyzed RDP behavior showing consistent data transmission to maintain session connectivity and provide real-time screen updates, even during idle periods.
- 
<img width="50%" height="50%" alt="rdp" src="https://github.com/user-attachments/assets/776342ea-2b2d-421b-9d6b-82e8815c36c1" />


