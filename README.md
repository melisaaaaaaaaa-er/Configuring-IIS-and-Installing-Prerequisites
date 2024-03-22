# Configuring IIS and Installing Prerequisites

<h3>Purpose</h3>

- Setting up the foundational requirements for osTicket.
- Installing osTicket.

<h3>Prerequisites:</h3>

- Create resource group + Windows 10 VM

<h3>Installation Files:</h3>

https://drive.google.com/drive/u/1/folders/1APMfNyfNzcxZC6EzdaNfdZsUwxWYChf6 

<h2>Deployment and Configuration:</h2>

<img src="https://raw.githubusercontent.com/melisaaaaaaaaa-er/osticket-images/main/1.png"/>

Navigate to “Turn Windows Features on or off” on your Windows 10 VM.

Enable IIS (Internet Information Services) with the following features:

-	Application Development Features →
    -	CGI
    - Common HTTP Features
- Web Management Tools →
    - IIS Management Console
- Common HTTP Features →
    - All should be enabled

#
<img src="https://raw.githubusercontent.com/melisaaaaaaaaa-er/osticket-images/main/1.5.png"/>

Go to the web browser and type in 127.0.0.1 (localhost) into the address bar.
If the IIS installation was successful, you should be directed to this page.

#
<img src="https://raw.githubusercontent.com/melisaaaaaaaaa-er/osticket-images/main/2.png"/>

From the installation files, download and install PHP Manager for IIS (PHPManagerForIIS_V1.5.0.msi).

#
<img src="https://raw.githubusercontent.com/melisaaaaaaaaa-er/osticket-images/main/3.png"/>

From the installation files, download and install the Rewrite Module (rewrite_amd64_en-US.msi).

#
<img src="https://raw.githubusercontent.com/melisaaaaaaaaa-er/osticket-images/main/4.png"/>

Create the PHP direction in C:\.

#
<img src="https://raw.githubusercontent.com/melisaaaaaaaaa-er/osticket-images/main/5.png"/>
<img src="https://raw.githubusercontent.com/melisaaaaaaaaa-er/osticket-images/main/6.png"/>

From the installation files, download PHP 7.3.8 (php-7.3.8-nts.Win32-VC15-x86.zip) and unzip the contents into C:\PHP.

When downloading the module, your browser may flag it as unsafe. Select “download anyway” and continue.

After unzipping the file, you may need to drag-and-drop the content of the files into C:\PHP manually.

#
<img src="https://raw.githubusercontent.com/melisaaaaaaaaa-er/osticket-images/main/7.png"/>

From the installation files, download and install VC_redist.x86.exe.

#
<img src="https://raw.githubusercontent.com/melisaaaaaaaaa-er/osticket-images/main/8.png"/>

From the installation files, download and install MySQL 5.5.62 (mysql-5.5.62-win32.msi).
- Typical Setup →
- Launch Configuration Wizard (after install) →
- Standard Configuration →
- Username: root (default – don’t change this), Password: Password123! (you can make this whatever you want. I just wrote something simple for the sake of the lab)

Make sure to remember these credentials. We will need them later.

#
<img src="https://raw.githubusercontent.com/melisaaaaaaaaa-er/osticket-images/main/9.png"/>

Open IIS as an Administrator.

Register PHP from within IIS (scroll down to find this option).
- Find and select php-cgi.exe from the PHP directory created earlier in the C:\ drive.

#
<img src="https://raw.githubusercontent.com/melisaaaaaaaaa-er/osticket-images/main/10.png"/>

Reload IIS using Restart on the right-hand side under Manage Server.

#
<img src="https://raw.githubusercontent.com/melisaaaaaaaaa-er/osticket-images/main/11.png"/>
<img src="https://raw.githubusercontent.com/melisaaaaaaaaa-er/osticket-images/main/12.png"/>

From the installation files, download osTicket.

Extract and copy the “upload” folder to C:\inetpub\wwwroot and rename it to “osTicket” from within the folder. The name must be “osTicket” exactly (i.e. not “osticket” or another variation).

Reload IIS again.

#
<img src="https://raw.githubusercontent.com/melisaaaaaaaaa-er/osticket-images/main/13.png"/>

On IIS, go to Sites → Default → osTicket using the left-hand side drop-down menu.

Click "Browse *:80 (http)" on the right-hand side.

<img src="https://raw.githubusercontent.com/melisaaaaaaaaa-er/osticket-images/main/14.png"/>

If everything has gone according to plan, you should be redirected to the osTicket website.
Note that some extensions are not enabled by default. We must enable them manually on the IIS manager.

#
<img src="https://raw.githubusercontent.com/melisaaaaaaaaa-er/osticket-images/main/15.png"/>

On IIS, go to Sites → Default → osTicket.

Double click the PHP Manager tile. Click “Enable or disable an extension”.

Enable the following extensions:
- php_imap.dll
- php_intl.dll
- php_opcache.dll

<img src="https://raw.githubusercontent.com/melisaaaaaaaaa-er/osticket-images/main/16.png"/>

Refresh the osTicket browser tab to view the changes.

#
<img src="https://raw.githubusercontent.com/melisaaaaaaaaa-er/osticket-images/main/17.png"/>

In C:\inetpub.wwwroot.osTicket\include\, rename ost-sampleconfig.php to ost-config.php.

#
<img src="https://raw.githubusercontent.com/melisaaaaaaaaa-er/osticket-images/main/18.png"/>

Change the permission settings of ost-config.php.

Right click → Properties → Security → Advanced →
- Disable inheritance → Remove All
    - Add → New principal – select “Everyone” → Full control

#
<img src="https://raw.githubusercontent.com/melisaaaaaaaaa-er/osticket-images/main/19.png"/>

From the installation files, download and install HeidiSQL and launch it.

<img src="https://raw.githubusercontent.com/melisaaaaaaaaa-er/osticket-images/main/20.png"/>

Create a new session with the credentials root/Password123!. Connect to the session and create a database called “osTicket”.

#
<img src="https://raw.githubusercontent.com/melisaaaaaaaaa-er/osticket-images/main/21.png"/>

Go back to the osTicket browser and continue setting it up.

<img src="https://raw.githubusercontent.com/melisaaaaaaaaa-er/osticket-images/main/22.png"/>

For the Database settings input the following:
- MySQL Database: osTicket
- MySQL Username: root
- MySQL Password: Password123!
    - Select “Install Now”.

#
<img src="https://raw.githubusercontent.com/melisaaaaaaaaa-er/osticket-images/main/23.png"/>

If the process has gone smoothly, this is the page you should be greeted with after a successful installation.

#

The final step is to change the ost-config.php (C:\inetpub\wwwroot\osTicket\include\ost-config.php) permissions back to “Read” only. 

#
<img src="https://raw.githubusercontent.com/melisaaaaaaaaa-er/osticket-images/main/24.png"/>

osTicket agent login URL: http://localhost/osTicket/scp/login.php 
- Help desk user accounts are called “agents” on osTicket.

<img src="https://raw.githubusercontent.com/melisaaaaaaaaa-er/osticket-images/main/25.png"/>

osTicket end user URL: http://localhost/osTicket/
