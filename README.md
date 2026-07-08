# virtual-network-security-lab-setup
Goal: After receiving my Network+ and Security+ certifications, I want to learn more hands on experience as im still in school. Configuring this virtualized network and running labs will allow me to gain more knowledge on certain commands and tools commonly used in Cybersecurity/network configuratin. 

Virtual Cybersecurity lab using a physical cisco switch + labs hosted on a windows pc

Step 1: Confiure the Virtual Environment

To begin, I set up a physical network using a Cisco Catalyst switch and a Windows Desktop PC. I connected the switch to my home router for internet access, then directly connected my desktop to the switch itself.:![Switch Configuration](IMG_7419.jpeg)
I used a console cable to configure the name and of the switch and common security practices like a secret password, then I configured SSH so I can use an out of band managment way to configure the switch from now on.![SSH Configuration](IMG_7423.jpeg)
Then, I confirmed connectivity by pinging the switch from my PC, and reading the arp table from my pc to ensure it has the switches MAC learned. ![Connectivity](IMG_7421.jpeg)
For now I will keep the switch seperate until I add on another NIC to my pc to allow the pfSense router im going to configure in virtualbox act as if it was on my actual network. 
I downloaded and setup a virtual pfSense version and configured it, with virtualbox being simulated for the WAN, then pfSense as the firewall/router, then the LAN, which is  where I will place future VMs.  ![PfSense](pfsense_lab1.jpg)
Acting as the "threat actor machine" will be a kali linux machine I set up through VirtualBox. ![Kali Linux](./Screenshot%202026-06-10%20131121.png)
I added a windowws machine to be the victim in the lab and configured DHCP through pfsense to give both devices IP addresses and confirmed connectivity through ping ![Kali Linux + Windows](./kalilinux_windows.jpg)

Lab #1: Blocking Unauthorized Network Reconnaissance with pfSense firewall
Goal: Using pfSense to demonstrate how firewall rules can prevent an attacker from performing active reconnaissance against a windows workstation. 

First I performed reconnaissance by directing an nmap scan to the victim machine to see which ports are open:![Screenshot](Screenshot%202026-06-24%20205141.png)


After the traffic was allowed through pfSense I made a rule stating that all traffic from that subnet is to be blocked, which includes the Kali Linux machine: ![Screenshot](Screenshot%202026-06-24%20205310.png)



Then, I attemped the nmap scan again after placing those rules: ![Screenshot](Screenshot%202026-06-24%20205158.png)

What I learned: 
In ths lab, I learned how to configure pfSense rules using it as a network firewall to segment traffic that flowed btween the Kali Linux and Windows virtual machines. I also learned how host based firewalls can differ from network based, as I had to disable the windows defender prior to this so I can use the pfSense firwall as the main firewall. 


