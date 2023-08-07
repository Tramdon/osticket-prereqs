<p align="center">
<img src="https://i.imgur.com/Clzj7Xs.png" alt="osTicket logo"/>
</p>

<h1>osTicket - Prerequisites and Installation</h1>
This tutorial outlines the prerequisites and installation of the open-source help desk ticketing system osTicket.<br />



<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Internet Information Services (IIS)

<h2>Operating Systems Used </h2>

- Windows 10</b> (21H2)

<h2>List of Prerequisites</h2>

- Create a virtual machine with azure
- Open the VM using Remote Desktop 
- Enable IIS on the VM
- Download and install PHP Manager for IIS
- Download and install the Rewrite Module
- Create the directory C:\PHP
- Download PHP 7.3.8 and unzip the contents into C:\PHP
- Download and install VC_redist.x86.exe
- Download and install MySQL 5.5.62
- Open IIS as an Admin
- Register PHP from within IIS
- Install osTicket v1.15.8
- Download and install HeidiSQL
- Continue Setting up osticket in the browser





<h2>Installation Steps</h2>

<p>
<img src="https://i.imgur.com/klz7AYN.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
On your browser go to portal.azure.com then create a Windows 10 Virtual Machine (VM) with 2-4 Virtual CPUs. Name the Virtual Machine "osticket-lab". Create a username and password that you can remember. Make sure you check the licensing agreement or you will not be able to continue. When ready click review + create. Then click create again.
</p>
<br />

<p>
<img src="https://i.imgur.com/YJ7P3Gw.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
When your deployment is complete click "go to resource" then copy the public ipadress of the VM.
</p>
<br />

<p>
<img src="https://i.imgur.com/f1CkLtN.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Click your windows key then type in "Remote Desktop" once you see it click "open" then paste your ip adress. Click "connect" then type in your username and password that you created. There will be a popup just click "yes". When the virtual machine begins, it will request some privacy choices. Just check all the boxes to turn them off.
</p>
<br />
<img src="https://i.imgur.com/yXlbvEK_d.webp?maxwidth=760&fidelity=grand" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Open this link: https://drive.google.com/drive/u/1/folders/1APMfNyfNzcxZC6EzdaNfdZsUwxWYChf6 this link holds the files needed to install osTicket.
</p>
<p>
<img src="https://i.imgur.com/jwuclnY.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Open Control Panel and navigate to "Programs and Features." Click on "Turn Windows features on or off." Ensure that the box for "Internet Information Services" is checked. Expand the options for "IIS," "World Wide Web Services," and "Application Development Features." Check the box next to "CGI" under "Application Development Features." Also, expand "Common HTTP Features" and select all the boxes in the dropdown that are not already checked. After checking all the required boxes, click "OK" and then "Apply" to install the features.
</p>
<br /><p>
<img src="https://i.imgur.com/ToZI6BF.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
Use the links given to install "PHPManagerForIIS" and "rewrite_amd64." After the installations, make a new folder named "PHP" on your C: Drive. Get the file called php-7.3.8-nts-Win32-VC15-x86.zip. Unzip the files from that download into the "PHP" folder you made earlier. Once you've completed extracting all the files, proceed to download and install "VC_redist.x86.exe".
<p>
`</p>
<br />
<img src="https://i.imgur.com/zSCJR5e.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
Download MySQL 5.5.62 from the Installation Files (mysql-5.5.62-win32.msi). Choose the "Typical Setup" option. Launch the Configuration Wizard after the installation. Select "Standard Configuration." Set the password as "Password1." Click next then execute.
<p>
<br />
<img src="https://i.imgur.com/MFNiAR9.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Use Windows Explorer to find and open "Internet Information Services (IIS) Manager" with Administrator rights. Inside IIS Manager, locate and select "PHP Manager." Click on "Register New PHP Version." Browse to the previously made "PHP" folder, then pick the "php-cgi" executable.
</p>
<br /> 
<img src="https://i.imgur.com/toCN77N.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Download osTicket from the Installation Files Folder and extract it. Copy the "upload" folder. Navigate to C: > inetpub > wwwroot and paste the copied "upload" folder there. Rename the "upload" folder to "osTicket" in the C:\inetpub\wwwroot directory. For this, open two separate File Explorer windows. In one window, go to the Downloads folder and open the "osTicket-v1.15.8" folder. Inside, you'll see the "upload" folder. In the other window, access the Windows (C:) drive. Open the "inetpub" folder, then open the "wwwroot" folder. Drag the "upload" folder from the first window into the "wwwroot" folder. Once that's done, rename the moved "upload" folder in the wwwroot directory to "osTicket." In IIS, expand VM-osTicket > Sites > Default Web Site > osTicket. Click on "Browse *:80 (http)" (This option is usually found under "Manage Folder" on the right side of the window). This action will take you to the osTicket Installer website for setting up your help desk.
</p>
<br /> 

<img src="https://i.imgur.com/Ka3MjzI.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Now return to VM-osTicket > Sites > Default Web Site > osTicket. Look for "PHP Extensions" on the main page. Beneath it, you'll find the option "Enable or disable an extension." Click on that option to access the list of features. You will see three features to enable: "php_imap.dll," "php_intl.dll," and "php_opcache.dll." Locate these features in the list, right-click on them, and choose to enable them. Refresh the osTicket Installer webpage. You should now see two enabled checkmarks: "PHP IMAP Extension" and "Intl Extension."
</p>
<br /> 

<img src="https://i.imgur.com/f2OW1xO.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Before proceeding on the webpage, there are two more tasks. Find the "ost-sampleconfig" file at C:/ > inetpub > wwwroot > osTicket > include > ost-sampleconfig.php and rename it to "ost-config.php." With the newly renamed "ost-config.php" file: Right-click and choose "Properties." Go to the "Security" tab and click "Advanced." Click the "Disable Inheritance" button and "Remove all inherited permissions from this object." Click "Add," then "Select a principal." Type "Everyone" in the text field and click "Check Names." Then, click OK. Check the "Full control" button to grant everyone full control. Apply these changes.
</p>
<br /> 

<img src="https://i.imgur.com/XvlMGAz.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Now, let's move forward on the webpage: Click the "Continue" button at the bottom of the page. Some features might remain un-added, but that's okay for this tutorial. On the next page, you'll need to provide basic information for the help desk. The essential details to remember are your login credentials (username and password). Jot these down, as they'll be used for help desk administration. 
</p>
<br /> 

<img src="https://i.imgur.com/70nBRZy.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Before proceeding with the installation, download HeidiSQL from the provided Installation Files. Ensure that HeidiSQL launches after installation. After HeidiSQL launches, click "New" at the bottom left corner. Use the MySQL login credentials from earlier, inputting the user and password. If not already set, the user should be "root." Click the "Open" button. Within the created database, right-click the "Unnamed" session and select "Create new," then choose "Database." Name the new database "osTicket" and confirm by clicking OK.
</p>
<br /> 
<img src="https://i.imgur.com/oZg32Ra.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Go to C: Drive > inetpub > wwwroot > osTicket. Delete the "Setup" folder from there. After deleting the setup folder, proceed to C: Drive > inetpub > wwwroot > osTicket > include. Right-click on the ost-config file. Go to Properties > Security Tab > Advanced. Choose the "Everyone" option from the list and click "Edit." Uncheck all boxes except for "Read" and "Read & execute." Apply the changes.
</p>
<br /> 
<img src="https://i.imgur.com/Mm276hO.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Lastly, Simply copy and paste this URL into your web browser: http://localhost/osTicket/scp/login.php This will grant you access to the Staff Control Panel.
</p>
<br /> 


