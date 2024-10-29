<p align="center">
<img src="https://i.imgur.com/Clzj7Xs.png" alt="osTicket logo"/>
</p>

<h1>osTicket - Prerequisites and Installation</h1>
This tutorial outlines the prerequisites and installation of osTicket.<br />


<h2>What is osticket?</h2>

osTicket is a free Help Desk ticketing sytem used to steamline customer support service. Many businesses operate with osTicket as it's widely trusted.

<h2>Why a Virtual Machine?</h2>

We are using a Virtual Machine in this project so those with personal devices can participate without having to delete unwanted files after completion. As well as giving MAC users the same experience within the project.

<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines)
- Remote Desktop
- Internet Information Services (IIS)

<h2>Operating Systems Used </h2>

- Windows 10</b> (21H2) (Virtual Machine within Azure)

<h2>List of Prerequisites</h2>

- Enable Internet Information Services (IIS)
- Install PHP Manager for IIS
- Install PHP 7.3.8
- Install VC_redist.x86.exe.
- Install MySQL 5.5.62
- Install HeidiSQL
  
All download links were provided by [Joshmadakor1](https://github.com/joshmadakor1) 😎

<h2>Installation Steps</h2>

<p>
<img src="https://i.imgur.com/GgiQvM3.png"/>
</p>
<p>
</h2> Virtual Machine </h2>

- Log Into Microsoft Azure and create a Windows 10 (21h2) Virtual Machine with a recommended 4 vcpus at least. Make sure a Virtual Network is being made along side the VM. Its unnecessary to configure with the rest of the settings, If you are unfimiliar with Azure, refer to my [Microsoft Azure: Vitual MAchine](https://github.com/GGeeto/Microsoft-Azure-Creating-a-Virtual-Machine/blob/main/README.md) repository. 
- Connect to the Virtual Machine via remote desktop  
</p>
<br />

<p>
<img src="https://imgur.com/cyuu43o.png"
</p>
<p>
</h2> Enable Windows Features </h2>

- Head staright to control panel then to the programs settings within control panel.
- Under Programs and features, click Turn Windows features on and off with the admin icon next to it.
- Find the Internet Information Services folder then check the box and expand it.
- Then expand World Wide Web services
- Within WWWS expand Application Development Features folder and check the folder labled CGI.
- Then expand the Common HTTP Features folder within the IIS folder. Every folder within this folder needs to be checked.
- Click OK on the bottom right and wait for the programs to be installed.
</p>
<br />

<p>
<img src="https://i.imgur.com/5Ja3Kp1.png"/>
</p>
<p>
</h2> Lots of Downloads </h2>

- Download and Install [PHP Manager for IIS](https://drive.google.com/file/d/1RHsNd4eWIOwaNpj3JW4vzzmzNUH86wY_/view?usp=share_link)
- Download and Install [RewriteModule ](https://drive.google.com/file/d/1tIK9GZBKj1JyUP87eewxgdNqn9pZmVmY/view?usp=share_link)
- Download [PHP 7.3.8](https://drive.google.com/file/d/1snNMtLdCOpMtkCyD4mvl9yOOmvVIp9fP/view?usp=share_link)
- Create a folder in Windows(C:) drive and name it PHP. Drag [PHP 7.3.8] into that folder and unzip the contents
- Download and Install [VC_redist.x86.exe.](https://drive.google.com/file/d/1s1OsGF3-ioO0_9LYizPRiVuIkb3lFJgH/view?usp=share_link)
- Download [MySQL 5.5.62](https://drive.google.com/file/d/1_OWh9p7VQLcrB0q_V7qT8yHl0xo5gv7z/view?usp=share_link)
- Install as typical set up and launch the Configuration wizard. Click standard configuration and click next untile you get to the security options. Create a password. Click next and then Execute.
</p>
<br />

<p>
<img src="https://i.imgur.com/zR7i3GN.png"/>
</p>
<p>
</h2> Register new PHP Version </h2>

- Open Internet Information Services Manager as an admin
- Open PHP Manager then click Register new PHP version
- Click the three dots then open the PHP folder we made earlier
- Click php-cgi and open
- Return to the IIS Manager home page and Below Manage Server click Restart. Close the application
</p>
<br />

<p>
<img src="https://imgur.com/VDf20UG.png"/>
</p>
<p>
</h2> Downloading osTicket </h2>

- Install [osTicket-v1.15.8](https://drive.google.com/file/d/1VeVXKlzHDRjeaVUL99ptq7qYbrbXdFxJ/view?usp=drive_link)
- Open the zip file within file explorer and extract the upload folder and copy it into c:\inetpub\wwwroot
- Rename the folder you copied to osTicket
</p>
<br />

<p>
<img src="https://imgur.com/9eGeJWp.png"/>
</p>
<p>
</h2> Enabling osTicket Features </h2>

- Reopen IIS Manager and restart the server
- Open PHP Manager and at the bottom of the page click Enable or disable an extension
- Enable: php_imap.dll
- Enable: php_intl.dll
- Enable: php_opcache.dll
</p>
<br />

<p>
<img src="https://imgur.com/NmMzq8b.png"/>
</p>
<p>
</h2> Disabling security for Config file </h2>

- Open file explorer and find the C:\inetpub\wwwroot\osTicket\include\ost-sampleconfig.php file
- Rename the file from ost-sampleconfig to ost-fonfig essentially just removing "sample" from the name
- Open the properties of the file, head to security and then advanced
- Click disable inheritance and then remove all permissions
- In the same security page click add then select a principal
- Type everyone is the object name and click check names then OK
- Check the Full Control box and click OK
- Click Apply then OK
</p>
<br />

<p>
<img src="https://i.imgur.com/CaqKPQc.png"/>
</p>
<p>
</h2> Installing HeidiSQL </h2>

- Download and Install [HeidiSQL](https://docs.google.com/document/d/1WovrX2DaS9xkfaSr4LXyB4YnnWpXIgPCMMbbfgHmGVw/edit)
- Launch and click new, keep this user as root and enter the password you created during the Configuration of MySQL then click open
- Then Right click the Database 'Unamed'. Then Create new and click database.
- Name it osTicket, click OK
  </p>
<br />

<p>
<img src="https://i.imgur.com/RUwoZeK.png"/>
</p>
<p>
</h2> Creating osTicket Account </h2>

- Head back to IIS Manager and under Connections you want to expand until you see the osTicket folder. 
- Open it and under Browse Folder click Browse *.80 (http)
- If you are following this project as an expiriment, the System settings and Admin user information can be random. Just make sure to remember what you have entered.
- Under Database settings Enter osTicket as the MySQLDatabase
- Enter root as the Username
- Enter the password you created during the configuration of MySQL
- Click Install Now
  </p>
<br />

<p>
<img src="https://i.imgur.com/eCEsLBx.png"/>
</p>
<p>
</h2> Clean up </h2>

- Reopen File explorer and delete C:\inetpub\wwwroot\osTicket\setup
- Go to C:\inetpub\wwwroot\osTicket\include\ost-config.php and set the security permissions back to read only
  </p>
<br />

<p>
<img src="https://imgur.com/nHqgAYG.png"/>
</p>
<p>
</h2> Logging into osTicket </h2>

- Go to the [osTicket Login Page](http://localhost/osTicket/scp/login.php)
- Login using the information you entered when creating the account
- You're in! Good Job!
