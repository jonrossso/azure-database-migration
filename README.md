# Azure Database Migration Project

The goal of the entire project however is to undertake the design and implementation of a cloud-based database system on the Microsoft Azure platform, showcasing my expertise in cloud engineering. This project started off with setting up a GitHub repository (azure-database-migration562) and Azure environment. I connected to a Virtual Machine successfully through a windows remote desktop connection and created the production database. 

I have now progressed to successfully migrate the local database to Azure SQL Database, making use of Azure Data Studio. I had to carefully plan, execute and use validation dutring the migration process to ensure data integrity.

I have now secured the data with backups and established a development database to ensure that the production evironment's data integrity is not compromised during development/testing.

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

## Milestone 3: Migrate to Azure SQL Database

The focus of Milestone 3 was to transition the on-premise database to Azure by migrating it to an Azure SQL Database. This involved a series of tasks to ensure both the schema and data were successfully transferred, using Azure Data Studio.

### Task 1: Set Up Azure SQL Database

I started this task by creating an Azure SQL Database named "production-database". The associated SQL Server, "production-database-server.database.windows.net", was configured to use SQL Login for authentication. I also included by IP address to the firewall settings, to allow secure access.

### Task 2: Prepare for Migration

Azure Data Studio was installed and configured on the production Windows VM, to ensure a  connection to the existing on-premise / local database.

### Task 3: Connect to Azure SQL Database

Using Azure Data Studio, I established a connection to the newly created Azure SQL Database.

### Task 4: Schema Migration

Upon connecting to both databases, I installed the SQL Server Schema Compare extension n Azure Data Studio. This  allowed me to compare the schemas of the two databases. I then proceeded to migrate the schema from my local database to the Azure SQL Database without any issue.

### Task 5: Data Migration

With the schema successfully migrated, the next step was to move the data. I used the Azure SQL Migration extension to seamlessly handle the data transfer process.

### Task 6: Validate Migration Success

To verify the migration's success, I conducted a thorough validation of the data, schema, and configurations in the migrated Azure SQL Database to ensure data integrity and that all components were functioning as expected.

### Migrated Data (Example Query)

![Migrated Data](screenshots/migrated_production_database_sample_query_screenshot.png)

### Local Data (Example Query)

![Local Data](screenshots/local_database_sample_query_screenshot.png)

## Milestone 4: Data Backup and Restore

 The focus here was to ensure the safety of the data stored in the production database making use of the distinction between production and development environments. Now that I have created a development database, I can experiment changes without risking the integrity of the main production data.

### Task 1: Backup the On-Premise Database

A full backup of the production database, "production-database", was successfully created from the Windows VM, "production-vm". The backup file was stored securely at "C:\Program Files\Microsoft SQL Server\MSSQL16.MSSQLSERVER\MSSQL\Backup" on the VM.

### Task 2: Upload Backup to Blob Storage

An Azure Blob Storage account, "developmentstorage562", was configured to serve as the online repository for the database backups. The backup file was then uploaded to the Blob Storage container, "development-container-1".

### Task 3: Restore Database on Development Environment

A new Windows VM, "development-vm", was created to simulate the development environment. SQL Server was then installed and the backup from the production environment was restored onto this VM.

### Task 4: Automate Backups for Development Database

![Maintenance Plan Wizard for Weekly Backups](screenshots/maintenance_plan_wizard.png)

Within the development environment, SSMS was used to set up an automated weekly backup system by using a management task to perform weekly backups. These backups are stored at "https://developmentstorage562.blob.core.windows.net/development-container-1", ensuring that it could be restored at anytime necessary.