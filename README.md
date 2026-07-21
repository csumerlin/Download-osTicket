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

After the VM was successfully deployed, I connected to it using Remote Desktop Protocol (RDP).

### Actions Performed:
1. Downloaded the RDP file from the Azure Portal.
2. Connected to the VM using the administrator username and password set during creation.
3. On first login:
   - Changed the administrator password.
   - Ran Windows Update and installed all available updates.
   - Renamed the computer to `OSTICKET-SRV` for easier identification.
   - Installed Google Chrome for better browsing experience.

**Screenshots**:

**1. Connecting via RDP**  
![RDP Connection](screenshots/rdp-connection.png)

**2. Windows Server Desktop after Login**  
![Server Desktop](screenshots/server-desktop.png)

**3. Running Windows Update**  
![Windows Update](screenshots/windows-update.png)

**4. Computer Name Change**  
![Rename Computer](screenshots/rename-computer.png)

## Step 3: Installing IIS
- Used Server Manager → Add Roles and Features
- Installed **Web Server (IIS)** with **CGI** role service (required for PHP)
- Installed **URL Rewrite** module

**Screenshots**:
- Add Roles and Features wizard
- IIS Manager open

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
