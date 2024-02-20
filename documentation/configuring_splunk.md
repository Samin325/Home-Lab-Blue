**Configuring Splunk**

Download the Ubuntu server ISO: https://ubuntu.com/download/server

![image](https://github.com/Samin325/Home-Lab-Blue/assets/88060791/d2688bdb-05af-492a-a793-f51e891430b6)

![image](https://github.com/Samin325/Home-Lab-Blue/assets/88060791/db63f1c8-e610-4a40-bf84-85ff453014e3)

Try and install ubuntu

Press “Enter” while having “Done” highlighted and select all the default selections until you are asked for a name and password

Fill in the fields as you wish

![image](https://github.com/Samin325/Home-Lab-Blue/assets/88060791/fdeddbd3-3a30-4adb-b97c-6f28283e10d2)

Press “Enter” to select the “Install OpenSSH server” option before moving on by selecting “Done”:

![image](https://github.com/Samin325/Home-Lab-Blue/assets/88060791/8908de78-c893-4707-aa0a-beba711f186e)

Keep the default selections for the next screens and then wait for the install to finish:

![image](https://github.com/Samin325/Home-Lab-Blue/assets/88060791/a3173e8d-315c-42f5-8f42-0f16322985b6)

Once you are able, reboot the machine and log in:

![image](https://github.com/Samin325/Home-Lab-Blue/assets/88060791/b101b8d9-256e-40c5-974a-88852eba2ba9)

Run the command “sudo apt install ubuntu-desktop” to get a GUI

![image](https://github.com/Samin325/Home-Lab-Blue/assets/88060791/50b4a0d7-e106-430f-bb50-559e2a68e8df)

![image](https://github.com/Samin325/Home-Lab-Blue/assets/88060791/0f850cfa-b057-4053-b684-f42b02b344d9)

![image](https://github.com/Samin325/Home-Lab-Blue/assets/88060791/4ae00782-b3a4-476b-86cb-69d3c83547b0)

Once the machine is rebooted, open up Firefox and log into the Splunk website (https://www.splunk.com/); if you do not have an account, create one account.
 
Click “Get My Free Trial” of Splunk Enterprise and download the linux .tgz file:

![image](https://github.com/Samin325/Home-Lab-Blue/assets/88060791/86b22475-0c3e-4fec-b70f-65d37c523e76)

![image](https://github.com/Samin325/Home-Lab-Blue/assets/88060791/b8f0ba53-5e8e-42b1-9c43-6a87bfcd32b8)

Open up a terminal and unzip the file:

![image](https://github.com/Samin325/Home-Lab-Blue/assets/88060791/3b1cfa88-abf6-4526-9dca-d108254cbe68)

Move to the splunk/bin directory and run “./splunk start” 

Agree with the license and set a username and password

![image](https://github.com/Samin325/Home-Lab-Blue/assets/88060791/9b143737-0d3d-49c9-b288-cd7d94a35124)

![image](https://github.com/Samin325/Home-Lab-Blue/assets/88060791/4ee0f100-b89e-46cc-9c55-6433675d5d6d)

![image](https://github.com/Samin325/Home-Lab-Blue/assets/88060791/c68eaa7e-007a-4d5e-8346-dcac776b6210)

You can now log in at “http://splunk:8000”

![image](https://github.com/Samin325/Home-Lab-Blue/assets/88060791/47ec0d5e-542f-40c7-bcd8-97490a471f2c)

![image](https://github.com/Samin325/Home-Lab-Blue/assets/88060791/38021b0f-7803-4c7f-a127-217ff91edce1)
