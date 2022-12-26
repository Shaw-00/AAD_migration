# Migrate SQL Server to an Azure SQL Managed Instance online by using Azure Data Studio with DMS
## Prequisites :- 
- Download and install SQL Server 2016 or later.

- Enable the TCP/IP protocol, which is disabled by default during SQL Server Express installation, by following the instructions in the article Enable or Disable a Server Network Protocol.

- Restore the AdventureWorks2016 database to the SQL Server instance.

- Create a Microsoft Azure Virtual Network for Azure Database Migration Service by using the Azure Resource Manager deployment model, which provides site-to-site connectivity to your on-premises source servers by using either ExpressRoute or VPN. Learn network topologies for SQL Managed Instance migrations using Azure Database Migration Service.

- Ensure that your virtual network Network Security Group rules don't block the outbound port 443 of ServiceTag for ServiceBus, Storage, and AzureMonitor.

- Configure your Windows Firewall for source database engine access.

- Open your Windows Firewall to allow Azure Database Migration Service to access the source SQL Server, which by default is TCP port 1433. If your default instance is listening on some other port, add that to the firewall.

- If you're running multiple named SQL Server instances using dynamic ports, you may wish to enable the SQL Browser Service and allow access to UDP port 1434 through your firewalls so that Azure Database Migration Service can connect to a named instance on your source server.

- If you're using a firewall appliance in front of your source databases, you may need to add firewall rules to allow Azure Database Migration Service to access the source database(s) for migration, as well as files via SMB port 445.

- Create a SQL Managed Instance by following the detail in the article Create a SQL Managed Instance in the Azure portal.

- Ensure that the logins used to connect the source SQL Server and target SQL Managed Instance are members of the sysadmin server role.

- Create a network share that Azure Database Migration Service can use to back up the source database.

- Ensure that the service account running the source SQL Server instance has write privileges on the network share that you created and that the computer account for the source server has read/write access to the same share.

- Make a note of a Windows user (and password) that has full control privilege on the network share that you previously created. Azure Database Migration Service impersonates the user credential to upload the backup files to Azure Storage container for restore operation.

- Create a blob container and retrieve its SAS URI by using the steps in the article Manage Azure Blob Storage resources with Storage Explorer, be sure to select all permissions (Read, Write, Delete, List) on the policy window while creating the SAS URI. This detail provides Azure Database Migration Service with access to your storage account container for uploading the backup files used for migrating databases to SQL Managed Instance.

## Register the resource provider
Register the Microsoft.DataMigration resource provider before you create your first instance of the Database Migration Service.

## Create an Azure Database Migration Service instance

## Create a migration project and Specify source details and target details

## Select logins and configure migration settings
