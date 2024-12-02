# OpenVPN Server on Azure

Before starting, ensure you have the following:
- An **Azure account** with the ability to create virtual machines.
- OpenVPN client software installed on your devices.


## Steps

## 1. Create an Azure Virtual Machine
- Log in to the Azure portal and navigate to **Create a resource**.
  ![image](images/1.png)

- Under **Virtual Machines**, click **Create**  

  ![image](images/2.png)

- Name your **Virtual Machine**

  ![image](images/3.png)

- Select the region you would like your server to be located

  ![image](images/4.png)

- Select **'See all images'** and search for **'openvpn'** then select **'OpenVPN Access Server - x64 Gen 1'**

  ![image](images/5.png)
  ![image](images/6.png)

> [!IMPORTANT]
> Make sure your security type is set to **'Standard'** as OpenVPN is not compatible with Trusted Launch VM because this feature uses enhanced security measures, such as secure boot and vTPM, which may conflict with the OpenVPN setup process.
  ![image](images/7.png)

- Select **Standard_B1s** as it is part of Azure's free tier and provides sufficient resources for running an OpenVPN server.

  ![image](images/8.png)

- Select **'Password'** as the authentication type and enter the credentials you want to use; these will be required to SSH into your server later.

  ![image](images/9.png)

- Click **'Review + Create'**, wait for the validation process to complete, and allow sufficient time for your virtual machine to start up after deployment.

  ![image](images/14.png)
  
  ![image](images/15.png)

- Once the deployment is complete, click **'Go to Resource'** and use the **'Connect'** option to access your instance.
  
  ![image](images/16.png)
  ![image](images/17.png)

- This will display your server's IP address and the admin username, which you will use to SSH into your server.
  
  ![image](images/18.png)

## 2. SSH into your Virtual Machine

- Use these credentials to SSH into your server.

```bash 
ssh <admin-username>@<public-ip-address>
```

  ![image](images/19.png)

- Enter the password you set earlier during the VM setup for authentication.
  
  ![image](images/21.png)

- After entering your password, a configuration agreement script will run; simply follow the prompts and agree to the terms.
  
  ![image](images/22.png)

- Leave the rest of the prompts at their default settings by pressing Enter until you reach the prompt where OpenVPN allows you to change the username for the admin dashboard. You can either change it to a username of your choice or leave it as the default by pressing Enter.
  
  ![image](images/23.png)

- The same applies to the password: you can set a custom password or leave it empty to have one randomly generated.
  
  ![image](images/24.png)

- You don’t need to modify anything else, so leave everything else to default until you see the message Initial Configuration Complete!.
  
  ![image](images/25.png)

## 3. Configure OpenVPN admin panel

- You can now access the OpenVPN admin dashboard by navigating to your web browser and entering:

  ```
  your-ip-address/admin
  ```
  
  ![image](images/26.png)

- Click Show **'Advanced'** and then select **'Proceed'** to continue to the OpenVPN admin dashboard.
  
  ![image](images/27.png)

- Now enter the admin credentials you configured earlier during the SSH setup to log into the OpenVPN admin dashboard.
  
  ![image](images/28.png)

- Navigate to **'Network Settings'**.
  
  ![image](images/29.png)

- Replace the default hostname or IP address with your Azure server's public IP.
  
  ![image](images/30.png)

  ![image](images/31.png)

- Save your settings by clicking **'Save'** at the bottom of the page, then click **'Update Running Server'** to apply the changes. This will cause the server to restart and log you out of the dashboard. Simply reconnect by navigating to your-ip-address/admin.
  
  ![image](images/32.png)

  ![image](images/33.png)

## 4. Connect to OpenVPN Client

- Download the OpenVPN client if you haven’t already, and also download the connection profile from the admin dashboard.
  
  ![image](images/34.png)

- Once in the OpenVPN client, click the **+** button at the bottom right to upload the connection profile you just downloaded.
  
  ![image](images/36.png)

  ![image](images/37.png)

- Enter the OpenVPN client credentials you configured earlier to complete the setup.
  
  ![image](images/39.png)

  ![image](images/40.png)

- Turn on the VPN connection, and you should see your IP address change, confirming that the VPN is active and routing your traffic.

  ![image](images/41.png)

## Summary
You have successfully set up an OpenVPN server on Azure, configured the admin dashboard, and connected your devices. You can now enjoy secure, encrypted remote connections for personal use or testing.  


