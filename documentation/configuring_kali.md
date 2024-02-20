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
