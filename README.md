<h2>Active Directory Lab</h1>

<h2>Description</h2>
Project consists of creating an Active Directory environment using Oracle Virtual Box. This tutorial will walk you through creating Virtual Machines, creating a functional Windows Server, Promoting a server to a Domain, Basic Windows Networking, Scopes, Creating user accounts and configuring roles and permissions. 
<br />


<h2>Languages and Utilities Used</h2>

- <b>PowerShell</b> 
- <b>Active Directory</b>
- <b>Oracle Virtual Box<b>
- <b>DHCP<b>
  

<h2>Environments Used </h2>

- <b>Windows 10</b>

<h2>What you will need before we start:</h2>

- <b>Oracle Virtual Box - You can install it here: (add link)<b>
 
- <b>Windows Server ISO -</b>
  
- <b>Windows 10 ISO -</b>

<h2>Lab walk-through:</h2>

<p align="center">

Open Oracle Virtual Box and click "New". 
 
Here I simply named it "WINDOWS SERVER" for the lab but you can name it whatever you'd like. 

Select the folder you'd like to save your Virtual Machine to.

Select the Windows Server ISO image you installed.

Select the edition and version :

<br/><img src="https://i.imgur.com/c2goCEh.png"/>

Next go to "Hardware" and select how much RAM you want to give your VM. Be aware of how much RAM your computer may have.

If you aren't sure you can simply leave it as is :
 
<br/><img src="https://i.imgur.com/cpZEtts.png"/>

Select "Hard Disk".

Here you'll select how much memory you want to give to your VM. Again, be aware of how much memory your computer has to spare.

Once selected click "Finish" :

<br/><img src="https://i.imgur.com/51jEyHh.png"/>

The Virtual Machine is now created. Before we power the VM on we need to configure a few things (The VM might power on automatically after clicking "Finish", simply power it back off)

Right click on your VM and select "Settings". This should bring you to the "General" tab. From here click "Advanced". Change both "Shared Clipboard" and "Drag'n'Drop" to "Bidirectional". This will allow you to drag and drop files from your Host computer to your Virtual Machine :

<br/><img src="https://i.imgur.com/hdTDXPD.png"/>

Next go down to the "Network" tab. Select "Adapter 2", Check "Enable Network Adapter", change the "Attached to:" to "Internal Network" and click "OK":

<br/><img src="https://i.imgur.com/2pSAPqz.png"/>

You can now Power on the Virtual Machine.

Once powered on the Windows Server ISO that was selected should boot up. If you did not select an ISO image before here you will be promted to select one.

Allow it to boot up and simply go through the set up / installation process. Installation may take a while, just allow it to do its thing. :

<br/><img src="https://i.imgur.com/2FBCR02.png"/>

Once it has finished installing, allow the machine to boot up :

<br/><img src="https://i.imgur.com/EdCNfnt.png"/>

<br/><img src="https://i.imgur.com/Jexfc5U.png"/>

Awesome! Now that your Windows Server machine is runnning we're going to configure a few things in the network settings before doing anything else. Click on the mini computer icon on the bottom right of the VM and click the connected network. This should open up your network settings. :

<br/><img src="https://i.imgur.com/Hmd3ln9.png"/>

Click on "Change adapter options". This should open a window displaying your network connections :

<br/><img src="https://i.imgur.com/ZR6wxZt.png"/>

<br/><img src="https://i.imgur.com/xD3R7fd.png"/>

Here you'll need to figure out which network is your Internet (Contains your Home IP Address) and which network is your Internal network. To do this right click on one of the networks and select "Status" then "Details..."
Look at the address displayed next to "IPv4 Address"

If IPv4 Address is:

"10.?.?.etc..." = Home IP Address / Internet

"169.?.?.etc..." = Internal network

Since this network has an IP address of "169.254.31.22" I now know this is my Internal network :

<br/><img src="https://i.imgur.com/pWuJRN3.png"/>

Since this network has an IP address of "10.0.2.15" I now know this is my Home IP Address / Internet :

<br/><img src="https://i.imgur.com/47YzofJ.png"/>

Once you know which network is which be sure to rename them accordingly as you will be using this later.

<br/><img src="https://i.imgur.com/MDRcoPp.png"/>

Now that you've identified your networks, we can configure the IP settings.

Right click on your Internal network and select "Properties", then select "Internal Protocol Version 4 (TCP/IPv4)"

<br/><img src="https://i.imgur.com/zD5DImH.png"/>

Select "Use the following IP address:" and enter the same info displayed in the image. (No time to explain IP addresses here so just trust)

<br/><img src="https://i.imgur.com/VcxYL1j.png"/>

Just something useful to note: The address "127.0.0.1" is the "Loopback" address. This is an address that allows a computer to refer to itself. You can use the loopback address or just use the same address you are trying to refer back to.

<br/><img src="https://i.imgur.com/QNqhnjE.png"/>

Now that your IP settings are configured we will be adding Active Directory Domain Services as well as promoting the server to a Domain.

Open Server Manager and click "Add roles and features" :

<br/><img src="https://i.imgur.com/sQ2vC7K.png"/>

Next...Next...

<br/><img src="https://i.imgur.com/DBj1G6O.png"/>


<br/><img src="https://i.imgur.com/AvU10ML.png"/>

Select your server and click Next :

<br/><img src="https://i.imgur.com/I3zztJU.png"/>

Select "Active Directory Domain Services". Make sure not to select any of the other Active Directory features.

<br/><img src="https://i.imgur.com/Grmt2RP.png"/>

Next...Next...Next...Install

Wait for the installation to complete

Close once it has finished installing :

<br/><img src="https://i.imgur.com/SwC0vlv.png"/>

Now that the features are installed, you can promote the server to a Domain

Click the Flag icon on the top right and select "Promote this server to a domain controller" :

<br/><img src="https://i.imgur.com/lB4zC72.png"/>

Select "Add a new forest" and name the domain whatever you'd like. For the lab I just named it "mydomain.com"

<br/><img src="https://i.imgur.com/v8BKPu3.png"/>

You won't really need this but just fill it out anyways. I just used the password "Password1" for the lab.

<br/><img src="https://i.imgur.com/gEetRiM.png"/>

Next...Next...Next...Install

Wait for it to install :

<br/><img src="https://i.imgur.com/zEPs0tw.png"/>

Once it's finished installing, the VM will restart.

<br/><img src="https://i.imgur.com/T52Vm4n.png"/>

Once your VM's booted back up go to the search icon in the taskbar and search for "Active Directory Users and Computers". Open the application. :

<br/><img src="https://i.imgur.com/OrxTZPm.png"/>

Now you're going to create an Admin account for yourself instead of using the built-in Administrator account.

Right click on the domain name, select "New" then select "Organizational Unit" :

<br/><img src="https://i.imgur.com/SesQCRL.png"/>

Name it something like "Admin Users" or "ADMINS", "Admin Accounts" , etc.
Click "OK"

<br/><img src="https://i.imgur.com/SYN39k9.png"/>

Right click on your admins folder you just created, select "New" and select "User"

<br/><img src="https://i.imgur.com/sFVFIPV.png"/>

Fill out your info with your name or whatever name you prefer. I used my name as an example.
My user logon name is my first initial with my last name. "a-" is just used to signify that it is an admin user.
Hit "Next"

<br/><img src="https://i.imgur.com/a2G1slY.png"/>

Create a password. I am using "Password1" for all passwords in this lab.
Normally you would not uncheck "User must change password at next login" or have "Password never expires" checked, but we will only do this for the purpose of this lab.

Click "Next" 

<br/><img src="https://i.imgur.com/pbQQdyM.png"/>

Your Admin account is created, now you just need to configure it into an admin account.

<br/><img src="https://i.imgur.com/QIMbguR.png"/>

Right click on your account and hit "Properties"

<br/><img src="https://i.imgur.com/a4IC7sU.png"/>

Select "Member of" and then select "Add..."

<br/><img src="https://i.imgur.com/q5hir4h.png"/>

Enter "domain admins" to the box, click "Check Names", then click "OK"

<br/><img src="https://i.imgur.com/5QRTo7H.png"/>

Apply :

<br/><img src="https://i.imgur.com/tup4cK4.png"/>

Your Admin account is now ready for use!

<br/><img src="https://i.imgur.com/i5D7G0q.png"/>

Now we're going to try logging into it.
Log out and select "Other user"

<br/><img src="https://i.imgur.com/tSClyxS.png"/>

<br/><img src=""/>

<br/><img src=""/>

<br/><img src=""/>

<br/><img src=""/>

<br/><img src=""/>

<br/><img src=""/>

<br/><img src=""/>

<br/><img src=""/>

<br/><img src=""/>

<br/><img src=""/>

<br/><img src=""/>

<br/><img src=""/>

<br/><img src=""/>

<br/><img src=""/>

<br/><img src=""/>

<br/><img src=""/>

<br/><img src=""/>

<br/><img src=""/>

<br/><img src=""/>

<br/><img src=""/>

<br/><img src=""/>

<br/><img src=""/>

<br/><img src=""/>

<br/><img src=""/>

<br/><img src=""/>

<br/><img src=""/>

<br/><img src=""/>

<br/><img src=""/>

<br/><img src=""/>

<br/><img src=""/>

<br/><img src=""/>

<br/><img src=""/>

<br/><img src=""/>

<br/><img src=""/>

<br/><img src=""/>

<br/><img src=""/>

<br/><img src=""/>

<br/><img src=""/>

<br/><img src=""/>

<br/><img src=""/>

<br/><img src=""/>

<br/><img src=""/>

<br/><img src=""/>

<br/><img src=""/>

<br/><img src=""/>

<br/><img src=""/>

<br/><img src=""/>

<br/><img src=""/>

<br/><img src=""/>

<br/><img src=""/>

<br/><img src=""/>

<br/><img src=""/>

<br/><img src=""/>

<br/><img src=""/>

<br/><img src=""/>

<br/><img src=""/>

<br/><img src=""/>

<br/><img src=""/>

<br/><img src=""/>

<br/><img src=""/>

<br/><img src=""/>

<br/><img src=""/>

<br/><img src=""/>

<br/><img src=""/>

<br/><img src=""/>

<br/><img src=""/>

<br/><img src=""/>

<br/><img src=""/>

<br/><img src=""/>

<br/><img src=""/>

<br/><img src=""/>

<br/><img src=""/>

<br/><img src=""/>

<br/><img src=""/>

<br/><img src=""/>

<br/><img src=""/>

<br/><img src=""/>

<br/><img src=""/>

<br/><img src=""/>

<br/><img src=""/>

<br/><img src=""/>

<br/><img src=""/>

<br/><img src=""/>

<br/><img src=""/>

<br/><img src=""/>

<br/><img src=""/>

<br/><img src=""/>

<br/><img src=""/>

<br/><img src=""/>

<br/><img src=""/>

<br/><img src=""/>

<br/><img src=""/>

<br/><img src=""/>

<br/><img src=""/>

<br/><img src=""/>

<br/><img src=""/>

<br/><img src=""/>

<br/><img src=""/>

<br/><img src=""/>
<!--
 ```diff
- text in red
+ text in green
! text in orange
# text in gray
@@ text in purple (and bold)@@
```
--!>
