![image](https://github.com/Samin325/Home-Lab-Blue/assets/88060791/8901a2cf-7bb0-4209-8ba6-81b23d458152)**Configuring a Universal Forwarder on a Windows Server**

Navigate to http://splunk:8000 on the Ubuntu server and go to 
Settings >> Forwarding and Receiving >> Add new

![image](https://github.com/Samin325/Home-Lab-Blue/assets/88060791/c0d2ace5-895e-45b5-aaff-2560962189f8)

![image](https://github.com/Samin325/Home-Lab-Blue/assets/88060791/760bb2c2-7d42-474a-b153-1cb8669543d4)

Listen on port 9997 and save:

![image](https://github.com/Samin325/Home-Lab-Blue/assets/88060791/3ba978a0-4f7a-4b33-a139-61532138e314)

![image](https://github.com/Samin325/Home-Lab-Blue/assets/88060791/41fa93da-2c7e-4be7-939c-6178a0abf59d)

Next, go to Settings >> Indexes >> New index and set the name “wineventlog” before saving (keep all the other options as default):

![image](https://github.com/Samin325/Home-Lab-Blue/assets/88060791/c05773ff-5474-4cb7-8277-52c40c388038)

Now, access the pfSense interface from the Kali machine and go to Firewall >> Rules >> Edit and use the following configurations (make sure you are on the Victim Network):

![image](https://github.com/Samin325/Home-Lab-Blue/assets/88060791/e6426935-e28d-4942-9ab8-7dc90a91bd60)

![image](https://github.com/Samin325/Home-Lab-Blue/assets/88060791/ea025fec-e594-46f9-ad89-d3d0a3741cb5)

You should now be able to access the internet from the domain controller (Windows Server)

Make the following changes under Settings>>Internet Options in Internet Explorer:

![image](https://github.com/Samin325/Home-Lab-Blue/assets/88060791/a95d7ee1-e737-4c3d-9208-11e78e34dfa0)

Restart the machine so the change can take effect.

Download the Universal Forwarder (https://www.splunk.com/en_us/download/universal-forwarder.html), 64 bit version:

![image](https://github.com/Samin325/Home-Lab-Blue/assets/88060791/2e39e928-aa66-44ec-b688-35af51d5e0b1)

Run the installer.

Accept the License Agreement and set a username and password:

![image](https://github.com/Samin325/Home-Lab-Blue/assets/88060791/d796ede3-c640-4d6a-a09f-c765ca99850c)

![image](https://github.com/Samin325/Home-Lab-Blue/assets/88060791/f8357079-c867-4627-83e2-2cb7a2fbb748)

Find the IP address of the Splunk machine and use it to fill in the IP fields for the next 2 screens, using the default ports 8089 and 9997:

![image](https://github.com/Samin325/Home-Lab-Blue/assets/88060791/3419e506-aec0-4e01-9460-2347493ce35f)

![image](https://github.com/Samin325/Home-Lab-Blue/assets/88060791/c3128879-4bc4-4223-b747-50b3abd2c865)

![image](https://github.com/Samin325/Home-Lab-Blue/assets/88060791/a3b784b7-6036-46ae-8f73-5d5243327890)

Press “Next” and install. Once completed, go to the Splunk Instance >> Settings >> Add Data:

![image](https://github.com/Samin325/Home-Lab-Blue/assets/88060791/8d1c4803-52f5-401f-a753-436fdcc5ee70)

Click “Forward” and select the domain controller and enter a name:

![image](https://github.com/Samin325/Home-Lab-Blue/assets/88060791/8f73adac-46b3-4d58-9f17-937b504dfbbd)

Select which Local Event Logs to keep track of:

![image](https://github.com/Samin325/Home-Lab-Blue/assets/88060791/bc69fb90-2f32-4cf6-9608-7273fc31107b)

Choose the “wineventlog” as the Index:

![image](https://github.com/Samin325/Home-Lab-Blue/assets/88060791/c7987741-c3dc-4d90-8bbf-94b196a92b5c)

Click “Review” and then “Submit”
