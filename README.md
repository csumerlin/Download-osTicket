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

This project was built in a **virtualized environment** to simulate a production Windows Server deployment.

### 1. Virtual Machine Creation
- **Hypervisor Used**: [Hyper-V / VirtualBox / VMware Workstation / Azure — choose one]
- **VM Specifications**:
  - Name: `osTicket-WinServer2025`
  - Generation: 2 (recommended for Windows Server 2025)
  - vCPU: 2–4 cores
  - RAM: 4–8 GB (Dynamic Memory enabled)
  - Hard Disk: 60–100 GB VHDX (dynamically expanding)
  - Network: External / Default Switch (for internet access during setup)

**Screenshots to include**:
- Hyper-V Manager → New Virtual Machine Wizard (name, memory, networking, disk, ISO selection)
- VM Settings summary

### 2. Installing Windows Server 2025
1. Download the official Windows Server 2025 ISO from the Microsoft Evaluation Center.
2. Boot the VM from the ISO.
3. Choose **Windows Server 2025 Datacenter (Desktop Experience)** during installation.
4. Complete initial setup:
   - Set administrator password.
   - Run Windows Update immediately after first login.
   - Configure static IP address (optional but recommended for consistency).

**Screenshots to include**:
- Installation media selection / boot screen
- OS selection (Desktop Experience)
- Post-install desktop with Server Manager open
- Windows Update status
- Network/IP configuration (`ipconfig` output)

### 3. Initial Server Configuration (Prerequisites)
Before installing IIS, PHP, or osTicket:
- Rename the server (e.g., `OSTICKET-SRV`).
- Join to a domain (optional — for this demo, it was left in Workgroup).
- Install latest Windows updates.
- Enable Remote Desktop (for easier management).

**Screenshots**:
- System Properties (computer name)
- Windows Update history
- `winver` command output

### 4. Key Software Prerequisites Installed
- **Visual C++ Redistributable** (2015–2022 x64) — required for PHP.
- **URL Rewrite Module** for IIS.
- **PHP Manager for IIS** (for easy PHP configuration).

**Screenshots**:
- Programs and Features list showing installed prerequisites.

---

**Notes**: 
- Total setup time for VM + base OS: ~45–60 minutes.
- All steps were performed on a fresh installation to ensure reproducibility.
