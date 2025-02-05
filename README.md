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

Since this network has an IP address of "169.254.31.22" I now know this is my Internal network
<br/><img src="https://i.imgur.com/pWuJRN3.png"/>

Since this network has an IP address of "10.0.2.15" I now know this is my Home IP Address / Internet
<br/><img src="https://i.imgur.com/47YzofJ.png"/>

Once you know which network is which be sure to rename them accordingly as we will be using this later.

<br/><img src="https://i.imgur.com/MDRcoPp.png"/>

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
