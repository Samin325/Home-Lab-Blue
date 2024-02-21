# Homelab for Security Detection & Monitoring

This homelab was created following Day CyberWox’s blueprint and documentation, available on his [website](https://cyberwoxacademy.com/building-a-cybersecurity-homelab-for-detection-monitoring/). It’s been changed slightly to use more recent software versions and technologies. 

The lab was created using VMWare Workstation Pro 17 - VMWare offers a 30-day free trial, which is what I used. 

In this lab:
- pfSense is configured to act as the firewall, router, and DHCP server
- Splunk is being used as a primary SIEM, and Security Onion has been configured to act as an IDS and secondary SIEM
- The victim network is comprised of a Windows Server domain controller with a Windows 10 machine in its Active Directory
- A Kali machine is being used as the attack box.

**Network topology:**
![image](https://github.com/Samin325/Home-Lab-Blue/assets/88060791/4ddbcad0-aab4-4b07-9721-1317100daf13)


**Samples:**

Connectivity between the Windows 10 user (Eileen) and the Domain Controller:

![image](https://github.com/Samin325/Home-Lab-Blue/assets/88060791/decc8815-7237-4505-b7ba-f2707ea9d026)

Windows 10 computer in the Active Directory Administrative Center:

![image](https://github.com/Samin325/Home-Lab-Blue/assets/88060791/03bd8d49-0442-4206-90dc-71bd32aa76cd)

Login activity logs on Splunk:

![image](https://github.com/Samin325/Home-Lab-Blue/assets/88060791/62cb0622-a513-43fd-b1ec-bd4ced7b090e)

Nmap scan from the Kali attack box:

![image](https://github.com/Samin325/Home-Lab-Blue/assets/88060791/8bf8966e-ba8b-4e57-a5d0-14f164fbe721)

pfSense dashboard and sample firewall rule:

![image](https://github.com/Samin325/Home-Lab-Blue/assets/88060791/aa744205-73a5-4466-9c7e-b02558b2e6a8)

![image](https://github.com/Samin325/Home-Lab-Blue/assets/88060791/ac8e433f-9eaa-4bec-8d6f-a4eadcfaa162)

Some Security Onion pages/tools:

![image](https://github.com/Samin325/Home-Lab-Blue/assets/88060791/3fbe8af8-a9ba-4b59-915b-20e3643574bc)

![image](https://github.com/Samin325/Home-Lab-Blue/assets/88060791/71d9a82d-d174-4c4c-88a5-aea08087fb11)

![image](https://github.com/Samin325/Home-Lab-Blue/assets/88060791/efa8dbe9-a2f3-4941-89a7-1ee223bba777)

![image](https://github.com/Samin325/Home-Lab-Blue/assets/88060791/0d9cc5db-db83-457d-9da3-ce6f70671770)

