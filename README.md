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
- Azure Portal - Create VM Basics tab
- Review + Create summary
- Deployment complete screen

### Connecting to the VM
- Connected via Remote Desktop using the public IP address.
- Changed administrator password and performed initial Windows Update.

**Screenshots**:
- RDP login screen
- Server Manager after first login
- Windows Update history

## Step 2: Initial Server Configuration
- Renamed computer to `OSTICKET-SRV`
- Installed latest Windows updates
- Installed Visual C++ Redistributable 2015-2022 (x64) — required for PHP
- Enabled Remote Desktop (already configured in Azure)

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
