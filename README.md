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

<h2>High-Level Steps</h2>

<h2>Part 1: Azure Resource Creation and Network Configuration</h2>

- Created a Resource Group in Microsoft Azure to logically organize and manage related resources within a single deployment environment.

- Deployed a Windows 10 Virtual Machine (VM) within the newly created Resource Group to serve as a client or administrative host.

- Configured a new Virtual Network (VNet) and Subnet during the Windows VM setup to establish secure network segmentation and communication pathways.

- Provisioned a Linux (Ubuntu) Virtual Machine (VM) using the same Resource Group and Virtual Network for cross-platform connectivity and testing.

- Utilized Azure Network Watcher to analyze and visualize the Virtual Network topology, verifying connections and network configurations between VMs.


<h2>Part 2: Network Connectivity Testing and Traffic Analysis</h2>

- Connected to the Windows 10 Virtual Machine via Remote Desktop to perform network monitoring and diagnostic tasks.

- Installed and configured Wireshark within the Windows VM to capture and analyze network packets in real time.

- Applied ICMP filters in Wireshark to isolate and monitor ping traffic between virtual machines and external networks.

- Retrieved the private IP address of the Ubuntu VM and conducted ping tests from the Windows VM to verify internal network connectivity.

- Observed ICMP request and reply packets in Wireshark, confirming successful communication between the Windows and Ubuntu VMs.

- Executed ping commands to a public website (e.g., www.google.com
) to analyze external network communication and ICMP behavior in Wireshark.

- Initiated a continuous ping session from the Windows VM to the Ubuntu VM to monitor sustained ICMP traffic.

- Modified Network Security Group (NSG) rules in Azure to disable inbound ICMP traffic for the Ubuntu VM, demonstrating controlled traffic blocking.

- Monitored Wireshark and command-line feedback to verify the cessation of ICMP traffic due to NSG restrictions.

- Re-enabled inbound ICMP traffic within the NSG to restore network connectivity and confirmed successful packet transmission in Wireshark.

- Terminated the continuous ping process upon successful validation of NSG rule enforcement and network functionality.
 <h2>Part 3: Secure Shell (SSH) Traffic Monitoring</h2>

- Configured Wireshark filters to capture and analyze SSH (Secure Shell) traffic between virtual machines.

- Established an SSH connection from the Windows 10 VM to the Ubuntu VM using its private IP address to test secure remote access.

- Executed authentication and command-line interactions (e.g., entering username and password) while monitoring encrypted SSH packet exchanges in Wireshark.

- Terminated the SSH session by exiting the terminal, confirming the closure of the secure connection in Wireshark traffic logs.


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

<h2>Conclusion</h2>


- Azure Virtual Network Setup and Network Traffic Analysis Project

- Provisioned and configured Azure infrastructure, including a Resource Group, Windows 10 and Linux (Ubuntu) Virtual Machines, Virtual Network (VNet), and Subnets to establish a multi-OS cloud environment.

- Utilized Azure Network Watcher to visualize and validate network topology and connectivity between deployed resources.

- Performed network diagnostics and traffic capture by connecting to the Windows VM via Remote Desktop and using Wireshark to analyze key network protocols.

- Captured and analyzed ICMP traffic to verify internal and external connectivity, and demonstrated traffic control by modifying Network Security Group (NSG) rules to block and unblock ICMP packets.

- Monitored SSH traffic to confirm secure remote shell connections and encrypted packet exchange between Windows and Ubuntu VMs.

- Captured DHCP traffic during IP address renewal processes to ensure proper network configuration and lease management.

- Analyzed DNS queries and responses by resolving domain names with nslookup and verifying DNS traffic flow within the network.

- Observed continuous RDP traffic to understand how Remote Desktop Protocol maintains active sessions through constant data transmission, even during idle periods.
