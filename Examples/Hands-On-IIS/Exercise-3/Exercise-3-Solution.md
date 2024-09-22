# Exercise 3
Publishing a .NET Framework Application on IIS

## **Solution**

### Step 1: Prepare the .NET Framework Application
1. **Create or Open Your .NET Framework Application:**
   - Open Visual Studio.
   - Create a new **ASP.NET Web Application (.NET Framework)** project, or open an existing one.

2. **Build the Application:**
   - Make sure your application is set to the **Release** configuration.
   - Right-click on the project in Solution Explorer and select **Build**.

3. **Publish the Application:**
   - Right-click on the project and select **Publish**.
   - Choose **Folder** as the target, and specify a path where you want the files to be published, e.g., `C:\Publish\MyNetApp`.
   - Click **Publish**.

### Step 2: Install and Configure IIS
 **Enable IIS and .NET Framework Features:**
   - Open **Control Panel** > **Programs** > **Turn Windows features on or off**.
   - Ensure that **Internet Information Services** and **ASP.NET** (version appropriate for your app) are checked.
   - Click **OK** to install.


### Step 3: Set Up the Application in IIS
1. **Create a New Website in IIS:**
   - Open **IIS Manager** (`inetmgr`).
   - Right-click on `Sites` in the left pane and select **Add Website**.
   - Configure the site:
     - **Site Name:** `MyNetApp`
     - **Physical Path:** `C:\Publish\MyNetApp`
     - **Binding:** Type `http`, IP Address `All Unassigned`, Port `80`, and no Host Name.
   - Click **OK** to create the website.

2. **Configure the Application Pool:**
   - Go to the **Application Pools** node in IIS Manager.
   - Find the pool associated with your site (e.g., `MyNetApp`).
   - Ensure the **.NET CLR Version** is set to the appropriate .NET Framework version.

3. **Test the Application:**
   - Start the website by right-clicking on it and selecting **Manage Website** > **Start**.
   - Open a browser and navigate to `http://localhost`. Your .NET Framework application should load.
  

### Step 4: Troubleshooting

1. **Check IIS Logs:**  
   - If your application doesn’t load, or you get errors, check the **IIS logs** located at `C:\inetpub\logs\LogFiles`. These logs can provide detailed error messages that may point to the issue.  

2. **Check the Event Viewer:**  
   - Open the **Windows Event Viewer**. Under **Windows Logs > Application**, look for any .NET Framework-related errors. These events can help diagnose issues related to your application failing to start or execute correctly.  

