# Azure Database Migration Project

This project has started off with setting up a GitHub repository (azure-database-migration562) and Azure environment. I have now connected to a Virtual Machine successfully through a windows remote desktop 
connection and created the production database. The goal of the entire project however is to undertake the design and implementation of a cloud-based database system on the Microsoft Azure platform, showcasing my expertise in cloud engineering.

## Milestone 1 and Milestone 2: Initial Setup / Configuration

### Azure Virtual Machine (VM) Deployment

- **VM Name:** production-vm
- **VM Size:** Standard Ds2 v3
- **VM vCPUs:** 2
- **VM RAM:** 8GB
- **Operating System:** Windows 11 Pro

### Establishment of Remote Desktop Connection

Utilising the RDP protocol, I have established a secure connection to the Azure VM via Microsoft Remote Desktop. This connection provides remote access for system management and configuration.

### Production Database Setup

To replicate a production-like scenario, I have downloaded the AdventureWorks backup file (AdventureWorks2022.bak), ensuring it resides in the backup "Program Files" location: C:\Program Files\Microsoft SQL Server\MSSQL16.SSQLSERVER\MSSQL\Backup\AdventureWorks2022.bak. 

Subsequently, I also successfully restored the AdventureWorks database on the Azure VM.

These milestones set the foundation of the rest of the project.
