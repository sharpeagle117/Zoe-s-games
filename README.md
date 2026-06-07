# Zoe-s-games
# Enterprise-Grade Virtual Network Security Lab

## Project Overview
This project demonstrates the design, deployment, and configuration of a secure, segmented virtual network. Built entirely within a hypervisor environment, it utilizes a dedicated gateway firewall to enforce strict access controls and monitor traffic flowing to and from an isolated internal sandbox. It demonstrates practical skills in hypervisor networking, firewall configuration, secure system deployment, and network traffic routing.

## Architecture & Topology
The network relies on a strict perimeter defense model. It is hosted on a Windows 11 machine using a Type 2 hypervisor. All client traffic is routed through the central firewall, which acts as the default gateway and primary chokepoint for packet analysis, access control lists (ACLs), and security testing.

*   **Host Machine:** Windows 11
*   **Hypervisor:** VirtualBox
*   **Firewall / Gateway:** pfSense
    *   Adapter 1 (WAN): NAT (Simulating external internet access)
    *   Adapter 2 (LAN): Internal Network (Serving the isolated lab environment)
*   **Client Machine:** Ubuntu
    *   Adapter 1: Internal Network (Routing all traffic through the pfSense gateway)
*   **Client Machine:** Kali Linux
    *   Adapter 1: Internal Network (Routing all traffic through the pfSense gateway)

## Skills Demonstrated
*   **Hypervisor Administration:** Configuring VirtualBox network adapters (NAT and Internal Networks) to enforce traffic isolation.
*   **Firewall Deployment:** Installing and configuring pfSense, establishing WAN/LAN interfaces, and managing the web GUI.
*   **Network Services:** Configuring DHCP and NAT to provide IP addressing and external connectivity to the internal client.
*   **Data Integrity & Security:** Performing cryptographic hash verifications on OS ISO files prior to installation via command-line tools.
*   **System Administration:** Deploying and configuring Linux and FreeBSD-based operating systems, including display and console optimizations.

## Tools & Technologies
*   **VirtualBox TypeII Hypervisor**
*   **pfSense Firewall ACLs**
*   **Ubuntu Linux CLI**
*   **Host OS PowerShell** (for integrity verification)

## Challenges & Solutions
**Cryptographic Integrity Checks:** Prior to installing the virtual machines, I verified the SHA256 hashes of the downloaded ISO files. While automating the comparison using PowerShell, I encountered an issue where the Microsoft.Powershell.Utility.FileHash object threw an error when attempting to use string manipulation methods on it. I resolved this by correctly extracting some spaces from the object before comparing the values, successfully validating the files were uncorrupted.

**Ubuntu VM Installation:** While attempting to install an Ubuntu VM in VirtualBox, the application hung on launch, showing only the menu bar with no boot sequence. I verified that hardware virtualization was enabled in Windows Task Manager and confirmed the ISO installation media was correctly mounted, but the issue persisted.
Solution: The root cause was a conflict between VirtualBox and the host OS security layers. Disabling Memory Integrity (Core Isolation) in Windows 11 and restarting the host resolved the hypervisor clash. The Ubuntu installation proceeded smoothly thereafter.

**Environment Optimization:** Adjusting to the default virtualized environments required optimizing the shell console sizing for the firewall and configuring guest additions to ensure the Ubuntu client display scaled correctly for efficient workflow management.

## Project Documentation

### 1. Virtual Machine Network Configuration
*This image demonstrates the VirtualBox adapter settings, ensuring the client machine is strictly isolated to the Internal Network and must route through the firewall.*
![VirtualBox Network Settings](link-to-your-image.jpg)

### 2. Pre-Deployment Data Integrity Verification
*Using PowerShell to verify the cryptographic hash of the downloaded ISO files before installation, ensuring no file corruption or tampering.*
![PowerShell Hash Check](link-to-your-image.jpg)

### 3. Firewall Interface Dashboard
*The firewall web interface showing the active WAN and LAN interfaces, confirming successful deployment and IP assignment.*
![Firewall Dashboard](link-to-your-image.jpg)

### 4. Client Connectivity & Routing
*The Ubuntu client terminal successfully pinging an external IP address, proving that NAT, DNS, and internal routing through the firewall are functioning correctly.*
![Ubuntu Ping Test](link-to-your-image.jpg)
