**Configuring Windows 10 Desktop**

Log into the Kali machine and navigate to the pfSense website

Under the victim network in Services - DHCP Server, add “192.168.2.10” to the DNS servers and the domain name created for the Windows Server to the “Domain Name” field:

![image](https://github.com/Samin325/Home-Lab-Blue/assets/88060791/56034005-01c6-45db-a308-952d6e539b23)

Save and apply the changes

Now, create a new virtual machine using the Windows 10 ISO file downloaded from their website (https://www.microsoft.com/en-us/evalcenter/download-windows-10-enterprise)

Using this ISO file, configure a new virtual machine, similar to the Windows Server machine configured earlier. Ensure that the Network Adapter is changed to Vmnet3 and “Power on this virtual machine after creation” is unchecked:

![image](https://github.com/Samin325/Home-Lab-Blue/assets/88060791/ac81695f-1d31-4c1b-a016-38f7cb0de300)

Click “Finish”, and before powering on the machine edit the settings again to remove the Floppy drive:

![image](https://github.com/Samin325/Home-Lab-Blue/assets/88060791/8da2c869-4232-4ad3-a559-d53d0b15f00d)

Configure as you wish once starting the machine up. Once you get to the following screen, select “Custom”:

![image](https://github.com/Samin325/Home-Lab-Blue/assets/88060791/ec4f35c6-a52f-4e2a-8a4c-3f7642a7b0aa)

Click “Next” on the following screen:

![image](https://github.com/Samin325/Home-Lab-Blue/assets/88060791/66893bc4-2483-4157-b0b3-aa406db6443a)

Continue configuring as you wish. Once you get to the following screen, select “I don’t have internet”:

![image](https://github.com/Samin325/Home-Lab-Blue/assets/88060791/7fc16a6a-9631-49d8-8c8d-ad9d1ebacb80)

Select “Continue with limited setup”:

![image](https://github.com/Samin325/Home-Lab-Blue/assets/88060791/1879f18b-dde5-4bf0-88df-3395e6714309)

Set a name and password:

![image](https://github.com/Samin325/Home-Lab-Blue/assets/88060791/46bbac49-fbc3-47f9-963a-197d1f264002)

You can set the security questions to be whatever you want. For the rest of the configurations, select “No” whenever it is the option and don’t share the optional data.

Once you can log in, change the name of the machine so it reflects the ‘user’ that will be using it; you can do this by searching for “PC name” in the Windows search bar and changing it. You will need to restart the machine so that the change is applied.

After logging in again, open up the network and internet settings from the bottom right-hand corner:

![image](https://github.com/Samin325/Home-Lab-Blue/assets/88060791/41ec8ceb-372d-44ae-b7ad-e8080cbfc83b)

Press “Change adapter options” and then right-click the Ethernet network and click “Properties”:

![image](https://github.com/Samin325/Home-Lab-Blue/assets/88060791/53fec914-5b2d-4026-a47d-484327619c74)

Click on the IPv4 line and configure as follows:

![image](https://github.com/Samin325/Home-Lab-Blue/assets/88060791/7fafdc13-e3c2-4c30-ad77-a474b2f5bc0f)

Click “OK” to exit out of the pop-ups and close everything else opened

Search for “Access work or school” in the Windows search box and click “Connect” once it’s opened up.

Select “Join this device to local Active Directory Domain”:

![image](https://github.com/Samin325/Home-Lab-Blue/assets/88060791/2d50bf36-7416-4c93-a2a8-ae33ef3ee2ab)

Enter the domain name; ensure that the pfSense machine and Windows Server machines are both running to avoid the error below:

![image](https://github.com/Samin325/Home-Lab-Blue/assets/88060791/5bcddf86-57d0-406b-a5d8-228d7e0263c2)

![image](https://github.com/Samin325/Home-Lab-Blue/assets/88060791/93f8ca5a-2d82-44a4-92da-40c84aa7fa4b)

Click “Skip” and then restart the device when prompted

If you check on the Windows server machine, this computer will now appear in the Active Directory computers:

![image](https://github.com/Samin325/Home-Lab-Blue/assets/88060791/1aa52e88-bfbe-4847-b26f-a68676a6bc4e)
