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

- Azure Subscription
- Virtual Machine with Windows 10
- IIS Installed and Enabled
- PHP and Required Extensions

<h2>Installation Steps</h2>

<h3>Step 1</h3>

- Create a virtual machine
- Username: labuser
- Password: osTicketPassword1!
- Confirm **licensing**
- Leave everything as default, Review + Create then select `Create`

<p>
<img src="https://github.com/user-attachments/assets/46e90763-9d87-499e-9b96-82586f0e33c7" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<h3>Step 2</h3>

- Log into the Virtual Machine with Remote Desktop
- Enter public Ip address of the Virtual Machine, then `Connect`
- Enter Username and Password 

<p>
<img src="https://github.com/user-attachments/assets/94842426-217d-4947-8e0c-c853f7d3ecbc" height="55%" width="55%" alt="Disk Sanitization Steps"/>
</p>

<h3>Step 3</h3>

- Download [osTicket-installation-Files.zip](https://drive.google.com/uc?export=download&id=1b3RBkXTLNGXbibeMuAynkfzdBC1NnqaD)
- Unzip on to your desktop. The folder should be called “osTicket-Installation-Files”
- We will use the files in this folder to install osTicket and some of the dependencies
<p>
<img src="https://github.com/user-attachments/assets/6494d4b5-0199-4003-a68a-bfc1139e0ee7" height="30%" width="30%" alt="Disk Sanitization Steps"/>
</p>

<h3>Step 4</h3>

- install / Enable IIS in Windows **WITH CGI**
- `Control Panel > Programs > Programs and Features > Turn Windows features on or off`
- Enable Internet Information Services
- Expand "Application Development Features" > Check **CGI**
  - `World Wide Web Services -> Application Development Features -> [X] CGI`
<p>
<img src="https://github.com/user-attachments/assets/467c826c-a9af-42c9-9462-df9b2f2f6ec1" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>

- Check if the webserver is running
- Type `127.0.0.1` in your browser

__If all is running well you should see this 👇

<img src="https://github.com/user-attachments/assets/453d0cf9-c479-489d-8b18-e508978ba2f4" height="65%" width="65%" alt="Disk Sanitization Steps"/>


- From the “osTicket-Installation-Files” folder, install PHP Manager for IIS (PHPManagerForIIS_V1.5.0.msi)
- From the “osTicket-Installation-Files” folder install the Rewrite Module (rewrite_amd64_en-US.msi)
- Create the directory C:\PHP

<img src="https://github.com/user-attachments/assets/2aab631f-8fa6-4e4a-acdd-32397d75e80b" height="65%" width="65%" alt="Disk Sanitization Steps"/>


- From the “osTicket-Installation-Files” folder, unzip PHP 7.3.8 (php-7.3.8-nts-Win32-VC15-x86.zip) into the “C:\PHP” folder
- From the “osTicket-Installation-Files” folder, install VC_redist.x86.exe.
- From the “osTicket-Installation-Files” folder, install MySQL 5.5.62 (mysql-5.5.62-win32.msi)
  - Typical Setup ->
  - Launch Configuration Wizard (after install) ->
  - Standard Configuration ->
  - Username: root
  - Password: root

<h3>Step 5</h3>

- Open IIS as an Admin

- Register PHP from within IIS (PHP Manager -> C:\PHP\php-cgi.exe)

<img src="https://github.com/user-attachments/assets/e3dbc965-a701-43a0-b451-53f42e46c8af" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<img src="https://github.com/user-attachments/assets/c406baa3-bb13-47d8-aa59-1175223f0871" height="80%" width="80%" alt="Disk Sanitization Steps"/>


- Reload IIS (Open IIS, Stop and Start the server)
<img src="https://github.com/user-attachments/assets/a802b306-db76-4026-b14c-4ddc61925d29" height="80%" width="80%" alt="Disk Sanitization Steps"/>

- Install osTicket v1.15.8
  - From the “osTicket-Installation-Files” folder, unzip “osTicket-v1.15.8.zip” and copy the “upload” folder into “c:\inetpub\wwwroot”
  - Within “c:\inetpub\wwwroot”, Rename “upload” to “osTicket”

<img src="https://github.com/user-attachments/assets/aef94558-913e-48e6-ae52-438c7ee623ab" height="80%" width="80%" alt="Disk Sanitization Steps"/>

- Reload IIS (Open IIS, Stop and Start the server)

- Go to sites -> Default -> osTicket
- On the right, click “Browse *:80”
  
![image](https://github.com/user-attachments/assets/b025c482-4db9-4d3c-9110-e8f21b5b8176)

<img src="https://github.com/user-attachments/assets/b36e9479-c032-4014-bb69-51208845a4bc" height="65%" width="65%" alt="Disk Sanitization Steps"/>

Note that some extensions are not enabled
  - Go back to IIS, sites -> Default -> osTicket
  - Double-click PHP Manager
  - Click “Enable or disable an extension”
      - Enable: php_imap.dll
      - Enable: php_intl.dll
      - Enable: php_opcache.dll
  - Refresh the osTicket site in your browser, observe the changes

Rename: ost-config.php
  - From: C:\inetpub\wwwroot\osTicket\include\ost-sampleconfig.php
  - To: C:\inetpub\wwwroot\osTicket\include\ost-config.php
  - 
Assign Permissions: ost-config.php
  - Disable inheritance -> Remove All
  - New Permissions -> Everyone -> All

![image](https://github.com/user-attachments/assets/ceae667c-3bf6-4c81-b9bf-e4500b358e84)

Continue Setting up osTicket in the browser (click Continue)
  - Name Helpdesk
  - Default email (receives email from customers)

From the “osTicket-Installation-Files” folder, install HeidiSQL.
  - Open Heidi SQL
  - Create a new session, root/root
  - Connect to the session
  - Create a database called “osTicket”
    
![image](https://github.com/user-attachments/assets/2bd73122-7bc9-4298-abca-8fb67e389462)

Continue Setting up osTicket in the browser
  - MySQL Database: osTicket
  - MySQL Username: root
  - MySQL Password: root
  - Click “Install Now!”

![image](https://github.com/user-attachments/assets/68c48d78-f97c-4b1b-b317-69d673576e9c)

Congratulations, hopefully it is installed with no errors!
  - Browse to your help desk login page: http://localhost/osTicket/scp/login.php

<img src="https://github.com/user-attachments/assets/e4ca5a22-fd2c-4fdc-9f85-ba58b0f3fdb9" height="60%" width="60%" alt="Disk Sanitization Steps"/>

- End Users osTicket URL: http://localhost/osTicket/

<img src="https://github.com/user-attachments/assets/74e98b81-387d-4942-a5e9-1b38c182e4ea" height="60%" width="60%" alt="Disk Sanitization Steps"/>



!!!CONGRATULATIONS YOU HAVE INSTALLED OS-TICKET!!!🎊

============================================================================================
