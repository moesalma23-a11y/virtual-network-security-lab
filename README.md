# virtual-network-security-lab-setup

Virtual Cybersecurity lab using a physical cisco switch + labs hosted on a windows pc
To begin, I set up a physical network using a Cisco Catalyst switch and a Windows Desktop PC. I connected the switch to my home router for internet access, then directly connected my desktop to the switch itself.:![Switch Configuration](IMG_7419.jpeg)
I used a console cable to configure the name and of the switch and common security practices like a secret password, then I configured SSH so I can use an out of band managment way to configure the switch from now on.![SSH Configuration](IMG_7423.jpeg)
Then, I confirmed connectivity by pinging the switch from my PC, and reading the arp table from my pc to ensure it has the switchs MAC learned. ![Connectivity](IMG_7421.jpeg)
I downloaded and setup a virtual pfSense version and configured it, with virtualbox being simulated for the WAN, then pfSense as the firewall, then the LAN, which is  where I will place future VMs.  ![PfSense](pfsense_lab1.jpg)
Acting has the "threat actor machine" will be a kali linux machine I set up through VirtualBox. 
