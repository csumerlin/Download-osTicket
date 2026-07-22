# Deploying osTicket on Microsoft Azure (Windows Server 2025)

This project demonstrates a **complete end-to-end deployment** of osTicket (open-source helpdesk/ticketing system) on Microsoft Azure using Windows Server 2025, IIS, PHP, and MariaDB.

## Project Overview
- **Platform**: Microsoft Azure
- **Operating System**: Windows Server 2025 Datacenter (Desktop Experience)
- **Web Server**: Internet Information Services (IIS)
- **Purpose**: To showcase cloud deployment skills, proper server configuration, and a fully functional helpdesk system.

## Environments and Technologies Used
- **Cloud Platform**: Microsoft Azure (Free Trial)
- **Virtual Machine**: Windows Server 2025 Datacenter
- **Web Server**: IIS 10
- **Runtime**: PHP 8.2+ (Non-Thread Safe)
- **Database**: MariaDB 10.11 or MySQL 8.0+
- **Management Tool**: PHP Manager for IIS
- **osTicket Version**: v1.18.x (latest)

## Architecture
- Azure VM with public IP (RDP access)
- IIS hosting osTicket web application
- MariaDB running on the same VM
- All components installed and configured manually for learning purposes

## Step 1: Creating the Azure Virtual Machine

1. Logged into the [Azure Portal](https://portal.azure.com) using a Free Trial account.
2. Created a new Resource Group: `osTicket-Project-RG`
3. Created a Windows Server 2025 VM with the following settings:
   - Name: `osticket-win2025`
   - Region: [Your Region, e.g. East US]
   - Image: Datacenter for Windows Server 2025 - x64 Gen2
   - Size: Standard D2s_v3 (2 vCPU, 8 GiB RAM)
   - Authentication: Password (Admin username + strong password)
   - Inbound Ports: RDP (3389)

**Screenshots**:

**1. Creating the Resource Group**  
![Create Resource Group](screenshots/Create%20RG.png)

**2. Create VM Basics Tab**  
![Create VM Basics](screenshots/Azure%20Portal%20-%20Create%20VM%20Basics%20tab.png)

**3. Review + Create Summary**  
![Review + Create](screenshots/Review%20+%20Create%20summary.png)

**4. Deployment Complete**  
![Deployment Complete](screenshots/Deployment%20complete%20screen.png)

## Step 2: Connecting to the VM & Initial Setup

After deployment, I connected to the Windows Server 2025 VM.

### Connection Process:
1. In Azure Portal → VM Overview → Clicked **Connect** → **RDP** → Downloaded the RDP file.
2. Opened the `.rdp` file and logged in with the admin credentials.

### Initial Configuration in Server Manager:
- Opened **Server Manager** (it launches automatically on login).
- Installed latest **Windows Updates**.
- Renamed the computer from the default to `OSTICKET-SRV`.
- Checked the dashboard for any warnings or configuration tasks.

**Screenshots**:

**1. Downloading RDP File**  
![Downloading RDP File](screenshots/Download%20the%20RDP%20file.png)

**2. RDP Connection Screen**  
![RDP Connection Screen](screenshots/RDP%20Connection%20Screen.png)

**3. Server Manager Dashboard**  
![Server Manager Dashboard](screenshots/Server%20Manager%20Dashboard.PNG)

**4. Running Windows Update**  
![Windows Update](screenshots/Windows%20Update.PNG)

**5. Renaming the Computer**  
![Rename Computer](screenshots/Rename%20Computer.PNG)

## Step 3: Installing IIS

With the server updated and configured, I installed Internet Information Services (IIS), the web server required to host osTicket.

### Installation Steps:
1. Opened **Server Manager**.
2. Clicked **Add Roles and Features**.
3. Selected **Web Server (IIS)** role.
4. Included the **CGI** role service (required for PHP).
5. Installed **URL Rewrite** module (for clean URLs).
6. Verified IIS was running by browsing to `http://localhost`.

**Screenshots**:

**Add Roles and Features Wizard**  
![Add Roles and Features](screenshots/add-roles-iis.png)

**Selecting Web Server (IIS)**  
![Web Server IIS](screenshots/web-server-iis.png)

**IIS Manager After Installation**  
![IIS Manager](screenshots/iis-manager.png)

**Default IIS Welcome Page**  
![IIS Welcome](screenshots/iis-welcome-page.png)

## Step 4: Installing PHP
- Downloaded PHP 8.2+ Non-Thread Safe (NTS) x64 from windows.php.net
- Extracted to `C:\PHP`
- Installed PHP Manager for IIS
- Registered PHP with IIS and enabled required extensions (`gd`, `imap`, `intl`, `mbstring`, `mysqli`, `opcache`, etc.)

**Screenshots**:
- PHP Manager interface
- `phpinfo()` test page

## Step 5: Installing MariaDB / MySQL
- Installed MariaDB 10.11
- Created root password
- Created database `osticket` and dedicated user

**Screenshots**:
- MariaDB installation
- Database creation (via HeidiSQL or command line)

## Step 6: Deploying osTicket
- Downloaded latest osTicket release from GitHub
- Extracted `upload` folder contents to `C:\inetpub\wwwroot\osticket`
- Renamed `ost-sampleconfig.php` → `ost-config.php`
- Set proper permissions on the config file

## Step 7: Running the osTicket Web Installer
- Browsed to `http://localhost/osticket` (or public IP)
- Completed the web-based installer:
  - Database configuration
  - Admin user creation
  - System settings
- Removed the `/setup/` folder for security

**Screenshots**:
- osTicket installer welcome screen
- Database settings page
- Successful installation confirmation
- osTicket Admin Dashboard

## Step 8: Testing & Verification
- Created test tickets as a user and agent
- Verified email piping potential and basic functionality
- Confirmed the system is accessible via public IP

**Screenshots**:
- Agent dashboard
- Sample ticket creation

## Cost Summary (Free Trial)
- VM runtime cost was minimal and covered under Azure Free Trial credits.
- After completion, the VM was **deallocated** to avoid charges.

## Conclusion & Lessons Learned
- Successfully deployed a production-ready helpdesk system in the cloud.
- Gained hands-on experience with Azure VM provisioning, Windows Server administration, IIS + PHP configuration, and osTicket setup.
- Key takeaway: Proper planning of VM sizing, security groups, and post-deployment configuration is critical.

---

**Repository Contents**
- This README with full documentation
- Screenshots folder (all steps documented)
- Any configuration files (optional)
