# Zoe-s-games
# Virtual Network Security Lab

## Objective
To design, deploy, and manage an isolated virtual network environment simulating a small enterprise network architecture. This project demonstrates practical skills in hypervisor networking, firewall configuration, secure system deployment, and network traffic routing.

## Network Topology
The lab environment is hosted on a Windows 11 machine using a Type 2 hypervisor. It consists of a virtualized firewall namely pfSense acting as the network gateway and a client machine Ubuntu VM operating within an isolated internal network.

*   **Host Machine:** Windows 11
*   **Hypervisor:** VirtualBox
*   **Firewall / Gateway:** pfSense
    *   Adapter 1 (WAN): NAT (Simulating external internet access)
    *   Adapter 2 (LAN): Internal Network (Serving the isolated lab environment)
*   **Client Machine:** Ubuntu Linux
    *   Adapter 1: Internal Network (Routing all traffic through the pfSense gateway)

## Skills Demonstrated
*   **Hypervisor Administration:** Configuring VirtualBox network adapters (NAT and Internal Networks) to enforce traffic isolation.
*   **Firewall Deployment:** Installing and configuring pfSense, establishing WAN/LAN interfaces, and managing the web GUI.
*   **Network Services:** Configuring DHCP and NAT to provide IP addressing and external connectivity to the internal client.
*   **Data Integrity & Security:** Performing cryptographic hash verifications on OS ISO files prior to installation via command-line tools.
*   **System Administration:** Deploying and configuring Linux and FreeBSD-based operating systems, including display and console optimizations.

## Tools & Technologies
*   **VirtualBox**
*   **pfSense**
*   **Ubuntu Linux**
*   **PowerShell** (for integrity verification)

## Challenges & Solutions
**Cryptographic Integrity Checks:** Prior to installing the virtual machines, I verified the SHA256 hashes of the downloaded ISO files. While automating the comparison using PowerShell, I encountered an issue where the `[Microsoft.Powershell.Utility.FileHash]` object threw an error when attempting to use string manipulation methods on it. I resolved this by correctly extracting the `.Hash` property from the object before comparing the values, successfully validating the files were uncorrupted.

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
