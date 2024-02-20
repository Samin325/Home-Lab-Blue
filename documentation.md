**Homelab for Security Detection & Monitoring**

This is a homelab created following Day CyberWox’s blueprint and documentation, available on his website (https://cyberwoxacademy.com/building-a-cybersecurity-homelab-for-detection-monitoring/). It’s been changed slightly to use the more recent, up-to-date software versions and technologies. The lab was created using VMWare Workstation Pro 17; you don’t need to buy a licence upfront since VMWare offers a 30-day free trial, which is what I will be using. 

**Contents:**
Configuring pfSense as a Firewall
Configuring Security Onion
Configure the Security Onion Analyst Machine
Configuring Kali as the Attack Box
Configuring pfSense Interface and Firewall Rules
Configuring Windows Server as a Domain Controller
Configuring Windows 10 Desktop
Configuring Splunk
Configuring a Universal Forwarder on a Windows Server

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

**Configuring Security Onion**

Security Onion will be acting as the IDS and Log Management solution.

Download the security onion iso from the Github repo (https://github.com/Security-Onion-Solutions/securityonion/blob/master/VERIFY_ISO.md)

![image](https://github.com/Samin325/Home-Lab-Blue/assets/88060791/a416a3a9-69a8-4c2d-90e9-04c55977d60b)

Set up a new virtual machine in VMWare as done above (with pfSense) with “Typical” selected on the first screen, and then select the disc image from where you downloaded it. When it asks to select a guest operating system, use the configuration below:

![image](https://github.com/Samin325/Home-Lab-Blue/assets/88060791/025437c4-b08c-4fe2-b88d-2a82ddb7aefb)

After clicking “Next”, use the following configuration for the next screen (give the machine at least 200 GB, the more the better):

![image](https://github.com/Samin325/Home-Lab-Blue/assets/88060791/50fdc677-7ff0-437f-8105-4bdb5d641cf0)

On the next screen, click “Customize Hardware” and give it more RAM - they recommend 12 GB, but I’ll be giving it 8. Also, give it at least 4 processors and create 2 new network adapters:

![image](https://github.com/Samin325/Home-Lab-Blue/assets/88060791/67d905d6-0b81-4111-8bd5-893ffe94ff12)

Configure Network adapter 2 to VMnet 4, and Network adapter 3 to VMnet 5. You can delete extra pieces like the Sound Card or USB Controller. The final screen looks like this:

![image](https://github.com/Samin325/Home-Lab-Blue/assets/88060791/d5567250-ce3b-4ee7-abe7-071c423d0eb0)

You can click “Close” and then “Finish” before powering on the VM.
Once turned on, let the VM load through everything and then enter “yes” when prompted. Enter a username and password as prompted as well.

![image](https://github.com/Samin325/Home-Lab-Blue/assets/88060791/1dc079e8-9523-4ee6-8f61-30c878f81006)

After entering and waiting, press enter when prompted. Enter your login information once you get to the prompt asking you for it. 

Select “Yes” by pressing enter on the next screen:

![image](https://github.com/Samin325/Home-Lab-Blue/assets/88060791/159022e4-4cbe-45a0-92e4-f8d9b58c7bbf)

Press enter on the “Install” option on the next screen:

![image](https://github.com/Samin325/Home-Lab-Blue/assets/88060791/33709128-5190-4547-b8f0-d61f2dedda2a)

Ensure the “EVAL” option is selected before pressing enter on the screen after:

![image](https://github.com/Samin325/Home-Lab-Blue/assets/88060791/49ee0cac-139f-40d7-8fdc-1b5223975409)

Type out “AGREE” when prompted. Select “Standard” on the next screen:

![image](https://github.com/Samin325/Home-Lab-Blue/assets/88060791/fadcbe83-7745-4ae4-96c2-9c9eb6e6deb3)

Create a hostname when asked. Select “ens33” on the next screen:

![image](https://github.com/Samin325/Home-Lab-Blue/assets/88060791/10321aac-43ac-436e-bc0b-fc5a8bda7610)

Select “DHCP” on the next screen:

![image](https://github.com/Samin325/Home-Lab-Blue/assets/88060791/e6553f94-db5d-4c9d-879a-5ade989f4b0e)

Select “YES”, “OK”, and then “Direct” for the next 3 prompts. Then select “ens35” at the next prompt:

![image](https://github.com/Samin325/Home-Lab-Blue/assets/88060791/33bfabb7-2a25-4cd4-a5ed-03d9dfce3c9a)

Select “Automatic” on the next screen. Select the default options for the next couple of screens before reaching the prompt asking for an email. Enter an email and password of your choosing.

Select “IP” at the next screen:

![image](https://github.com/Samin325/Home-Lab-Blue/assets/88060791/85b0c295-3020-4fe5-9221-79c224ea4ce3)

Select “Yes” for the NTP server on the next screen and then select all the default options.

When you get to the final screen, save the information displayed; importantly, ensure you know the IP address for web access (next to “Access URL”). Press “Tab” and select “Yes” once you are done. The installation will begin, and it will likely take a long time (it took around 20 minutes for me).

**Configure the Security Onion Analyst Machine**

Here we will be configuring an Ubuntu machine that will be used to access the Security Onion web interface, simulating how a SOC Analyst would access a SIEM.

First, we download the Ubuntu Desktop image from their website (https://ubuntu.com/download/desktop)

![image](https://github.com/Samin325/Home-Lab-Blue/assets/88060791/c4876856-f441-4458-8969-5b889aa6b6bf)

On VMware, create a new virtual machine with typical selected before clicking “Next”:

![image](https://github.com/Samin325/Home-Lab-Blue/assets/88060791/562a6908-123c-496e-b3dd-28561ea0007a)

Select the disk image from where you downloaded it before clicking “Next”:

![image](https://github.com/Samin325/Home-Lab-Blue/assets/88060791/2260da9c-25a1-48b6-899f-88dc610f063f)

Fill in the fields as you choose, then click “Next”:

![image](https://github.com/Samin325/Home-Lab-Blue/assets/88060791/5aff35a8-09f7-4d59-b50f-a4956d39e888)

Give the machine a name and choose the location to store it before clicking “Next”:

![image](https://github.com/Samin325/Home-Lab-Blue/assets/88060791/f421c103-a89c-4c7c-a3c4-41b88e82f716)

The next two screens you can leave at the defaults:

![image](https://github.com/Samin325/Home-Lab-Blue/assets/88060791/60be49c7-e6a3-4d75-976b-3e87274ad2a6)

![image](https://github.com/Samin325/Home-Lab-Blue/assets/88060791/c9766ea8-a629-43e0-9d5f-455a43ca5722)

Load up the virtual machine and configure it as you wish; for this lab, all the default options were used (ignore any warnings about overwriting the defaults). Once you are able to log into the machine, open up a terminal and enter “sudo apt install net-tools”:

![image](https://github.com/Samin325/Home-Lab-Blue/assets/88060791/da267f29-4da7-4b6a-adec-b1ec3a4cd5b6)

Run “ifconfig” next and then note the following IP address:

![image](https://github.com/Samin325/Home-Lab-Blue/assets/88060791/84c977df-c9d3-453b-8308-bc2db7becd0a)

Now, log into the Sec Onion machine and enter “sudo so-allow”, then enter “a”:

![image](https://github.com/Samin325/Home-Lab-Blue/assets/88060791/5112e5a9-b4a5-4091-bc48-45e1027fed33)

When prompted, enter in the the IP address of the Ubuntu Desktop noted above (this will allow traffic from your Ubuntu machine through to the Security Onion web instance).

Now navigate to the access URL of the Security Onion machine noted previously from the Ubuntu Desktop. You will be warned about a potential security risk, but you can ignore that and continue to the login page where you will be prompted to login with the email and password you defined earlier on:

![image](https://github.com/Samin325/Home-Lab-Blue/assets/88060791/6edb9483-351c-4f3d-8a2c-ecc4bf875224)

![image](https://github.com/Samin325/Home-Lab-Blue/assets/88060791/3fbe8af8-a9ba-4b59-915b-20e3643574bc)

From here, you navigate between the tabs on the left side to see the “Alerts”, “Dashboards”, and “Hunt” pages, among others; tools like Kibana and Grafana can also be opened from this sidebar (you may be prompted to log in with your email again when opening up tools like Kibana):

![image](https://github.com/Samin325/Home-Lab-Blue/assets/88060791/71d9a82d-d174-4c4c-88a5-aea08087fb11)

![image](https://github.com/Samin325/Home-Lab-Blue/assets/88060791/efa8dbe9-a2f3-4941-89a7-1ee223bba777)

![image](https://github.com/Samin325/Home-Lab-Blue/assets/88060791/0d9cc5db-db83-457d-9da3-ce6f70671770)

**Configuring Kali as the Attack Box**

First, we will need to download the Kali image, which can be found on their website (https://www.kali.org/get-kali/#kali-virtual-machines). For this lab, we will be downloading the VMware 64 bit version:

![image](https://github.com/Samin325/Home-Lab-Blue/assets/88060791/b495b9ac-503a-49c0-af26-477a451297eb)

Once downloaded, extract the file to where you would like it to be, and then search for the file ending in .vmx (alternatively, look for the “VMware virtual machine configuration” file) and open it. It should open up the machine in VMware

![image](https://github.com/Samin325/Home-Lab-Blue/assets/88060791/320e6201-5192-4bcd-b801-1411f94e4769)

Edit the virtual machine settings to add another Network Adapter and map it to VMnet2:

![image](https://github.com/Samin325/Home-Lab-Blue/assets/88060791/9d5c82c1-698a-4ba0-a122-84180422b023)

You can now boot up the machine and log in with the default credentials (username and password are both “kali”)

You can change the password by running “passwd” on the terminal, where you will be prompted to enter the current password (“kali”) before you set the new password:

![image](https://github.com/Samin325/Home-Lab-Blue/assets/88060791/9b819a4d-3780-4d8c-82b2-575f347c9f71)

**Configuring pfSense Interface and Firewall Rules**

Log into the Kali machine and open up a web browser and navigate to 192.168.1.1. You will be warned about potential security risks, but you can accept and continue:

![image](https://github.com/Samin325/Home-Lab-Blue/assets/88060791/934fea93-619b-45b6-ab05-2ce7dba3991a)

Login with the default credentials (“admin” and “pfsense” as username and password):

![image](https://github.com/Samin325/Home-Lab-Blue/assets/88060791/676723e6-6c56-4594-ac23-a40d53d5bc3c)

Click “Next” on the first two screens:

![image](https://github.com/Samin325/Home-Lab-Blue/assets/88060791/829b7445-b7a1-42ab-b248-62b6bb7d3db4)

![image](https://github.com/Samin325/Home-Lab-Blue/assets/88060791/09e4ead0-956b-4c0f-af1c-1bf86c3956e6)

Enter “8.8.8.8” as the primary DNS server and “4.4.4.4” as the secondary before clicking “Next”:

![image](https://github.com/Samin325/Home-Lab-Blue/assets/88060791/e0d89270-57ef-4267-8baa-ddbeacef9898)

Select your timezone on the next screen and click “Next”:

![image](https://github.com/Samin325/Home-Lab-Blue/assets/88060791/63ab0fd0-197f-4434-b32b-cabe256688ac)

On the next screen, you can leave all the default selections. If you choose, you can unselect the two checkboxes at the bottom of the screen to see more alerts generated later on:

![image](https://github.com/Samin325/Home-Lab-Blue/assets/88060791/dfffdca6-7016-4b0c-aabb-47f4298e230b)

The next screen you should just click “Next”:

![image](https://github.com/Samin325/Home-Lab-Blue/assets/88060791/3e34827e-584c-4d08-95af-d686d70ef511)

On the next screen, set a password before clicking “Next”:

![image](https://github.com/Samin325/Home-Lab-Blue/assets/88060791/a39e8805-dbf3-4ad0-ab16-ada8ecb0255b)

On the next screen, click “Reload” and it will reload pfSense with the new changes. You can then hit “Finish” when you are able to:

![image](https://github.com/Samin325/Home-Lab-Blue/assets/88060791/eb408beb-9989-4628-8bcc-40b0b04f9f98)

You can change to dark mode by selecting “General Setup” under “System” in the navigation bar at the top and changing the theme to pfSense-dark:

![image](https://github.com/Samin325/Home-Lab-Blue/assets/88060791/e8d6729e-ba28-4395-b20a-69f5699fa3ea)

Under the “Intefaces” dropdown, select “Lan”:

![image](https://github.com/Samin325/Home-Lab-Blue/assets/88060791/07ff6dd2-1e08-46c4-9313-3170cc047743)

This will be the Kali interface, so give it a description and hit “Apply Changes”:

![image](https://github.com/Samin325/Home-Lab-Blue/assets/88060791/f2b30f7e-c78a-4f60-8c12-e5a2aa171205)

Similarly, make the descriptions more descriptive for the remainder of the interfaces:
OPT1 will be for the victim network
OPT2 will be for Security Onion
OPT3 will be for the span port
OPT4 will be for Splunk
Make sure to check that “Enable interface” is checked for all of them, particularly OPT3. After you apply all changes, you should see the changes reflected under interface assignments:

![image](https://github.com/Samin325/Home-Lab-Blue/assets/88060791/8db0e89a-ea21-4796-992a-4b1b62337432)

Enter the “Bridges” tab in the secondary navbar and click “Add”:

![image](https://github.com/Samin325/Home-Lab-Blue/assets/88060791/5919d530-1d19-4c03-b66a-6310acadf479)

Select the victim network as the Member Interface and click “Display Advanced” so you can select the span port as the Span port:

![image](https://github.com/Samin325/Home-Lab-Blue/assets/88060791/6b53c9b7-9a57-4ac5-84e1-3d604b5deaaf)

Press “Save” at the bottom of the screen after scrolling down:

![image](https://github.com/Samin325/Home-Lab-Blue/assets/88060791/aee537d7-8ac1-4be8-8a2f-954d162f97f3)

Create a rule for the firewall under “Rules” in the “Firewall” dropdown from the main navbar (ensure that the “Wan” tab is selected) by pressing the “Add” with a downwards facing arrow:

![image](https://github.com/Samin325/Home-Lab-Blue/assets/88060791/04bccd6d-4f61-4572-a027-0106c44d56bc)

Change the protocol to “Any” and press save (this will allow for more alerts and logs to be generated). Click “Apply Changes” when brought back to the overview screen:

![image](https://github.com/Samin325/Home-Lab-Blue/assets/88060791/6048d80d-6698-4282-92b4-9056bf878135)

![image](https://github.com/Samin325/Home-Lab-Blue/assets/88060791/a234bbf1-f552-48df-95b9-6157b34c883f)

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
















































