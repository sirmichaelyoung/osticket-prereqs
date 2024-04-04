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

- PHPManagerForIIS_V1.5.0.msi
- rewrite_amd64_en-US.msi
- php-7.3.8-nts-Win32-VC15-x86.zip
- VC_redist.x86.exe
- mysql-5.5.62-win32.msi
- HeidiSQL_12.3.0.6589_Setup.exe
- osTicket-v1.15.8.zip

We will use these files to install osTicket and some of the dependencies.

<h2>Installation Steps</h2>

<p>
  <img width="359" alt="Screenshot 2024-04-02 at 10 11 06 PM" src="https://github.com/sirmichaelyoung/osticket-prereqs/assets/163785883/44690cf5-1cc3-491c-9258-d0a84bb58ea7">
</p>
<p>
Part 1: Create Virtual Machine in Azure
  
Start by  creating a Resource Group. Then, create a Windows 10 Virtual Machine (VM) with 2-4 Virtual CPUs. Select the option to create a new Virtual Network (Vnet) in the networking section.

</p>
<br />

<p>
  <img width="540" alt="Screenshot 2024-04-02 at 10 23 15 PM" src="https://github.com/sirmichaelyoung/osticket-prereqs/assets/163785883/982fa903-0643-497d-aad3-b5bc372622ff">
</p>
<p>
Access the VM with remote desktop.

Next, Install / Enable IIS in Windows WITH CGI and Common HTTP Features

To do this, open Control Panel > Programs > Turn Windows features on or off > [X] Internet Information Services

World Wide Web Services > Application Development Features > [X] CGI

World Wide Web Services > [X] Common HTTP Features ([X] all entities)

<img width="285" alt="Screenshot 2024-04-02 at 10 50 49 PM" src="https://github.com/sirmichaelyoung/osticket-prereqs/assets/163785883/b70b6ba2-6743-42a3-a7c9-719202c6cbb6">

Include IIS Management Console

Internet Information Services > Web Management Tools > [X] IIS Management Console

<img width="286" alt="Screenshot 2024-04-02 at 11 19 59 PM" src="https://github.com/sirmichaelyoung/osticket-prereqs/assets/163785883/eb534054-8543-4cd1-85ad-7d579a506fc6">


Now, Installations:

download and install PHP Manager for IIS (PHPManagerForIIS_V1.5.0.msi)

download and install the Rewrite Module (rewrite_amd64_en-US.msi)

- Open File Explorer, create the directory C:\PHP

download and unzip/extract PHP 7.3.8 (php-7.3.8-nts-Win32-VC15-x86.zip) into C:\PHP

download and install VC_redist.x86.exe.

download and install MySQL 5.5.62 (mysql-5.5.62-win32.msi)
 
 -Typical Setup > Launch Configuration Wizard (after install) > Standard Configuration > (example; Password1)

Run IIS as an Administrator

Register PHP from within IIS

<img width="513" alt="Screenshot 2024-04-03 at 12 22 33 PM" src="https://github.com/sirmichaelyoung/osticket-prereqs/assets/163785883/1c2b9472-23c2-4be1-89b6-04ebed9100f7">

Designate the PHP Executable File Path as C:\PHP\php-cgi.exe

*Within ISS, restart the server under Manage Server Actions 

On to osTicket,

Extract osTicket-v1.15.8.zip, copy "upload" folder into C:\inetpub\wwwroot

-Rename "upload" to "osTicket" within C:\inetpub\wwwroot

*Within ISS, restart the server under Manage Server Actions 

Go to sites > Default > osTicket

<img width="193" alt="Screenshot 2024-04-03 at 12 36 40 PM" src="https://github.com/sirmichaelyoung/osticket-prereqs/assets/163785883/6dfd3d5c-b325-48f8-88be-1613e3cdcbb7">

On the right, click “Browse *:80”

This will bring you to the osTicket Installation page, but some extensions are not yet enabled.

<img width="418" alt="Screenshot 2024-04-03 at 12 38 54 PM" src="https://github.com/sirmichaelyoung/osticket-prereqs/assets/163785883/f92a2436-f225-49a8-95fc-19d28cb6e3bd">

Open IIS, sites > Default > osTicket

Open PHP Manager
Click “Enable or disable an extension”

<img width="255" alt="Screenshot 2024-04-03 at 12 42 20 PM" src="https://github.com/sirmichaelyoung/osticket-prereqs/assets/163785883/81fb28f1-a864-48ac-834e-3e6850ddfb76">

- Enable: php_imap.dll
- Enable: php_intl.dll
- Enable: php_opcache.dll

Within C:\inetpub\wwwroot\osTicket\include

-Rename: ost-sampleconfig.php to: ost-config.php

Open ost-config.php Properties > Security > Advanced

Disable inheritance > Remove All

New > add Everyone > Full Control

<img width="265" alt="Screenshot 2024-04-03 at 12 52 04 PM" src="https://github.com/sirmichaelyoung/osticket-prereqs/assets/163785883/5956f738-0ce1-40c0-9a99-fe92f431385e">

Download and install HeidiSQL_12.3.0.6589_Setup.exe
- Open Heidi SQL
- Create a new session, root/Password1
- Connect to the session
- Create a database called “osTicket”

Continue Setting up osTicket in the browser (click Continue)
- Name Helpdesk
- Default email (receives email from customers)
- MySQL Database: osTicket
- MySQL Username: root
- MySQL Password: Password1
- Install

<img width="356" alt="Screenshot 2024-04-03 at 1 30 47 PM" src="https://github.com/sirmichaelyoung/osticket-prereqs/assets/163785883/afabbfa8-47f9-485d-90f9-f3f3343fb835">

Finally,

Delete "setup" folder in C:\inetpub\wwwroot\osTicket\setup

Go to C:\inetpub\wwwroot\osTicket\include 
- Change ost-config.php permissions to "read" 

Useful reference links
- help desk login page: http://localhost/osTicket/scp/login.php
- End Users osTicket URL: http://localhost/osTicket/

This concludes osTicket Instillation. 

Continue [osTicket: Post-Installation Configuration](https://github.com/sirmichaelyoung/post-install-config)
