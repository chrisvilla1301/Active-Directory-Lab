<h2>Active Directory Lab</h1>

<h2>Description</h2>
Project consists of creating an Active Directory environment using Oracle Virtual Box.

<h2>What you will learn in this lab</h2>

- How to create Virtual Machines in Oracle Virtual Box
 
- How to create a functional Windows Server
  
- How to promote a server to a domain
 
- Basic Windows Networking
 
- Basic Active Directory configuring
  
- Basic DHCP Configuring / Creating scopes
 
- How to create user accounts with PowerShell
  
- How to create a client and connect it to a domain


<h2>Applications and Utilities Used</h2>


- <b>Oracle Virtual Box<b>
- <b>Server Manager<b>
- <b>IPv4<b>
- <b>Active Directory</b>
- <b>Routing and Remote Access<b>
- <b>DHCP<b>
- <b>PowerShell</b>
  

<h2>Windows Versions Used </h2>

- <b>Windows 10 Pro</b>
- <b>Windows Server 2022</b>

<h2>What you will need before we start:</h2>

- <b>Oracle Virtual Box - You can install it here: https://www.virtualbox.org/wiki/Downloads<b>
 
- <b>Windows Server ISO: https://mega.nz/file/K6A1nb5Q#YEipCtNX_YYSZER1XucDxrsLVjr-6YBmjTamX42lI68 -</b>
  
- <b>Windows 10 ISO: https://mega.nz/file/3zRQFbbS#LP2w9fOswWahn-OoSzgEAnnjSbaarVmacGKBz5Qiyjk -</b>

- <b>PowerShell Script (1000+ Users): https://www.youtube.com/redirect?event=video_description&redir_token=QUFFLUhqa0w0c3dJLXZUZVEteTlSZl82eEdzMWJLVDRrZ3xBQ3Jtc0trUnpnMGNOVW1ydVRpbkRlaUZtYmhCekZKeUI1NlNDX0huZG41NVlvT1FrRWhxMWN5bmNRbVFweEtTR1Blb1pNbllJdEQ4am9NRmZzVjFhZmRKSjFUbTB5WjZlYzBmMGU2bjcyY21IZ1VEbnVtVEtmNA&q=https%3A%2F%2Fgithub.com%2Fjoshmadakor1%2FAD_PS%2Farchive%2Frefs%2Fheads%2Fmaster.zip&v=MHsI8hJmggI </b>

Here is a diagraham of what we will be doing. Make sure to save this to help you while going through this lab : 

<br/><img src="https://i.imgur.com/KoGeluD.png"/>

<h2>Lab walk-through:</h2>

<p align="center">

First we will start with creating our Windows Server and promoting it into a domain, which will be our Domain Controller.

Open Oracle Virtual Box and click "New". 
 
Here I simply named it "WINDOWS SERVER" for the lab but you can name it whatever you'd like. 

Select the folder you'd like to save your Virtual Machine to.

Select the Windows Server ISO image you installed.

Select the edition and version

You can check "Skip unattended installation" :

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

Open Server Manager and click "Add roles and features" (You will be doing this a lot) :

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
Log out and select "Other user" aand enter your login info :

<br/><img src="https://i.imgur.com/tSClyxS.png"/>

<br/><img src="https://i.imgur.com/PnCOsSB.png"/>

Now we're signed in to our Admin account!

<br/><img src="https://i.imgur.com/kQ1BpBx.png"/>

Next we're going to install RAS / NAT . This will allow our client (once we create our client VM later) to be on a virtual "private" network but still be able to access the internet through the domain.

Open Server Manager and click "Add roles and features" :

<br/><img src="https://i.imgur.com/kdkq9lm.png"/>

Next...Next...Select your server...Next :

<br/><img src="https://i.imgur.com/N5cktOA.png"/>

Select "Remote Access" and hit Next :

<br/><img src="https://i.imgur.com/83S1M8e.png"/>

Select "Routing" and hit Next :

<br/><img src="https://i.imgur.com/aCNZRVI.png"/>

Select Install and wait for the features to install :

<br/><img src="https://i.imgur.com/kLH1ECh.png"/>

Once finished, select "Tools" on the top right and select "Routing and Remote Access" :

<br/><img src="https://i.imgur.com/XfK0SjS.png"/>

Right click on your server and select "Configure and Enable Routing and Remote Access" :

<br/><img src="https://i.imgur.com/TxvlSJD.png"/>

Next :

<br/><img src="https://i.imgur.com/kQ6hPtT.png"/>

Select "NAT" and hit Next :

<br/><img src="https://i.imgur.com/3Rfqrdk.png"/>

You should see your network connections inside the box.
If there's nothing or it's grayed out for you just exit out and reopen the "Routing and Remote Access" tool:

Once you see your network connections select your Internet and hit Next :

<br/><img src="https://i.imgur.com/QyIhck0.png"/>

Finish :

<br/><img src="https://i.imgur.com/bn2wnki.png"/>

If you refresh your server you can now see the symbol has turned green

<br/><img src="https://i.imgur.com/aehzagr.png"/>

Now that we have completed that we will set up a DHCP Server :

Open Server Manager and select "Add roles and features" :

<br/><img src="https://i.imgur.com/XK8BhUi.png"/>

Next...Next...select your server...Next :

<br/><img src="https://i.imgur.com/PnkIsRK.png"/>

Select "DHCP Server" and hit Next :

<br/><img src="https://i.imgur.com/2rB8gNF.png"/>

Install and wait for it to finish installing :

<br/><img src="https://i.imgur.com/vOOcrmC.png"/>

Once finished select "Tools" and select "DHCP"
The purpose of this is to automatically give each client computer connected to the Network an IP address  :

<br/><img src="https://i.imgur.com/006GE20.png"/>

Right click on "IPv4" and select "New Scope..." :

<br/><img src="https://i.imgur.com/7FA7ZlC.png"/>

Here it's useful to name the scope the same as the IP address. I named it "172.16.0.100-200" since we will give IP addreses within this range :

<br/><img src="https://i.imgur.com/VajdRX4.png"/>

Here simply copy the info below and hit Next :

<br/><img src="https://i.imgur.com/BkhN659.png"/>

Yes...Next :

<br/><img src="https://i.imgur.com/hpLbhRJ.png"/>

Enter "172.16.0.1" and make sure to click "Add" before selecting Next :

<br/><img src="https://i.imgur.com/AtXAFpT.png"/>

Next :

<br/><img src="https://i.imgur.com/CO2Cthp.png"/>

Yes...Next :

<br/><img src="https://i.imgur.com/N0HJ8Tt.png"/>

Finish :

<br/><img src="https://i.imgur.com/3lNe7jV.png"/>

You might need to "Authorize". Right click on the server and select "Authorize" then "Refresh" :

<br/><img src="https://i.imgur.com/FdDcLyi.png"/>

<br/><img src="https://i.imgur.com/SlNcoZR.png"/>

Now you can see both icons have turned green

<br/><img src="https://i.imgur.com/cFi9gA8.png"/>

Next we will disable IE Enhanced Security only for the purpose of this lab. Normally you would not do this in a work environment.

<br/><img src="https://i.imgur.com/Qlqw14P.png"/>

<br/><img src="https://i.imgur.com/y7bDDee.png"/>

Next we are going to create a bunch of users for our server using PowerShell.

First open the "AD_PS_master" folder previously downloaded. This is a script that we will Run in Windows PowerShell that will automatically generate 1000+ users for our server. This will allow you to get a more realistic feel of a real life IT work environment and allow you to play around with it.

NOTE: All users will have a username consisting of their first initial + their last name. All passwords will be "Password1" for the purpose of this lab.

<br/><img src="https://i.imgur.com/auhnrNN.png"/>

Open the "names" .txt file :

<br/><img src="https://i.imgur.com/ggTv9nw.png"/>

At the top I put my name as an example but you can use whatever you'd like. This will be our client user :

<br/><img src="https://i.imgur.com/ouHpNiO.png"/>

Next search for "Windows PowerShell ISE" and Run as Administrator :

<br/><img src="https://i.imgur.com/RS9Y7W2.png"/>

Select "File" and "Open..." :

<br/><img src="https://i.imgur.com/dklJrq2.png"/>

Now select "1_CREATE _USERS" from wherever you saved the "AD_PS_master" folder and click Open

<br/><img src="https://i.imgur.com/VcxU9pu.png"/>

You'll see if you try to Run the script you'll get an error :

<br/><img src="https://i.imgur.com/oRk6u8M.png"/>

To fix this error enter "Set-ExecutionPolicy Unrestricted" and hit enter.
Select "Yes to all"
This allows you to run all scripts :

<br/><img src="https://i.imgur.com/MxMRXt8.png"/>

<br/><img src="https://i.imgur.com/tPpIHgM.png"/>

Before running the script you need to be in the same directory as the script for it to work.
Enter "cd c:users\(your user account)\(wherever you saved the folder to)\AD_PS_master" and hit enter :

<br/><img src="https://i.imgur.com/X8Ujt4c.png"/>

If you enter "ls" you can see now you're inside the same directory as the script.

<br/><img src="https://i.imgur.com/Lm7AdNA.png"/>

Now you can run the script! Click "Run" and select "Run once"

<br/><img src="https://i.imgur.com/nPduQ0h.png"/>

Now just allow it to finish generating users for you.

<br/><img src="https://i.imgur.com/fRRqVK9.png"/>

You may notice a few errors, they are simply duplicate names so nothing to worry about :

<br/><img src="https://i.imgur.com/DFSBcWC.png"/>

Once it has finished, you can open Active Directory Users and Computers, and now you'll see a "_USERS" folder has been created from the script. If you click on it you can see all the users that were created.

<br/><img src="https://i.imgur.com/VRUO6lS.png"/>

Let's search for our user account!
Right click on the server and select "Find..."

<br/><img src="https://i.imgur.com/uPQwgBR.png"/>

Enter the name you typed into the script .txt file earlier and select "Find Now"

<br/><img src="https://i.imgur.com/iiBRhIn.png"/>

As you can see we have 2 user accounts that were found (if you used the same name). One user is the Domain Admin account we created earlier, and the other is our user account that was just created with our batch of users.
We will be logging into our client VM using our new user account.

<br/><img src="https://i.imgur.com/ejurxeo.png"/>

Cool! Almost finished! The last thing we need to do now is create a new virtual machine for our Windows 10 client and connect it to our server. :

Go back to Oracle Virtual Box and select "New"

<br/><img src="https://i.imgur.com/TbqmMbu.png"/>

I simply named mine "CLIENT1" but you can name it whatever you'd like.

Select the folder you'd like to save your Virtual Machine to.

Select the Windows 10 ISO image you installed

Select the edition and version

You can check "Skip unattended installation" :

<br/><img src="https://i.imgur.com/msfsz1Z.png"/>

Go to "Hardware" and select how much RAM you want to give your VM

If you aren't sure you can simply leave it as is :

<br/><img src="https://i.imgur.com/2zPc1By.png"/>

Select "Hard Disk".

Select how much memory you want to give to your VM. Again, be aware of how much memory your computer has to spare.

Once selected click "Finish"

<br/><img src="https://i.imgur.com/n2GW9zU.png"/>

Before powering on the VM we are going to configure a few things.
Right click the client VM and select "Settings"

Change Shared Clipboard and Drag'n'drop to "Bidirectional"

<br/><img src="https://i.imgur.com/JEMabzv.png"/>

Then go to the "Network" tab. Since we're emulating a "Corporate" network change the "Attached to" to "Internal Network"

Hit OK and now you can power on the client machine :

<br/><img src="https://i.imgur.com/lyXurfl.png"/>

Once the machine has booted up simply go through the setup : 

<br/><img src="https://i.imgur.com/J1g9Dnx.png"/>

<br/><img src="https://i.imgur.com/F1Y9I09.png"/>

Make sure to select "Windows 10 Pro" as you cannot connect to the domain with the Home edition of Windows

<br/><img src="https://i.imgur.com/Dhw3tuI.png"/>

Next :

<br/><img src="https://i.imgur.com/VUXY46g.png"/>

Select "Custom" since we have nothing on the hard drive

<br/><img src="https://i.imgur.com/PYA0S1z.png"/>

Hit Next and allow it to install and reboot itself. This may take a while. :

<br/><img src="https://i.imgur.com/ypqwnPF.png"/>

<br/><img src="https://i.imgur.com/4e18IQR.png"/>

<br/><img src="https://i.imgur.com/21NQKd1.png"/>

Once it has rebooted go through the setup :

<br/><img src="https://i.imgur.com/QaE61JW.png"/>

If promted to select an internet connection just click "I don't have internet"

Make sure to click "Limited experience" if you get this window so you aren't promted to create a Microsoft account. You want to keep it as a local / home account :

<br/><img src="https://i.imgur.com/BwdH4uD.png"/>

I named mine "user" but you can use whatever you'd like.

<br/><img src="https://i.imgur.com/tF2LdgB.png"/>

Just click Next, you don't need to enter a password here. :

<br/><img src="https://i.imgur.com/UFQG2QK.png"/>

I disabled all of these features but that's personal preference, you can just hit Next or Accept if you'd like :

<br/><img src="https://i.imgur.com/IzIyNpk.png"/>

Allow the VM to start up :

<br/><img src="https://i.imgur.com/ygtqyIz.png"/>

<br/><img src="https://i.imgur.com/P86V0kC.png"/>

The client VM is now created

<br/><img src="https://i.imgur.com/zcBFWUf.png"/>

Now we are going to check our IP addresses. Open command line and enter "ipconfig".
Your client computer should have a Default Gateway address.

<br/><img src="https://i.imgur.com/cVuH2ZH.png"/>

If you do not have a Default Gateway address this means you did not click "Add" back when we created a Scope for your server. Simply go back to your WINDOWS SERVER VIRTUAL MACHINE (NOT YOUR CLIENT VIRTUAL MACHINE), and go back to the DHCP tool to add the IP address.

<br/><img src="https://i.imgur.com/AtXAFpT.png"/>

Click the Start button and go to "System" 

Scroll down until you find "Rename this PC (advanced)" and click it. This should open the System Properties window. Click "Change".

Here we are going to rename the PC to "CLIENT1" and also join the Domain. After you've renamed your PC select the "domain" option under "Member of". Enter your domain name and click OK. This should prompt you to enter a domain admin account. Enter your domain admin account you created earlier and click OK. 

Allow the system to Restart :

<br/><img src="https://i.imgur.com/1K0pa2J.png"/>

<br/><img src="https://i.imgur.com/hcTNtnp.png"/>

<br/><img src="https://i.imgur.com/cYkLyfQ.png"/>

If you go back to your Domain Controller (WINDOWS SERVER VM) and go into your DHCP tool > IPv4 > Scope > Address Leases you are able to see the IP addresses automatically assigned to your clients by DHCP when they are connected to the network. Here we only have one but in a work environment you would probably have hundreds of addresses depending how big the scope is.

<br/><img src="https://i.imgur.com/5FOWu1o.png"/>

And if you check the "computers" folder in Active Directory Users and Computers you can now see you have the client computer. Here you can see any computers that are connected to your domain. These computers can login using any of the generated user accounts, which is our final step!

<br/><img src="https://i.imgur.com/vKJ3aFP.png"/>

Logout of the built-in user account in your client VM. Select "Other User" and enter your login info (You can play around with this and login in with any of the accounts you generated)

<br/><img src="https://i.imgur.com/6HZ2nRT.png"/>

<br/><img src="https://i.imgur.com/VSS8Nu2.png"/>

Allow the system to start up :

<br/><img src="https://i.imgur.com/pqVygQD.png"/>

Congrats! Now that the system has booted up, you've completed this lab! 

<br/><img src="https://i.imgur.com/XgoDp0s.png"/>

Now you can play around with the server however you'd like! It is useful to go through this lab more than once to get a better understanding of an Active Directory environment. Try creating more servers along with this tutorial, eventually attempting to create and set up a server without the need for a walk-through. 

Thank you for taking the time to read through this tutorial, I hope it was easy to follow and helped you understand Active Directory better! 




