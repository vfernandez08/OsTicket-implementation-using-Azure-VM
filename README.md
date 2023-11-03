# Project: Implementing a Help Desk Ticketing System (osTicket) using Azure Virtual Machines

## Environments and Technologies Used

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Internet Information Services (IIS)

## Operating Systems Used

- Windows 10 (21H2)


## Installation Steps

1. **Create a Windows 10 Virtual Machine**
   - Create a Windows 10 Virtual Machine with 2 or 4 virtual CPUs to ensure a smooth experience.

![Image of VM Settings](https://i.imgur.com/azaZ1vP.png)

   - Ensure that you check the box recognizing 'I confirm I have an eligible Windows 10/11 license with multi-tenant hosting rights,' or else you will receive a validation error message when you choose to 'Review + Create.'

![Image of user_name](https://i.imgur.com/TIYI7SJ.png)




2. **Connect to Your Virtual Machine**
   - To connect to your Virtual Machine, search for 'Remote Desktop Connection' on your local machine and copy and paste the public IP address into the provided space. Then press the Connect button.

   ![Public IP Address](https://i.imgur.com/AynhMxF.png)

3. **Install Internet Information Services (IIS)**
   - Once connected, install IIS by searching for the Control Panel and selecting 'Turn Windows features on or off.' Enable 'Internet Information Services' (IIS) from the available services.
     ![IIS1](https://i.imgur.com/0ulHd8J.png)
     ![IIS](https://i.imgur.com/JGonrCG.png)


4. **Install Web Platform Installer (WebPI)**
   - Download and install Web Platform Installer (WebPI), a tool that simplifies the installation workflow for web applications and platform technologies.

   ![Download WebPI](https://i.imgur.com/mMHrT25.png)

5. **Add MySQL 5.5 Database and PHP**
   - Using WebPI, add MySQL 5.5 database, PHP 5.6.31, and various versions of PHP (x86) 7.0 to 7.3.

   ![Add MySQL](https://i.imgur.com/PglqxBp.png)
   ![Install PHP](https://i.imgur.com/rnj8f1e.png)
   ![Password Request](https://i.imgur.com/PFjLBuw.png)

6. **Fix Any Failures**
   - If necessary, fix any installation failures by downloading and installing PHP 7.3.8, PHP Manager, and Microsoft Visual C++ 2009 Redistributable Package from the provided files. [Link to Google Drive Folder](https://drive.google.com/drive/u/0/folders/1APMfNyfNzcxZC6EzdaNfdZsUwxWYChf6)


7. **Extract and Configure osTicket**
   - Download and extract the osTicket files. Copy the "upload" folder to c:\inetpub\wwwroot and rename it to "osTicket."

   ![Extracted osTicket Files](https://i.imgur.com/pJEIG0t.png)

8. **Restart IIS**
   - In IIS, restart the server by going to sites -> Default -> osTicket and clicking Browse *:80.

   ![IIS Restart](https://i.imgur.com/JobuMH8.png)
   ![osTicket Installer](https://i.imgur.com/9wdYmQa.png)

   -Once browse: 80 is selected a browser window will open presenting osTicket installer page along with the recommendation/prerequisites of use.

   ![Prerequisites](https://i.imgur.com/HNJPOlM.png)

## Configuring PHP Extensions and File Permissions

1. Return to IIS.

2. Navigate to the **Default** site in your osTicket installation.

3. Double-click on **PHP Manager**.

4. In PHP Manager, select **Enable or disable an extension**.

5. Enable the following PHP extensions:
   - `php_imap.dll`
   - `php_intl.dll`
   - `php_opcache.dll`.
   ![PHP Extension Enabled](https://i.imgur.com/k4DGxEh.png)
   ![PHP Extension Enabled2](https://imgur.com/MGq7gF1.png)
   
7. After enabling the PHP extensions, refresh your osTicket site in your web browser to see the changes.

   ![Refreshed osTicket Installer](https://imgur.com/TkS03E0.png)

8. Rename the configuration file:
   - From: `C:\inetpub\wwwroot\osTicket\include\ost-sampleconfig.php`
   - To: `C:\inetpub\wwwroot\osTicket\include\ost-config.php`.

   ![Rename Configuration File](https://imgur.com/dex3lcq.png)
   
   ![Rename Configuration File](https://imgur.com/DJqYwVy.png)

10. Assign Permissions to `ost-config.php`:

   - Right-click on `ost-config.php` and select 'properties.'
   - In the 'Security' tab, select 'Advanced.'

   ![Properties Selection](https://imgur.com/oVHq2Xk.png)
  

11. In the 'Advanced' settings:

   - Disable inheritance and remove all inherited permissions.
   - Add new permissions for everyone and grant 'Full Control.'
     ![Disable Inheritance](https://imgur.com/JbSjGaD.png)
   ![Remove All Inherited](https://imgur.com/eVe4Y1a.png)
   ![Add Permissions for Everyone](https://imgur.com/sVjhTdj.png)

12. Return to the browser window with the osTicket installer and press 'Continue.' You will now see the form to complete before continuing.

   ![osTicket Form](https://imgur.com/MUhOuca.png)


## Configure Database in HeidiSQL

1. **Download and Install HeidiSQL**:
   - Obtain HeidiSQL from Google Drive using the default installation settings provided in the installer.
   - [Link to Google Drive Folder](https://drive.google.com/drive/u/0/folders/1APMfNyfNzcxZC6EzdaNfdZsUwxWYChf6)

   ![HeidiSQL Installation](https://i.imgur.com/Mx5tzuT.png)

2. **Creating a Database Session in HeidiSQL**:

   - Open HeidiSQL and create a new session with the following credentials:
     - Username: root
     - Password: Password1

   ![Create HeidiSQL Session](https://i.imgur.com/llWGdUk.png)

3. **Connect and Create the "osTicket" Database**:

   - Connect to the session, and within HeidiSQL, create a new database named "osTicket."

   ![Create Database in HeidiSQL](https://i.imgur.com/IK0AQzQ.png)

      ![Create Database in HeidiSQL](https://i.imgur.com/YFfWb6S.png)

5. **Entering Database Details into osTicket Installer**:

   - With the "osTicket" database now created, you'll need to provide these details in the osTicket Installer:
     - MySQL Username: root
     - MySQL Password: Password1


6. **Complete Installation**:

   - Click the "Install Now!" button to initiate the installation process. We hope that it proceeds without any errors.

   ![osTicket Installer Database Details](https://i.imgur.com/wfCaOa2.png)

## Accessing the osTicket User Interfaces

After successfully installing osTicket, you can access the following interfaces:

- **Admin Login for osTicket**:
  - This link takes you to the administrative control panel, known as the "Staff Control Panel."

   ![Admin Login for osTicket](https://i.imgur.com/rNqcQAZ.jpg)

- **End User Portal**:
  - "Your osTicket URL" directs users to the End User Portal. Here, customers can submit their support tickets for assistance from your help desk.

   ![End User Login Page](https://i.imgur.com/hOd3UiS.png)

## Cleanup

1. **Delete the Setup Folder**:
   - Remove the 'C:\inetpub\wwwroot\osTicket\setup' directory.

  ![Read-Only Permissions for ost-config.php](https://i.imgur.com/6QYkpFf.png)

   

2. **Set Permissions to "Read" Only**:
   - To enhance security, right-click on 'ost-config.php,' go to properties, and set the permissions to "Read" only. Ensure you disable inheritance and remove all inherited permissions.
  
 ![Accessing the osTicket Admin Panel](https://i.imgur.com/OApncw3.png)


3. **Access the osTicket Admin Panel**:
   - To complete the cleanup, access the osTicket Admin Panel at [http://localhost/osTicket/scp/login.php](http://localhost/osTicket/scp/login.php).

  
   ![Accessing the osTicket Admin Panel](https://i.imgur.com/wUMJ8N8.png)
