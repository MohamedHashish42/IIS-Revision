# Exercise 2
Publish a simple website on IIS by placing the site's folder `out of wwwroot` directory within IIS.

## **Solution**

Solution steps will be the same in [Exercise 1](./Examples/Hands-On-IIS/Exercise-1/Exercise-1-Solution.md) In addition to the following steps

### Ensure Proper Permissions

- Let’s assume your site folder is located at `D:\MyWebsite`.

1. **Set Permissions for IIS:**
   - Right-click on the `D:\MyWebsite` folder and select **Properties**.
   - Go to the **Security** tab and click on **Edit** to change permissions.
   - Click **Add** and type `IIS_IUSRS` into the object name box, then click **Check Names** and **OK**.
   - Select `IIS_IUSRS` from the list and check the box for **Read & execute** and **Read** permissions.
   - Click **Apply** and **OK**.

