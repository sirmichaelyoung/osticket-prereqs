<p align="center">
<img src="https://i.imgur.com/Clzj7Xs.png" alt="osTicket logo"/>
</p>

<h1>osTicket - Prerequisites and Installation</h1>
This tutorial outlines the prerequisites and installation of the open-source help desk ticketing system osTicket.<br />


<h2>Video Demonstration</h2>

- ### [YouTube: How To Install osTicket with Prerequisites](https://www.youtube.com)

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
Internet Information Services -> Web Management Tools -> IIS Management Console -> [X] IIS Management Console

</p>
<br />

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur.
</p>
<br />
