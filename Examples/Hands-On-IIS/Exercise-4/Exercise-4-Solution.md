# Exercise 4
Publishing a .NET Core Application on IIS

## **Solution**

### Step 1: Prepare the .NET Core Application
1. **Create or Open Your .NET Core Application:**
   - Open Visual Studio.
   - Create a new **ASP.NET Core Web Application** project, or open an existing one.

2. **Publish the Application:**
   - Right-click on the project and select **Publish**.
   - Choose **Folder** as the target, and specify a path where you want the files to be published, e.g., `C:\Publish\MyNetCoreApp`.
   - Select **Configuration** as **Release**.
   - Click **Publish**.

### Step 2: Install and Configure IIS
1. **Enable IIS:**
   - Open **Control Panel** > **Programs** > **Turn Windows features on or off**.
   - Ensure that **Internet Information Services** is checked.
   - Click **OK** to install.

2. **Install the .NET Core Hosting Bundle:**
   - Download and install the [ASP.NET Core Hosting Bundle](https://dotnet.microsoft.com/download/dotnet) appropriate for your version of .NET Core.
   - This bundle includes the .NET Core runtime, libraries, and the IIS integration module.

### Step 3: Set Up the Application in IIS
1. **Create a New Website in IIS:**
   - Open **IIS Manager** (`inetmgr`).
   - Right-click on `Sites` in the left pane and select **Add Website**.
   - Configure the site:
     - **Site Name:** `MyNetCoreApp`
     - **Physical Path:** `C:\Publish\MyNetCoreApp`
     - **Binding:** Type `http`, IP Address `All Unassigned`, Port `80`, and no Host Name.
   - Click **OK** to create the website.

2. **Configure the Application Pool:**  
When publishing a .NET Core application on IIS, we Set the **.NET CLR Version** to **No Managed Code** because .NET Core applications run **out-of-process** using **Kestrel** web server, and **IIS** only acts as a **reverse proxy** to forward requests to the **Kestrel** web server.  
     To set the **.NET CLR Version** to **No Managed Code** in IIS, follow these steps:
      1. Open **IIS Manager**.
      2. In the **Connections** pane, expand the server node and click on **Application Pools**.
      3. In the **Application Pools** list, find the pool that your .NET Core app uses.
      4. Right-click on the application pool and select **Advanced Settings**.
      5. In the **Advanced Settings** window, under the **General** section, find **.NET CLR Version**.
      6. Set the **.NET CLR Version** to **No Managed Code** from the dropdown.
      7. Click **OK** to save the changes.

           
3. **Test the Application:**
   - Start the website by right-clicking on it and selecting **Manage Website** > **Start**.
   - Open a browser and navigate to `http://localhost`. Your .NET Core application should load.
  


### Step 4: Troubleshooting

1. **Check IIS Logs:**  
   - If your application doesn’t load, or you get errors, check the **IIS logs** located at `C:\inetpub\logs\LogFiles`. These logs can provide detailed error messages that may point to the issue.  

2. **Check the Event Viewer:**  
   - Open the **Windows Event Viewer** to check for ASP.NET Core-related errors. Under **Windows Logs > Application**. These events can help diagnose issues related to your application failing to start or execute correctly.






