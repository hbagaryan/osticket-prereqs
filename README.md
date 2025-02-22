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

- Microsoft Azure - Virtual Machine Setup
- osTicket System Configuration
- Install osTicket V1.15.8
  - Permission Assignments
  - Enable Key Extenstions

<h2>Installation Steps</h2>

<p>
<img src="https://i.imgur.com/wNAle21.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Deployed a Windows 10 Pro Virtual Machine in Microsoft Azure with 2 vCPUs, named osticket-vm, and configured user credentials (labuser / osTicketPassword1!). Successfully provisioned the VM and retrieved its public IP address from the Azure portal under the Networking section. Established a Remote Desktop Protocol (RDP) connection using the assigned credentials to access and manage the virtual environment.
</p>
<br />

<p>
<img src="https://i.imgur.com/k1QK8ia.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Configured the osticket-vm in Microsoft Azure to host the osTicket ticketing system. Downloaded and extracted the osTicket-Installation-Files.zip onto the desktop, creating the osTicket-Installation-Files directory for system setup. Installed and enabled Internet Information Services (IIS) with CGI support, ensuring the necessary web server environment for osTicket. Configured World Wide Web Services → Application Development Features → [X] CGI, enabling the required dependencies for osTicket deployment.
  
</p>
<img src="https://i.imgur.com/vzFpc4A.png"80%" width="80%" alt="Disk Sanitization Steps"/>  
</p>
<p>
Installed PHP Manager for IIS (PHPManagerForIIS_V1.5.0.msi) from the osTicket-Installation-Files folder to facilitate PHP configuration within Internet Information Services (IIS). This tool was used to manage PHP settings and streamline the integration of osTicket with IIS. Ensured proper PHP environment setup to support osTicket's functionality, optimizing server performance and compatibility.
</p>
<br />

<p>
<img src="https://i.imgur.com/VYTqWVC.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Installed the IIS Rewrite Module (rewrite_amd64_en-US.msi) from the osTicket-Installation-Files folder to enable URL rewriting and enhance web application functionality. This module was configured within Internet Information Services (IIS) to support osTicket’s URL structure and improve accessibility. Ensured proper integration with IIS, allowing for efficient request routing and enhanced application performance.
</p>
<br />

<p>
<img src="https://i.imgur.com/rSj3xj1.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<img src="https://i.imgur.com/k0rzmXx.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Created the C:\PHP directory to serve as the installation path for PHP on the osticket-vm. Extracted PHP 7.3.8 (php-7.3.8-nts-Win32-VC15-x86.zip) from the osTicket-Installation-Files folder into the C:\PHP directory to configure the PHP runtime environment. This setup ensured compatibility with IIS and osTicket, allowing the web application to process PHP scripts efficiently
</p>
<br />

<p>
<img src="https://i.imgur.com/OOtefEn.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Installed VC_redist.x86.exe from the osTicket-Installation-Files folder to provide the necessary Microsoft Visual C++ runtime libraries required for PHP and IIS functionality. This installation ensured compatibility between the PHP environment and Windows Server, preventing runtime errors and improving system stability. Proper integration of the Visual C++ Redistributable package was essential for the successful execution of osTicket on IIS.
</p>
<br />

<p>
<img src="https://i.imgur.com/9gNIoxl.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Installed MySQL 5.5.62 (mysql-5.5.62-win32.msi) from the osTicket-Installation-Files folder using the Typical Setup option to provide database support for osTicket. After installation, launched the MySQL Configuration Wizard and selected the Standard Configuration to optimize the database settings. Configured the root user credentials with Username: root and Password: root, ensuring administrative access for database management.
</p>
<br />

<p>
<img src="https://i.imgur.com/HjtdWM3.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Opened Internet Information Services (IIS) Manager as an administrator to configure the PHP environment for osTicket. Registered PHP within IIS using PHP Manager, setting the executable path to C:\PHP\php-cgi.exe to enable PHP script processing. Reloaded IIS by stopping and starting the server to apply the changes and ensure proper integration.
</p>
<br />

<p>
<img src="https://i.imgur.com/hhXzRB4.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Installed osTicket v1.15.8 by extracting osTicket-v1.15.8.zip from the osTicket-Installation-Files folder. Copied the upload folder into C:\inetpub\wwwroot, ensuring the web application was placed in the correct IIS directory. Renamed the upload folder to osTicket within C:\inetpub\wwwroot to establish the application’s root directory.
</p>
<br />

<p>
<img src="https://i.imgur.com/U57GrB2.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<img src="https://i.imgur.com/h0oJwPC.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Navigated to IIS Manager, accessed Sites → Default → osTicket, and clicked *“Browse :80” to verify the osTicket installation. Noted that some required PHP extensions were not enabled, affecting functionality. Returned to IIS Manager, accessed Sites → Default → osTicket, and opened PHP Manager to enable the necessary extensions: php_imap.dll, php_intl.dll, and php_opcache.dll. Refreshed the osTicket site in the browser to confirm the changes and ensure proper functionality. This project highlights IIS configuration, PHP extension management, and troubleshooting web application dependencies.
</p>
<br />

<p>
<img src="https://i.imgur.com/FO0g48y.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Renamed the osTicket configuration file to enable proper system functionality. Changed the filename from ost-sampleconfig.php (located in **C:\inetpub\wwwroot\osTicket\include**) to ost-config.php. This step was necessary for osTicket to recognize and apply the correct settings during installation.
</p>
<br />

<p>
<img src="https://i.imgur.com/OLpsDze.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Assigned the necessary permissions to ost-config.php to enhance security and ensure proper functionality. Disabled inheritance for the file by removing all inherited permissions. Added a new permission entry granting Everyone full access to ost-config.php, allowing the osTicket application to modify the configuration as needed.
</p>
<br />

<p>
<img src="https://i.imgur.com/2ruGQE9.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Continued the osTicket installation through the web browser by clicking "Continue", setting the Helpdesk Name, and configuring the default email to receive customer inquiries. Installed HeidiSQL from the osTicket-Installation-Files folder to manage the MySQL database. Opened HeidiSQL, created a new session using root/root credentials, and established a connection. Created a new database named "osTicket", preparing the system for data storage and management. This project demonstrates web application setup, database administration, and MySQL management for osTicket deployment.
</p>
<br />

<p>
<img src="https://i.imgur.com/6kkNncQ.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Completed the osTicket setup in the web browser by entering the MySQL database credentials. Configured the database settings with Database Name: osTicket, Username: root, and Password: root to establish a connection. Clicked “Install Now!” to finalize the installation and integrate osTicket with the MySQL database.
</p>
<br />

<p>
<img src="https://i.imgur.com/kJJvDZ6.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Successfully installed osTicket, ensuring there were no errors during the setup process. Verified the help desk login page by browsing to http://localhost/osTicket/scp/login.php, confirming administrative access. Checked the end-user portal by navigating to http://localhost/osTicket/ to ensure customers could submit support tickets.
</p>
<br />
