# Cybersecurity Lab Environment Setup

**Networkwalks Cybersecurity Internship | Week 1 | Project Module 1**

## 1. Project Overview

This project focuses on building a virtual cybersecurity testing environment using Oracle VirtualBox and Kali Linux.

The objective is to create a controlled virtual laboratory where cybersecurity tools, network reconnaissance, vulnerability assessment, packet analysis and other authorized security-testing activities can be practised safely.

The laboratory uses a dedicated VirtualBox NAT Network, allowing future virtual machines to communicate with one another while maintaining outbound internet connectivity.

## 2. Project Objectives

The main objectives of this project are:

- Install and configure Oracle VirtualBox.
- Install 7-Zip for extracting virtual machine archives.
- Download and import Kali Linux as a virtual machine.
- Create a dedicated NAT Network using the 10.0.0.0/24 subnet.
- Configure Kali Linux with a static IP address.
- Enable shared clipboard and bidirectional drag-and-drop.
- Configure a shared folder between Windows and Kali Linux.
- Verify internet connectivity and DNS resolution.
- Create a clean virtual machine snapshot for recovery.
- Document the complete laboratory setup.

## 3. Lab Architecture

The laboratory consists of:

- Host Operating System: Windows [10/11]
- Hypervisor: Oracle VirtualBox [actual version]
- Guest Operating System: Kali Linux [actual version]
- Virtual Network: NAT Network
- Network Name: NatNetwork
- Network Address: 10.0.0.0/24
- Kali IP Address: 10.0.0.2/24
- Default Gateway: 10.0.0.1
- DNS Server: 8.8.8.8

## 4. Lab Configuration

| Component | Configuration |
|---|---|
| Host OS | Windows [version] |
| Hypervisor | VirtualBox [version] |
| Guest OS | Kali Linux [version] |
| Virtual Network | NAT Network |
| Network Name | NatNetwork |
| Network CIDR | 10.0.0.0/24 |
| Kali IP | 10.0.0.2/24 |
| Gateway | 10.0.0.1 |
| DNS | 8.8.8.8 |
| Kali RAM | [actual allocated RAM] |
| Shared Folder | downloads |

## 5. Installation and Configuration Procedure

### Step 1: Install 7-Zip

Downloaded and installed 7-Zip to extract the Kali Linux virtual machine archive.

Official resource: https://7-zip.org/download.html

### Step 2: Install VirtualBox

Downloaded and installed Oracle VirtualBox to create and manage virtual machines.

Official resource: https://virtualbox.org/wiki/Downloads

### Step 3: Create NAT Network

Created a dedicated NAT Network in VirtualBox.

Configuration:
- Network Name: NatNetwork
- IPv4 Prefix: 10.0.0.0/24
- IPv6: Disabled

### Step 4: Import Kali Linux

Downloaded the official prebuilt Kali Linux VirtualBox image and imported it into VirtualBox.

Configured its network adapter to use the previously created NatNetwork.

### Step 5: Configure Kali Linux Networking

Identified the active network connection using:

```bash
nmcli connection show --active
```

Configured the static IP address using NetworkManager.

```bash
sudo nmcli connection modify "Wired connection 1" ipv4.method manual ipv4.addresses 10.0.0.2/24 ipv4.gateway 10.0.0.1 ipv4.dns 8.8.8.8
```

Restarted the network connection and verified the configuration.

### Step 6: Configure VirtualBox Integration

Configured the following settings:

- Shared Clipboard: Bidirectional
- Drag and Drop: Bidirectional
- Shared Folder: downloads
- Auto-mount: Enabled
- Make Permanent: Enabled

### Step 7: Create Virtual Machine Snapshot

Created a clean baseline snapshot named:

**Clean Kali - Network Setup**

This snapshot provides a recovery point for future cybersecurity practicals and experiments.

## 6. Network Verification

The following commands were used to verify the laboratory configuration.

### Check IP Address

```bash
ip -br addr
```

Expected Kali IP: 10.0.0.2/24

### Check Routing Table

```bash
ip route
```

Expected gateway: 10.0.0.1

### Test Gateway Connectivity

```bash
ping -c 4 10.0.0.1
```

### Test Internet Connectivity

```bash
ping -c 4 8.8.8.8
```

### Test DNS Resolution

```bash
nslookup networkwalks.com
```

### Verify Nmap Installation

```bash
nmap --version
```

### Verify Shared Folder

```bash
ls -ld /media/sf_downloads
```

**Actual verification results:** [Describe your observed results here.]

## 7. Problems Encountered and Troubleshooting

Document the actual problems encountered during the setup.

### Problem 1: [Actual problem encountered]

**Cause:** [Explain the cause if identified.]

**Solution:** [Describe the steps used to resolve it.]

**Verification:** [Explain how you confirmed the solution.]

### Problem 2: [Actual problem encountered, if any]

**Cause:** [Explain the cause.]

**Solution:** [Describe the troubleshooting process.]

If no issue occurred, state that the setup was completed without encountering a major technical issue. Do not invent troubleshooting incidents.

## 8. What I Learned

Through this project, I learned:

1. How virtualization works and how to create virtual machines using VirtualBox.
2. The difference between NAT and NAT Network.
3. How to configure a dedicated virtual network using an IPv4 subnet.
4. How to assign a static IP address in Kali Linux.
5. How gateways, subnet masks and DNS servers work together.
6. How to verify network connectivity using ping and nslookup.
7. How to configure shared folders and clipboard integration.
8. Why snapshots are important for restoring a clean virtual machine.
9. How to prepare an isolated environment for future ethical hacking and penetration-testing exercises.

## 9. Security and Ethical Considerations

This laboratory is intended strictly for educational purposes and authorized security testing.

All practical activities will be conducted only on systems owned by me or systems for which I have explicit permission to perform security testing.

## 10. Tools and Resources

- 7-Zip: https://7-zip.org/download.html
- Oracle VirtualBox: https://virtualbox.org/wiki/Downloads
- Kali Linux: https://kali.org/get-kali

## 11. Project Information

Program: Networkwalks Cybersecurity Internship

Week: 01

Project Module: WK1-PM1

Project: Practical Lab Environment Setup

Author: Shaurya Gupta

Batch: B084

Repository: GitHub

**Note:** Screenshots documenting the actual installation, network configuration, connectivity verification, shared-folder configuration and snapshot are included in the screenshots folder.