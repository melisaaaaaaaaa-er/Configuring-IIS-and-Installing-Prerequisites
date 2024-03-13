# Configuring IIS and Installing Prerequisites

<h2>Prerequisites:</h2>

- Create resource group + Windows 10 VM

<h2>Installation Files:</h2>

https://drive.google.com/drive/u/1/folders/1APMfNyfNzcxZC6EzdaNfdZsUwxWYChf6 

<h2>Deployment and Configuration:</h2>

![1](https://github.com/melisa-er/Configuring-IIS-and-Installing-Prerequisites/assets/157723219/13676c6c-65ed-43a2-b39d-2a749ebc2053)

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
![1 5](https://github.com/melisa-er/Configuring-IIS-and-Installing-Prerequisites/assets/157723219/8c2ee180-9391-4eaf-9a91-f07f46db3095)

Go to the web browser and type in 127.0.0.1 (localhost) into the address bar.
If the IIS installation was successful, you should be directed to this page.

#
![2](https://github.com/melisa-er/Configuring-IIS-and-Installing-Prerequisites/assets/157723219/2399fc7f-c154-4814-ab94-e6eea93d51e4)

From the installation files, download and install PHP Manager for IIS (PHPManagerForIIS_V1.5.0.msi).

#
![3](https://github.com/melisa-er/Configuring-IIS-and-Installing-Prerequisites/assets/157723219/c262e3ca-bbed-4fd0-a020-5e7b79f5559f)

From the installation files, download and install the Rewrite Module (rewrite_amd64_en-US.msi).

#
![4](https://github.com/melisa-er/Configuring-IIS-and-Installing-Prerequisites/assets/157723219/5a1af383-5c03-4445-9e17-360891ecb22f)

Create the PHP direction in C:\.

#
![5](https://github.com/melisa-er/Configuring-IIS-and-Installing-Prerequisites/assets/157723219/05fef50c-eef7-4780-9af6-065dcb961e6d)
![6](https://github.com/melisa-er/Configuring-IIS-and-Installing-Prerequisites/assets/157723219/b88aca57-5d1e-4e18-acca-e209ded4ef01)

From the installation files, download PHP 7.3.8 (php-7.3.8-nts.Win32-VC15-x86.zip) and unzip the contents into C:\PHP.

When downloading the module, your browser may flag it as unsafe. Select “download anyway” and continue.

After unzipping the file, you may need to drag-and-drop the content of the files into C:\PHP manually.

#
![7](https://github.com/melisa-er/Configuring-IIS-and-Installing-Prerequisites/assets/157723219/ab6c4995-cd96-4d76-b68e-3cc097d650ec)

From the installation files, download and install VC_redist.x86.exe.

#
![8](https://github.com/melisa-er/Configuring-IIS-and-Installing-Prerequisites/assets/157723219/9cfeaf24-3d08-4148-a794-629ece0db211)

From the installation files, download and install MySQL 5.5.62 (mysql-5.5.62-win32.msi).
- Typical Setup →
- Launch Configuration Wizard (after install) →
- Standard Configuration →
- Username: root (default – don’t change this), Password: Password123! (you can make this whatever you want. I just wrote something simple for the sake of the lab)

Make sure to remember these credentials. We will need them later.

#
![9](https://github.com/melisa-er/Configuring-IIS-and-Installing-Prerequisites/assets/157723219/965876d3-de12-41f3-88e5-82e6a2acc817)

Open IIS as an Administrator.

Register PHP from within IIS (scroll down to find this option).
- Find and select php-cgi.exe from the PHP directory created earlier in the C:\ drive.

#
![10](https://github.com/melisa-er/Configuring-IIS-and-Installing-Prerequisites/assets/157723219/eaedc038-b259-467c-ad03-8c770d5a3618)

Reload IIS using Restart on the right-hand side under Manage Server.

#
![11](https://github.com/melisa-er/Configuring-IIS-and-Installing-Prerequisites/assets/157723219/37db6892-3d87-41ee-9f48-90f21a1c692e)
![12](https://github.com/melisa-er/Configuring-IIS-and-Installing-Prerequisites/assets/157723219/4ff817f0-f9e4-4da8-8bd3-b57f7b8bac3f)

From the installation files, download osTicket.

Extract and copy the “upload” folder to C:\inetpub\wwwroot and rename it to “osTicket” from within the folder. The name must be “osTicket” exactly (i.e. not “osticket” or another variation).

Reload IIS again.

#
![13](https://github.com/melisa-er/Configuring-IIS-and-Installing-Prerequisites/assets/157723219/0b1fbb27-255b-487a-91fa-982b1f6a68a5)

On IIS, go to Sites → Default → osTicket using the left-hand side drop-down menu.

Click "Browse *:80 (http)" on the right-hand side.

![14](https://github.com/melisa-er/Configuring-IIS-and-Installing-Prerequisites/assets/157723219/bf650a5c-0618-46de-b0ee-8373cb545c60)

If everything has gone according to plan, you should be redirected to the osTicket website.
Note that some extensions are not enabled by default. We must enable them manually on the IIS manager.

#
![15](https://github.com/melisa-er/Configuring-IIS-and-Installing-Prerequisites/assets/157723219/61b2984f-24d3-476c-890b-67b378efd1ec)

On IIS, go to Sites → Default → osTicket.

Double click the PHP Manager tile. Click “Enable or disable an extension”.

Enable the following extensions:
- php_imap.dll
- php_intl.dll
- php_opcache.dll

![16](https://github.com/melisa-er/Configuring-IIS-and-Installing-Prerequisites/assets/157723219/4de03ecc-55ef-4043-a06b-dfcd609d634e)

Refresh the osTicket browser tab to view the changes.

#
![17](https://github.com/melisa-er/Configuring-IIS-and-Installing-Prerequisites/assets/157723219/36d35d7a-028c-49e0-9142-5c1e68885d85)

In C:\inetpub.wwwroot.osTicket\include\, rename ost-sampleconfig.php to ost-config.php.

#
![18](https://github.com/melisa-er/Configuring-IIS-and-Installing-Prerequisites/assets/157723219/ec7e740a-1467-405a-9a2b-b963eb8b7b4f)

Change the permission settings of ost-config.php.

Right click → Properties → Security → Advanced →
- Disable inheritance → Remove All
    - Add → New principal – select “Everyone” → Full control

#
![19](https://github.com/melisa-er/Configuring-IIS-and-Installing-Prerequisites/assets/157723219/162ae9d6-f886-488f-9e0e-fd77f6d67dca)

From the installation files, download and install HeidiSQL and launch it.

![20](https://github.com/melisa-er/Configuring-IIS-and-Installing-Prerequisites/assets/157723219/15097c98-d3b0-4fa3-bbf4-31282a6579d2)

Create a new session with the credentials root/Password123!. Connect to the session and create a database called “osTicket”.

#
![21](https://github.com/melisa-er/Configuring-IIS-and-Installing-Prerequisites/assets/157723219/688ecbb0-5998-45a8-b742-5265e5ad9e9f)

Go back to the osTicket browser and continue setting it up.

![22](https://github.com/melisa-er/Configuring-IIS-and-Installing-Prerequisites/assets/157723219/66972640-a7b6-46df-8749-6f7e1c9159c6)

For the Database settings input the following:
- MySQL Database: osTicket
- MySQL Username: root
- MySQL Password: Password123!
    - Select “Install Now”.

#
![23](https://github.com/melisa-er/Configuring-IIS-and-Installing-Prerequisites/assets/157723219/d1d0854c-2d26-40d1-a833-2915d514212f)

If the process has gone smoothly, this is the page you should be greeted with after a successful installation.

#

The final step is to change the ost-config.php (C:\inetpub\wwwroot\osTicket\include\ost-config.php) permissions back to “Read” only. 

#
![24](https://github.com/melisa-er/Configuring-IIS-and-Installing-Prerequisites/assets/157723219/ad5f0b86-3c83-40db-89c9-e7cd0bf7509e)

osTicket agent login URL: http://localhost/osTicket/scp/login.php 
- Help desk user accounts are called “agents” on osTicket.

![25](https://github.com/melisa-er/Configuring-IIS-and-Installing-Prerequisites/assets/157723219/a3c91d7d-e1b9-4238-af05-60d4551c3f93)

osTicket end user URL: http://localhost/osTicket/
