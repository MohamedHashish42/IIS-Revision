# Configuring SQL Server Authentication for Application Deployment 

SQL Server authentication is often preferred over Windows authentication when publishing an application for the following reasons:

1. **Cross-Platform Compatibility**: SQL Server authentication allows connections from non-Windows environments, which is essential for applications that might be accessed or hosted on different operating systems.

2. **Independent Access Control**:  SQL Server authentication lets you manage database access independently of Windows domain credentials. This is particularly useful when you need to grant access to users who aren't part of the domain.

3. **Consistent Credentials**: Using SQL Server authentication can provide a consistent set of credentials across different environments, making deployment more straightforward.


## Steps to To switch your application to use SQL Server authentication 
To switch your application to use SQL Server authentication instead of Windows authentication when publishing, follow these steps:

### First: Check and Enable SQL Server Authentication

1. Open SQL Server Management Studio (SSMS).
2. Connect to your SQL Server instance.
3. **Right-click on the server name** in Object Explorer and select **Properties**.
4. In the Server **Properties** window, go to the **Security** page.
5. Check the `Server authentication` section:
   - If `Windows Authentication mode` is selected, change it to `SQL Server and Windows Authentication mode`.
6. **Click `OK`** to save the changes.

### Second: Restart the SQL Server Service

After changing the authentication mode, **restart the SQL Server service** by   
- **Right-click on the server name** in SSMS Object Explorer, selecting **Restart**, and confirming.

### Third: Create a SQL Server Login

1. Open SQL Server Management Studio (SSMS).
2. Connect to your SQL Server instance.
3. Expand the `Security` folder in Object Explorer.
4. Right-click on `Logins` and select `New Login...`.
5. Enter the login name** under the `Login name` field.
6. Select `SQL Server authentication`**.
   - Enter a password for the login and confirm it.
   - Uncheck `Enforce password policy` if you do not want the password to expire or have complexity requirements.
7. **Map the login to the appropriate databases**:
   - Go to the `User Mapping` page.
   - Check the databases you want this login to access.
   - Assign the necessary roles (e.g., `db_datareader`, `db_datawriter`).
8. **Click `OK`** to create the login.


### Fourth: Test the Configuration

Finally, test your application with the updated connection string to ensure it connects successfully using SQL Server authentication.



