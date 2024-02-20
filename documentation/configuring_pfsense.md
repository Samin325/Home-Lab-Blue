**Configuring pfSense as a Firewall**

To create the pfSense firewall, we first need to download the ISO file, available on their website (https://www.pfsense.org/download/)

For 64-bit machines, the following should be selected before downloading (select the nearest location to you from the ‘Mirror’ dropdown):

![image](https://github.com/Samin325/Home-Lab-Blue/assets/88060791/1cf10d3a-2d3b-4819-9c3b-dff62cdd8c8b)

Extracting the downloaded file using the Windows Extractor gave an error, so I used 7zip instead

Open up VMWare and click “Create a New Virtual Machine” - ensure the “Typical” is selected before clicking “Next”:

![image](https://github.com/Samin325/Home-Lab-Blue/assets/88060791/99d6bdea-3c57-4cc6-b2e8-4a12c82b66c7)

Select the ISO file by clicking “Browse” and browsing to where the file is located before clicking “Next”:

![image](https://github.com/Samin325/Home-Lab-Blue/assets/88060791/3032189f-5f33-4ee2-85cd-aa5ad20196b4)

Give your virtual machine a name and a location before clicking next:

![image](https://github.com/Samin325/Home-Lab-Blue/assets/88060791/a453665b-ab64-4c0a-a0fb-195b818f1a89)

Keep the preselected options and click “Next”:

![image](https://github.com/Samin325/Home-Lab-Blue/assets/88060791/07390a08-c6f1-4efe-a130-95a8a8b07092)

On the next screen, click “Customize Hardware” and give it around 2GB RAM.

![image](https://github.com/Samin325/Home-Lab-Blue/assets/88060791/c2d03363-9e4a-44ae-873e-4d21fd72bdc7)

![image](https://github.com/Samin325/Home-Lab-Blue/assets/88060791/ffc029a4-3916-472e-882b-6b11e90291fd)

Add a network adapter by clicking “Add”, selecting “Network Adapter” and clicking “Finish”:

![image](https://github.com/Samin325/Home-Lab-Blue/assets/88060791/76982bc7-d8ea-40be-a06f-ba1bf76e4cfc)

Repeat this 4 more times so that you have 6 network adapters total:

![image](https://github.com/Samin325/Home-Lab-Blue/assets/88060791/42ce5af8-98bf-4a8b-a1c1-33a01142088d)

For each of the Network adapters, click on them and choose the custom network connection of “VMnetX” where “X” is the network adapter number (eg. for “Network Adapter 5”, choose “VMnet5”, as shown below). Leave the original Network adapter (the one with no number) as NAT:

![image](https://github.com/Samin325/Home-Lab-Blue/assets/88060791/e0bbe490-2a66-4a9c-9467-ad1d6e82dc16)

You can remove the “Sound Card” and “USB Controller” if you wish. Otherwise, you can click “Close” and then “Finish”:

![image](https://github.com/Samin325/Home-Lab-Blue/assets/88060791/d4df171d-da78-4f0d-a4ea-86f80af6fda1)

The pfSense machine should launch. Except for the default partition option, where you should select "Auto (UFS) BIOS” from the list, you can press “Enter” through each screen to select the default for the rest of the options. Any warnings about overwriting disk content permanently can be safely disregarded.

Once you reboot the machine and are prompted with “Enter an option”, enter “1”:

![image](https://github.com/Samin325/Home-Lab-Blue/assets/88060791/9ff6ad30-27bf-438b-86f5-8ac5098f366f)

Enter “n” at the next prompt when it asks about setting up VLANs:

![image](https://github.com/Samin325/Home-Lab-Blue/assets/88060791/3c04bab6-7566-4f2d-b3c7-39a6e3d303e9)

Enter each of the “emX” at the subsequent prompts (ie. em0, em1, …, em5):

![image](https://github.com/Samin325/Home-Lab-Blue/assets/88060791/7a0e43eb-bb51-4947-84f2-a99175d31c8b)

![image](https://github.com/Samin325/Home-Lab-Blue/assets/88060791/54fa8575-ff82-49df-80ba-fe2af3d409d0)

Enter “y” at the prompt asking if you want to proceed.

Next, to set the interface IP addresses, enter “2” at the prompt:

![image](https://github.com/Samin325/Home-Lab-Blue/assets/88060791/388bcac3-d46f-4d51-9e5a-c961e2378d99)

To configure the LAN, enter the associated number (in the screenshot below, it's ‘2’) and enter  ‘n’ when asked about configuring the IPv4 address via DHCP. Enter the IP address that is going to be used to access the pfSense WebGUI (in this case, we are using 192.168.1.1): 

![image](https://github.com/Samin325/Home-Lab-Blue/assets/88060791/09358fe0-26cb-45bc-8ffd-e1323e94d2f4)

Configure as follows (the start and end addresses are 192.168.1.11 - 192.168.1.200):

![image](https://github.com/Samin325/Home-Lab-Blue/assets/88060791/05d0a583-f13c-445b-b6a8-dc633860c515)

Press “Enter” at the next prompt to continue.

Configure each of the remaining interfaces as follows. OPT1:

![image](https://github.com/Samin325/Home-Lab-Blue/assets/88060791/d44fc8fe-9eb1-4ced-b9f0-ddff249929ec)

![image](https://github.com/Samin325/Home-Lab-Blue/assets/88060791/785c401d-1f8b-43b6-8b71-f719c012051f)

OPT2:

![image](https://github.com/Samin325/Home-Lab-Blue/assets/88060791/0fc6e784-1b71-48ee-8e35-78c0d87c49c4)

![image](https://github.com/Samin325/Home-Lab-Blue/assets/88060791/08bba8c6-60b5-4883-866f-88d08804f8d0)

OPT4: (note that we are not touching OPT3 for now)

![image](https://github.com/Samin325/Home-Lab-Blue/assets/88060791/33efc9b4-ad6a-4909-9f96-a83168c5c803)

![image](https://github.com/Samin325/Home-Lab-Blue/assets/88060791/6d6ba10f-5f36-4902-a5f0-347c7d930854)

This is what it should look like at the end:

![image](https://github.com/Samin325/Home-Lab-Blue/assets/88060791/10ce5e51-bdfa-4c7e-b904-ac2ceca83779)
