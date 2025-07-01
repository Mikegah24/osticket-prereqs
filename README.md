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


