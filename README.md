<p align="center">
<img src="https://i.imgur.com/Clzj7Xs.png" alt="osTicket logo"/>
</p>

<h1>osTicket Installation and Configuration on Windows Server 2025 (IIS)</h1>
This project demonstrates a complete installation of osTicket (open-source helpdesk/ticketing system) on Windows Server 2025 using IIS, PHP, and MariaDB/MySQL. Includes VM setup, prerequisites, configuration, and verification..<br />

<h2>Environments and Technologies Used</h2>

- Windows Server 2025
- Internet Information Services (IIS)
- PHP 8.2+ (NTS recommended for IIS)
- MariaDB or MySQL 8.0+
- PHP Manager for IIS
- osTicket v1.18.x

## Prerequisites & VM Setup

This project demonstrates a complete osTicket deployment in a realistic cloud environment using **Microsoft Azure**.

### 1. Azure Virtual Machine Creation
I created a new Windows Server 2025 VM in Microsoft Azure for this demonstration.

**VM Configuration**:
- **Subscription**: [Your Subscription Name]
- **Resource Group**: `osTicket-Project-RG` (new)
- **Virtual Machine Name**: `osticket-win2025`
- **Region**: [e.g., East US or closest to you]
- **Image**: Windows Server 2025 Datacenter (Desktop Experience)
- **Size**: Standard D2s_v5 (2 vCPU, 8 GiB memory) or larger
- **Authentication**: Password (admin username + strong password)
- **Inbound Ports**: RDP (3389) enabled for management
- **Disk**: 128 GB Premium SSD (OS disk)
- **Networking**: New virtual network with public IP

**Step-by-Step Process**:
1. Log into the [Azure Portal](https://portal.azure.com).
2. Search for **Virtual Machines** → Click **Create** → **Azure Virtual Machine**.
3. Fill in the **Basics** tab with the settings above.
4. In the **Networking** tab, allow RDP inbound.
5. Review + Create → Deploy.

**Screenshots to include**:
- Azure Portal "Create a virtual machine" Basics tab
- Review + Create summary page
- Deployment progress / "Go to resource" after deployment

### 2. Connecting to the VM & Initial Setup
1. Once deployed, connect via **RDP** using the public IP and admin credentials.
2. On first login:
   - Run **Windows Update** and install all available updates.
   - Rename the computer (e.g., `OSTICKET-SRV`).
   - Configure a static private IP (optional but recommended).
   - Install **Google Chrome** or Edge extensions for better productivity.

**Screenshots to include**:
- RDP connection screen / successful desktop login
- Server Manager opening on first boot
- Windows Update running
- System Properties showing computer name and Windows version (`winver`)

### 3. Key Prerequisites Installed
Before installing IIS/PHP/osTicket:
- **Microsoft Visual C++ Redistributable 2015-2022 (x64)**
- Latest Windows updates applied
- Remote Desktop enabled (already configured in Azure)

**Screenshots**:
- "Apps & features" list showing Visual C++ Redistributable
- `winver` showing Windows Server 2025

---

**Notes**:
- Total cost for this demo VM (a few hours): Very low (< $1).
- The VM was created fresh specifically for this project to match real-world cloud deployment scenarios.
- Azure provides easy scalability, automatic patching options, and built-in security features (NSGs, etc.).
