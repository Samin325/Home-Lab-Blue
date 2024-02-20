
**Configuring Windows Server as a Domain Controller**

Download the ISO image from their website (https://info.microsoft.com/ww-landing-windows-server-2019.html)  - it doesn’t matter what you fill the form in with:

![image](https://github.com/Samin325/Home-Lab-Blue/assets/88060791/1ab65207-418c-40cc-b9c5-1a339d38714c)

![image](https://github.com/Samin325/Home-Lab-Blue/assets/88060791/002245be-68d6-4eaa-8b94-44823685fa32)

Create a new virtual machine with “Typical” configuration and select the iso file from where you downloaded it.

The next screen where you are asked for a product key you can ignore and continue:

![image](https://github.com/Samin325/Home-Lab-Blue/assets/88060791/7043bcd7-4960-4c4b-b4f6-e31ae0f05622)

You can give the machine a name and choose the location to store it next:

![image](https://github.com/Samin325/Home-Lab-Blue/assets/88060791/832c5a24-5e24-43ac-beb2-9248262bb9fe)

You can keep the default selections for the disk:

![image](https://github.com/Samin325/Home-Lab-Blue/assets/88060791/b1994db0-266c-4a0d-b823-0812233da524)

Uncheck the checkbox for powering on after completion, and customize the hardware to make the network adapter map to VMnet3:

![image](https://github.com/Samin325/Home-Lab-Blue/assets/88060791/58bac71e-dc4f-470b-b497-7caf5a40bb18)

Remove the floppy drive:

![image](https://github.com/Samin325/Home-Lab-Blue/assets/88060791/fc329404-fc88-4f61-b903-ff13df914b91)

Power the machine on and press a key very quickly (otherwise it will time out). Click “Next” and then “Install Now”. 

Select “Windows Server 2019 standard Evaluation (Desktop Experience)” before clicking “Next” and accepting the terms:

![image](https://github.com/Samin325/Home-Lab-Blue/assets/88060791/2ca8b1e3-86c7-413f-bf6d-b3323402d783)

![image](https://github.com/Samin325/Home-Lab-Blue/assets/88060791/09409d33-b52a-4685-b070-45bd1a87369d)

Click “New”, then “Apply”, and then “Ok” before clicking “Next”:

![image](https://github.com/Samin325/Home-Lab-Blue/assets/88060791/d07deedd-a620-46fb-ade7-520c0a6abd5c)

Once it finishes installing, create a password (does not need to be secure, since this is a lab environment):

![image](https://github.com/Samin325/Home-Lab-Blue/assets/88060791/1a3e1a6f-23ff-4abe-b44e-19ce31b78f67)

To log in, send CTRL-ALT-DELETE to the machine:

![image](https://github.com/Samin325/Home-Lab-Blue/assets/88060791/7ced14ea-cc9f-4ae8-b74f-c1c85249acce)

Once the Server Manager Dashboard loads up, Click “Add Roles and Features” under “Manage” 

Click “Next” until you get to the following screen, where you can check the “Active Directory Domain Services” and then click “Add Features“:

![image](https://github.com/Samin325/Home-Lab-Blue/assets/88060791/1d5f4496-605c-461e-9437-c4f12a1afd47)

Continue clicking “Next” until you can click the “Install” button:

![image](https://github.com/Samin325/Home-Lab-Blue/assets/88060791/df0d6354-55df-4f2c-b85f-0957619d1b8f)

Once it appears, click the flag icon with the yellow marker and click “Promote this server to a domain controller“

![image](https://github.com/Samin325/Home-Lab-Blue/assets/88060791/d8f5b69f-f9aa-48e9-966c-705cc1793761)

Click “ Add a new forest” and specify a domain name before clicking “Next”:

![image](https://github.com/Samin325/Home-Lab-Blue/assets/88060791/55d42f35-6fb7-475d-8962-7183ac5fcb5d)

Set a password:

![image](https://github.com/Samin325/Home-Lab-Blue/assets/88060791/22e64131-40a5-4c8b-b370-2df3f6a04086)

Click “Next” until you can click “Install”:

![image](https://github.com/Samin325/Home-Lab-Blue/assets/88060791/4830432e-75f2-4ea9-99fa-c5ca4b982094)

Click “Install”, then wait for the machine to reboot and log back in. 

Once logged in, click “Add Roles and Features” under “Manage”

Click “Next” until you get to the screen below. Here, check off “Active Directory Certificate Services” and click “Add Features” before clicking “Next”:

![image](https://github.com/Samin325/Home-Lab-Blue/assets/88060791/75e5d7c1-ec89-4b20-a8c7-d6593a922ac3)

Click “Next” until you reach the screen with the install button. Here, check the box that says “Restart the destination server automatically if required” and click “Yes” before pressing the “Install” button:

![image](https://github.com/Samin325/Home-Lab-Blue/assets/88060791/9a908842-ba9b-4115-86f0-f37c67cc6739)

Click on the flag with the yellow triangle and click “Configure Active Directory Certificate Services on the destination server“:

![image](https://github.com/Samin325/Home-Lab-Blue/assets/88060791/bfadda5d-1cb2-4fa9-9973-d13ff91712af)

Enter your credentials before clicking next:

![image](https://github.com/Samin325/Home-Lab-Blue/assets/88060791/fac93f9b-0778-4f01-924c-d0204e4a0e49)

![image](https://github.com/Samin325/Home-Lab-Blue/assets/88060791/07de43be-deff-42d4-a62c-fa38ccdd788a)

Check “Certification Authority”:

![image](https://github.com/Samin325/Home-Lab-Blue/assets/88060791/38d39c84-48ac-4dfc-949b-c7547fd63bcf)

Hit “Next” until you are able to click “Configure”:

![image](https://github.com/Samin325/Home-Lab-Blue/assets/88060791/897ae37b-a80e-4a46-8853-a15272b52596)

Once done, manually restart the machine if it did not do so automatically.

To add users, click “Active Directory Users and Computers” under “Tools”

Click the local domain and right click on the “Users” file and click “User” under “New”:

![image](https://github.com/Samin325/Home-Lab-Blue/assets/88060791/98791850-ea81-42d8-828b-461d2da6af70)

Create the user, ensuring to uncheck the changing password option and check the “Password never expires” option:

![image](https://github.com/Samin325/Home-Lab-Blue/assets/88060791/5a3863ea-1181-4935-a032-9e92a2e82c2a)

![image](https://github.com/Samin325/Home-Lab-Blue/assets/88060791/9fb07eb1-b9ef-45f4-9a33-0e7c5264c1fa)

![image](https://github.com/Samin325/Home-Lab-Blue/assets/88060791/879b9a2a-e510-4cad-8867-50204488f817)

After clicking finish and adding the user, search up Windows Defender Firewall on Windows and turn them all off:

![image](https://github.com/Samin325/Home-Lab-Blue/assets/88060791/15f77c88-fb6c-498f-8309-6229c232a371)

Now, open up Control Panel and navigate to “Network Connections” under “Network and Internet” before right-clicking on the Ethernet connection and selecting “Properties”:

![image](https://github.com/Samin325/Home-Lab-Blue/assets/88060791/123fa0e9-6fb0-4647-948c-8ea6c4ec7942)

Click on the IPv4 line and enter the following configurations:

![image](https://github.com/Samin325/Home-Lab-Blue/assets/88060791/10fef409-969d-4051-99f8-a3fb1c38bf42)
