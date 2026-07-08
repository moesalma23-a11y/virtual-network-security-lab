# Virtual Network Security Lab Setup

## Goal

After earning my CompTIA Network+ and Security+ certifications, I wanted to gain more hands-on experience with networking and cybersecurity technologies while continuing my education. Building this virtualized lab allows me to practice configuring network devices, implementing security controls, and using tools commonly found in cybersecurity environments.

**Virtual Cybersecurity Lab Using a Physical Cisco Switch and Virtual Machines Hosted on a Windows PC**

---

## Step 1: Configure the Virtual Environment

To begin, I built a small physical network using a Cisco Catalyst switch and a Windows desktop PC. The switch was connected to my home router for internet access, while my desktop was connected directly to the switch for management and testing purposes.

I used a console cable to perform the initial switch configuration, including setting the hostname and configuring administrative credentials.

![Switch Configuration](IMG_7419.jpeg)

After completing the initial setup, I enabled SSH to allow secure remote management of the switch without requiring a console connection.

![SSH Configuration](IMG_7423.jpeg)

To verify connectivity, I successfully pinged the switch from my PC and confirmed that the switch had learned my device's MAC address by reviewing the ARP table.

![Connectivity](IMG_7421.jpeg)

For now, the switch remains separate from the virtual lab environment. In the future, I plan to install an additional network interface card (NIC) in my PC so pfSense can interact directly with my physical network infrastructure.

I then installed pfSense in VirtualBox and configured it as the primary firewall and router for the lab environment. VirtualBox NAT was used to simulate WAN connectivity, while pfSense managed the internal networks.

![PfSense](pfsense_lab1.jpg)

To simulate an attacker system, I deployed a Kali Linux virtual machine through VirtualBox.

![Kali Linux](./Screenshot%202026-06-10%20131121.png)

I also deployed a Windows virtual machine to act as the target system. DHCP services were configured through pfSense to automatically assign IP addresses, and connectivity between the systems was verified through successful ping tests.

![Kali Linux + Windows](./kalilinux_windows.jpg)

---

# Lab 1: Blocking Unauthorized Network Reconnaissance with pfSense

## Objective

Demonstrate how pfSense firewall rules can be used to prevent network reconnaissance activity originating from an attacker system.

---

## Phase 1: Reconnaissance

The first step was to perform reconnaissance against the Windows target machine using Nmap from the Kali Linux system. This scan was used to identify open ports and services available on the target host.

The scan successfully detected multiple Windows services exposed on the network.

![Screenshot](Screenshot%202026-06-24%20205141.png)

---

## Phase 2: Firewall Mitigation

After identifying the exposed services, I created a pfSense firewall rule that blocked traffic originating from the Kali Linux subnet and destined for the Windows system.

This rule demonstrates how network segmentation and firewall policies can be used to restrict communication between different security zones.

![Screenshot](Screenshot%202026-06-24%20205310.png)

---

## Phase 3: Verification

After applying the firewall rule, I repeated the Nmap scan against the Windows machine to verify that the security control was functioning as intended.

The scan was unable to successfully discover the target system, confirming that the firewall policy was preventing reconnaissance traffic from reaching the victim machine.

![Screenshot](Screenshot%202026-06-24%20205158.png)

---

## What I Learned

Through this lab, I gained hands-on experience with:

- Configuring pfSense interfaces and firewall rules
- Building and managing a segmented virtual network
- Deploying Kali Linux and Windows virtual machines
- Using Nmap for reconnaissance and service discovery
- Understanding the difference between host-based and network-based firewalls
- Verifying firewall effectiveness through testing
- Implementing network segmentation as a security control

This lab demonstrated how properly configured firewall rules can disrupt the reconnaissance phase of an attack by preventing host discovery and service enumeration between network segments.

---

