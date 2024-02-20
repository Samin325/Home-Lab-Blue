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
