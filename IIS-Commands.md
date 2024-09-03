# IIS Commands

To manage Internet Information Services (IIS) on a web server using Command Prompt (CMD), you can use the following commands:

**Note**  
some commands need to run on this directory `C:\Windows\System32\inetsrv` so you can use one of the following options:
  1. Navigate to the directory `C:\Windows\System32\inetsrv` using command `cd C:\Windows\System32\inetsrv`
  2. Add directory `C:\Windows\System32\inetsrv` to your system's PATH environment variable

## Commands

1. **Start, Stop, Restart IIS:**

   - **Start IIS:**
     ```cmd
     iisreset /start
     ```
   - **Stop IIS:**
     ```cmd
     iisreset /stop
     ```
   - **Restart IIS:**
     ```cmd
     iisreset /restart  
     ```
     or
     ```cmd
     iisreset   
     ```


2. **List, Create, Delete Sites:**

   - **List Sites:**
     ```cmd
     appcmd list site
     ```

   - **Create Sites:**
     ```cmd
     appcmd add site /name:"NewSiteName" /bindings:"http/*:80:" /physicalPath:"C:\inetpub\wwwroot\NewSite"
     ```

   - **Delete Sites:**
     ```cmd
     appcmd delete site /site.name:"SiteName"
     ```



3. **Start, Stop a Specific Site:**

   - **Start a site:**
     ```cmd
     appcmd start site /site.name:"SiteName"
     ```
   - **Stop a site:**
     ```cmd
     appcmd stop site /site.name:"SiteName"
     ```

4. **list, Start, Stop, or Recycle a Specific application pool:**

   - **List Application Pools:**
     ```cmd
     appcmd list apppool
     ```

   - **Start an application pool:**
     ```cmd
     appcmd start apppool /apppool.name:"AppPoolName"
     ```
   - **Stop an application pool:**
     ```cmd
     appcmd stop apppool /apppool.name:"AppPoolName"
     ```
   - **Recycle an application pool:**
     ```cmd
     appcmd recycle apppool /apppool.name:"AppPoolName"
     ```


5. **Backup and Restore IIS Configuration:**

   - **Backup IIS configuration:**
     ```cmd
     appcmd add backup "MyBackup"
     ```
   - **Restore IIS configuration from backup:**
     ```cmd
     appcmd restore backup "MyBackup"
     ```

  

These commands are essential for managing IIS on a web server directly through the Command Prompt.