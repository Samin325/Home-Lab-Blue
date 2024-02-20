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
