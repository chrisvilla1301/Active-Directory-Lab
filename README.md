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

Allow it to boot up and simply go through the set up / installation process. :

<br/><img src="https://i.imgur.com/2FBCR02.png"/>

Once it has finished installing, allow the machine to boot up :

<br/><img src="https://i.imgur.com/EdCNfnt.png"/>

<br/><img src="https://i.imgur.com/Jexfc5U.png"/>


<!--
 ```diff
- text in red
+ text in green
! text in orange
# text in gray
@@ text in purple (and bold)@@
```
--!>
