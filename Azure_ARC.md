# AAD_migration

## Set up Azure Active Directory authentication for SQL Server (1 hr)
Prequisite :- SQL Server is connected to Azure ARC

Azure Arc-enabled SQL Server
SQL Server on Arc-enabled servers brings all the Azure management capabilities to SQL Server environments running anywhere so customers can better manage, secure and govern their entire SQL estate. With Azure Arc-enabled SQL Server, customers can achieve improved cost efficiencies with a consumption-based billing model. Pay by the hour for spikes and ad-hoc usage and eliminate the need for a full upfront investment.

|   | Monthly Rate  | Hourly Rate |
| :------------ |:---------------:| -----:|
| Standard Edition      | $73 | $0.10 |
| Enterprise Edition      | $273.75        |   $0.375 |

	
		
		

For Authentication :- To perform Azure AD authentication, SQL Server needs to be able to query Azure AD and requires an Azure AD app registration, which it can authenticate as. The app registration also needs a handful of permissions for the queries SQL Server will perform.

## Create and register an Azure AD application and Grant application permissions (30 min)

## Grant application permissions (30 min)
Select Add a permission > Microsoft Graph > Application permissions

- Check Directory.Read.All
- Select Add permissions
- Select Add a permission > Microsoft Graph > Delegated permissions

- Check Application.Read.All
- Check Directory.AccessAsUser.All
- Check Group.Read.All
- Check User.Read.All
- Select Add permissions
- Select Grant admin consent

## Create and assign a certificate (1 hr)
To grant Admin consent to the permissions above, your account requires a role of Azure AD Global Administrator or Privileged Role Administrator.

## Configure Azure AD authentication for SQL Server through Azure portal (1 hr)
The Azure AD admin login is listed in sys.server_principals, but is not part of the sysadmin role. To grant the Azure AD admin the sysadmin role, use the sp_addsrvrolemember stored procedure.

Once the Azure AD admin login is granted the sysadmin role, changing the Azure AD admin in the Azure portal does not remove the previous login that remains as a sysadmin. To remove the login, it must be dropped manually.

The Azure AD admin change for the SQL Server instance takes place without a server restart, once the process is completed with the SQL Server's Azure Arc agent. For the new admin to display in sys.server_principals, the SQL Server instance must be restarted, and until then, the old admin is displayed. The current Azure AD admin can be checked in the Azure portal.
