# Readme
This repository is used to play a bit around Azure. I demonstrates how to deploy VMs, Container Registry, Kubernetes Cluster, Containers, etc.
This is not a full training or learning material. It just give a feeling about Azure with some focus areas (especially containers).
The target is to have 2 hours of fun for the price of 1 or half bottle of beer. Seriously, you will use my shared subscription so deploy carefully ;)

## Azure interface
In the below example we will use the [Azure Portal](https://portal.azure.com/) and the [Azure CLI](https://docs.microsoft.com/en-us/cli/azure/install-azure-cli?view=azure-cli-latest).
For Windows download the installer from here: [Azure CLI](https://aka.ms/installazurecliwindows)

While you install let's see how Azure organizes resources.

Open [Azure Portal](https://portal.azure.com/) and log in to your account.

## Azure hierarchy
It looks like this:
![Hierarchy](Azure_hierarchy.png)

## Setup Azure CLI
After the installation, start a PowerShell and enter the following commands to configure the proxy.
This is temporary only to that PowerShell session.
Then login the Azure CLI. It will prompt up your default browser and ask you to log in.

```powershell
$env:HTTP_PROXY='http://10.158.100.1:8080'
$env:HTTPS_PROXY='http://10.158.100.1:8080'
az login
```

## Create a Resource group
1. On the Azure portal's home screen select **Resource groups**. It opens the Resource groups "blade" where you might see other resource groups which belong to the same Subscription.
2. Click on **Add**
3. Give a **Name** to your own Resource group.
4. For the **Location** select "Central US". This location has some fancy features like Availability zones.
5. Then click on **Review + create**
6. Then once click on **Create**
It might take few seconds and your own Resource group is ready.

## Create your very first service
On the top of the portal there is a search bar.
1. Click on the **Search bar at the top**
2. And search for **Wordpress**
3. Select the "WordPress" from the Marketplace
4. Give a unique **Name** to your instance. This must be globally unique in the whole Azure.
5. At Resource Group select **Use existing** then select your previously created. At this point you can create a new resource group if it wouldn't exist.
6. Click on **App Service plan/Location**
   1. **Create new**
   2. Add a name to **App Service plan**
   3. Click on **Pricing tier**
   4. Go to the **Dev / Test** tab
   5. Select **F1**
   6. Click on **Apply**
   7. Click on **OK** at the bottom. Now the Service plan is updated with your named SP.
7. Click on Database
   1. Enter a random **Password**. We won't use it anywhere. To fulfill requirements use this: Password+1234
   2. And then **Confirm password**
   3. Select **Pricing tier**
   4. Go to **Basic** tab
   5. Bring the **vCore** and **Storage** slides to the minimum
   6. Click on **OK**
   7. And again click on **OK**
   8. Click on **Create**

The deployment is ongoing. You can track the deployment if you click on the bell icon on the top right on the portal.
It will take about 3 minutes.
When the deployment is done then:
1. Navigate to your own **Resource group**
2. Observe the new object which just deployed
3. Click on your item which has the **App Service** type
4. Observe the details
5. On the **Overview** page search for the **URL**. This is https://<your_given_name>.azurewebsites.net
6. Click on the link. Congratulation you have your very own website running on Azure.
7. Close your webpage tab and go back to Azure portal
8. Go back to your **Resource group**
9. Select your item which has the **Application Insights** type. Here you can see metrics and statistics about the application.
Are you happy? Then let's delete it :)

Clean up. You can notice that there are several resources automatically created inside your resource group. You can delete them  1 by 1. The easiest way to clean up everything is delete the whole resource group.
1. Navigate to your own **Resource group**
2. On the top menu click on **Delete resource group**
3. You need to re-enter its Name.
4. Click on **Delete**
Removing everything will take a while. No need to wait for it.

** Create a Container builder VM
We need a VM which will build our container and push it into the Registry.
1. On the home page click on **Create resource**. You can see **Categories** and some **Popular** options here. 
2. Click on **Ubuntu Server 18.04 LTS**. The VM creation blade comes up immediately.
3. At the **Resource group** click on the **Create new**. (If the previous is still under delete then give another name.)
4. Give a name at the **Virtual machine name**
5. For the **Region** select **Central US**
6. At the **Size**, click on the **Change size**
7. As we don't need a powerfull machine hence select **B1s**. (If you don't see it then remove the filters.)
8. For the **Authentication type** select **Password**
9. Give a **Username**
10. Give a **Password** and **Confirm password**. Hint: Password+1234
11. The SSH port shall be allowed for inbound.
12. There are additional options for networking and storage but we skip them.
13. Click on **Review + create**. The validation takes few seconds.
14. Click on **Create** and wait for the deployment.
The deployment takes ~5 minutes.

Meanwhile prepare putty with proxy.
![Putty](Putty_proxy.png)
1. Go to your **Resource group**
2. Find your **Public IP address**. Hint: it has an own resource but your can find it a the Virtual Machine as well.
3. Connect to the VM via SSH. You shall use your given username/password.
4. Install Docker
```bash
sudo apt-get update
sudo apt-get install docker docker.io
```
5. Build the first container
```bash
wget 
sudo docker 
```
