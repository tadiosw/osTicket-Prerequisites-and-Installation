<p align="center">
<img src="https://i.imgur.com/Clzj7Xs.png" alt="osTicket logo"/>
</p>

<h1>osTicket - Prerequisites and Installation</h1>
This guide walks you through the prerequisites and installation process of osTicket, an open-source help desk ticketing system.<br />

<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Microsoft Remote Desktop (RDP)
- Internet Information Services (IIS)

<h2>Operating Systems Used</h2>

- Windows 10  

<h2>Prerequisites</h2>

- An Azure Virtual Machine  
- osTicket installation files  
- HeidiSQL  

<h2>Installation Steps</h2>

<p>
To get started, create a Virtual Machine (VM) through the Microsoft Azure portal (portal.azure.com). We are using a VM as it provides an isolated environment, ensuring our physical system remains unaffected in case of errors. Additionally, a VM allows easy replication of this lab.  
</p>
<p>
Create a new resource group and name it "osTicket". Then, set up a VM with 2-4 CPUs (this example uses 4 CPUs).  
</p>

<img src="https://i.imgur.com/yqk0lmM.png" height="80%" width="80%" alt="Creating a Virtual Machine"/>

<br />

<p>
Once your VM is ready, connect to it using Remote Desktop Protocol (RDP). Use the public IPv4 address provided in Azure.  
</p>
<p>
If you're using a Mac, you'll need to install Microsoft Remote Desktop to connect.  
</p>

<img src="https://i.imgur.com/uLVKzxS.png" height="80%" width="80%" alt="Connecting via RDP"/>

<br />

<p>
Now that you're connected, the next step is to enable Internet Information Services (IIS).  
</p>
<p>
Open the **Control Panel**, then select **Uninstall a Program**. On the left side, click **Turn Windows features on or off**, then enable **Internet Information Services (IIS)**.  
</p>

<img src="https://i.imgur.com/qtEnuWu.png" height="80%" width="80%" alt="Enabling IIS"/>

<br />

<p>
With IIS enabled, we now need to install the Web Platform Installer. Use the following link to download the required installation files:  
<a href="https://drive.google.com/drive/u/0/folders/1APMfNyfNzcxZC6EzdaNfdZsUwxWYChf6">Download Here</a>  
</p>
<p>
Once downloaded, install the **Web Platform Installer**.  
</p>

<img src="https://i.imgur.com/AxHCfQ6.png" height="80%" width="80%" alt="Installing Web Platform Installer"/>

<p>
After installing the Web Platform Installer, open it and install **MySQL 5.5**.  
</p>
<p>
Next, install the **x86 version of PHP up to 7.3**. Some files, such as the C++ Redistributable package, PHP 7.3.8, and PHP Manager for IIS, might not install automatically. These can be downloaded from the provided link.  
</p>

<img src="https://i.imgur.com/JJ8bZeJ.png" height="80%" width="80%" alt="Installing MySQL and PHP"/>

<p>
Now, download the osTicket installation package and extract it.  
</p>
<p>
Copy the "upload" folder to **C:\inetpub\wwwroot** and rename it to **osTicket**.  
</p>

<img src="https://i.imgur.com/TUGiSKi.png" height="80%" width="80%" alt="Copying osTicket Files"/>

<br />

<p>
Open **IIS Manager** and restart the server.  
</p>
<p>
In IIS Manager, navigate to **Sites → Default → osTicket**, then on the right-hand side, click **Browse *.80**. This will launch the osTicket setup page in your browser.  
</p>

<img src="https://i.imgur.com/4AkTkV0.png" height="80%" width="80%" alt="Opening osTicket in Browser"/>

<br />

<p>
To enable essential PHP extensions, go back into IIS Manager.  
</p>
<p>
Navigate to **Sites → Default → osTicket**, then double-click on **PHP Manager**. Click **Enable or disable an extension** and enable **php_intl.dll** and **php_opcache.dll**. After making these changes, refresh the osTicket setup page and verify that the "Intl Extension" is now enabled.  
</p>

<img src="https://i.imgur.com/APZgUTT.png" height="80%" width="80%" alt="Enabling PHP Extensions"/>

<br />

<p>
Next, go to **C:\inetpub\wwwroot\osTicket\include\** and rename **ost-sampleconfig.php** to **ost-config.php**.  
</p>
<p>
Adjust the permissions of **ost-config.php** by disabling inheritance and removing all existing permissions. Then, assign **full control** permissions to **Everyone**.  
</p>

<img src="https://i.imgur.com/1nYaYGe.png" height="80%" width="80%" alt="Configuring File Permissions"/>

<br />

<p>
Proceed with the osTicket setup in your browser. Enter a name for your help desk and specify a default email address to receive ticket notifications.  
</p>

<img src="https://i.imgur.com/RmVk3q5.png" height="80%" width="80%" alt="Configuring osTicket Helpdesk"/>

<br />

<p>
Finalize the setup by entering your database credentials:  
</p>
<ul>
  <li>MySQL Database: <strong>osTicket</strong></li>
  <li>MySQL Username: <strong>root</strong></li>
  <li>MySQL Password: <strong>Password1</strong></li>
</ul>
<p>
Click **Install Now!** to complete the installation. If everything is configured correctly, osTicket should install without errors.  
</p>

<p>
### Final Cleanup  
</p>
<ul>
  <li>Delete: **C:\inetpub\wwwroot\osTicket\setup**</li>
  <li>Set **ost-config.php** to **Read-Only**</li>
  <li>Log in to the osTicket Admin Panel: <a href="http://localhost/osTicket/scp/login.php">osTicket Admin Login</a></li>
</ul>

<p>
Congratulations! 🎉 Your osTicket system is now successfully installed and ready to use.
</p>


