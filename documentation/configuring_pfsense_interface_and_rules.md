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
