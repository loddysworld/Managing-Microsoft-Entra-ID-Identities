# Creating Microsoft Azure Entra-ID Identities

<h2>Description</h2>
In this Tutorial, we will be diving into the Fundamentals of an Azure Administrator with creating and understanding of groups and users. These are the basic building blocks for Identity Management and Priviledged Management.
<br />
<h2>Time Estimated: 30 Mins</h2>
<h2>Scenerio</h2>
Your company is establishing a fresh laboratory setting for pre-production examination of applications and services. Several engineers are being recruited to oversee this environment, including the virtual machines. Your responsibility is to facilitate user authentication via Microsoft Entra ID by provisioning user and group accounts. The aim is to reduce administrative workload by automatically updating group memberships according to job titles. Additionally, you need to understand the process of deleting users to prevent access once an engineer departs from the organization.


<h2>Architecture Diagram</h2>

<img src="https://imgur.com/BeyIE2g" alt="Diagram"/>

<h2>Skills</h2>

- <b>Creating a Resource Group</b>
- <b>Create and Configure User Accounts</b>
- <b>Create Group Accounts and Add Members</b>
- <b>Use Cloud Shell</b>
- <b>Use PowerShell</b>
- <b>Use Bash Shell</b>

<h2>Step 1: Creating A Resource Group</h2>
In this step, we will be creating a Resource Group for the Company. A resource group is a container that groups related resources for your cloud solution. You would make Resource groups for each different department, application, or project for concerns of seperation.

1. Sign in to the **Azure portal** - `https://portal.azure.com`.

    >**Note:** If you are new to the Azure, search for and select `Quickstart Center`. Take a few minutes to watch the **Getting started in the Azure portal** video.
   
1. In the Azure portal, search for and select `Resource groups`.

![step1](https://github.com/loddysworld/Managing-Microsoft-Entra-ID-Identities/assets/134660738/e034380b-9563-4cbb-a586-c03456b9470e)

![step2](https://github.com/loddysworld/Managing-Microsoft-Entra-ID-Identities/assets/134660738/177d8daa-a76b-4f58-9543-4fdb089e76cb)
   
1. On the **Resource groups** blade, click **+ Create**, and provide the required information. 

    | Setting | Value |
    | --- | --- |
    | Subscription name | your subscription |
    | Resource group name | `workhard.rg1` |
    | Location | **East US** |

![step3](https://github.com/loddysworld/Managing-Microsoft-Entra-ID-Identities/assets/134660738/8fc62d67-9dc4-4693-ba4f-5fe0141ce137)


## Step 2: Create and configure user accounts

In this step, you will create and configure user accounts. User accounts will store user data such as name, department, location, and contact information.

1. Continue in the Azure portal. 

1. Search for and select `Microsoft Entra ID`.

1. Microsoft Entra ID is Azure's cloud-based identity and access management solution (Active Directory).

![step4](https://github.com/loddysworld/Managing-Microsoft-Entra-ID-Identities/assets/134660738/5893c3f5-b9df-4cfb-8dff-d5bde0969eb3)

### Create a new user

1. Select **Users**, then in the **New user** drop-down select **Create new user**.
   
![step5](https://github.com/loddysworld/Managing-Microsoft-Entra-ID-Identities/assets/134660738/acff6b4b-e8bf-433e-b689-6435fe9c624d)

1. Create a new user with the following settings (leave others with their defaults). On the **Properties** tab notice all the different types of information that can be included in the user account. 

    | Setting | Value |
    | --- | --- |
    | User principal name | `workhard-user1` |
    | Display name | `workhard-user1` |
    | Auto-generate password | de-select |
    | Initial password | **Provide a secure password** |
    | Job title (Properties tab) | `IT Lab Administrator` |
    | Department (Properties tab) | `IT` |
    | Usage location (Properties tab) | **United States** |

    >**Note:** For this exercise you may use any password but a strong and secure Password is imperative and recommended for the security and well-being of the company. Weak passwords lead to unauthorized access from bruteforce attacks and Compliance Issues due to data vulnerability.

1. Once you have finished reviewing, select **Review + create** and then **Create**.

![step6](https://github.com/loddysworld/Managing-Microsoft-Entra-ID-Identities/assets/134660738/12f7d215-d222-4e12-899f-3c10866bf9bc)

### Invite an external user

1. Select **Users**, then in the **New user** drop-down select **Invite an external user**.
   
![step7](https://github.com/loddysworld/Managing-Microsoft-Entra-ID-Identities/assets/134660738/8077c66c-2493-456f-9261-8d6b41856726)

    | Setting | Value |
    | --- | --- |
    | Email | your email address |
    | Display name | your name |
    | Send invite message | **check the box** |
    | Message | **Welcome to Azure and our group project** |

1. Move to the **Properties** tab. Notice the **User type** is **Guest**. Notice the user account information is similar to creating a new user.

1. Select **Review + invite**, and then **Invite**.

![step8](https://github.com/loddysworld/Managing-Microsoft-Entra-ID-Identities/assets/134660738/374b53e8-dd73-428a-96c6-ccfa5044f831)

>**Note:** You are unlikely to be creating accounts individually. Are you aware of of the plans your organization have implemented to create and manage user accounts?

### Step 4: Create group accounts and add members

In this step, you will create a group account. Group accounts can include user accounts or devices. These are two ways member are assigned to groups: Statically and Dynamically. Static groups require manual updates of adding and removing users by the administrator. Dynamic will do the steps based off of properties associated with the user. For example, their job title or department.

1. In the Azure portal, search for and select `Groups`.

![step9](https://github.com/loddysworld/Managing-Microsoft-Entra-ID-Identities/assets/134660738/6b278ab9-db24-4fd4-b2f8-00a0107967aa)

1. Select **+ New group** and create a new group. 

    | Setting | Value |
    | --- | --- |
    | Group type | **Security** |
    | Group name | `IT Lab Administrators` (adjust the name if this one is not available) |
    | Group description | `Administrators that manage the IT lab` |
    | Membership type | **Assigned** |

    >**Note**: There are other options in the **Membership type** drop-down. An Entra ID Premium P1 or P2 license is required for dynamic membership. 

![step10](https://github.com/loddysworld/Managing-Microsoft-Entra-ID-Identities/assets/134660738/d3f885a1-29d1-4790-97ef-c330e93c1fe3)

1. Select **No owners selected**.

1. In the **Add owners** page, search for and **select** yourself as the owner. Notice you can have more than one owner. 
   
1. Select **No members selected**.

1. In the **Add members** pane, search for and **select** the **az104-user1** and add them to the group. 

1. Select **Create** to deploy the group.

>**Note:** You may be managing a large number of groups. Does your organization have a plan for creating groups and adding members?

## Step 5: Use the Cloud Shell.

In this step, you will be working with the Azure Cloud Shell. Azure Cloud Shell is an interactive, authenticated, browser-accessible terminal for managing Azure resources. It provides flexibility of choosing the shell experience that best suits the way you work, either Bash or PowerShell.

1. Select the **Cloud Shell** icon in the top right of the Azure Portal. If you'd like, you can navigate directly to `https://shell.azure.com`.

![step11](https://github.com/loddysworld/Managing-Microsoft-Entra-ID-Identities/assets/134660738/8d6237ea-2c44-4cd1-8280-5ab60ad22503)

1. When prompted to select either **Bash** or **PowerShell**, select **PowerShell**.
   
![step12](https://github.com/loddysworld/Managing-Microsoft-Entra-ID-Identities/assets/134660738/daab670f-1c4d-44c6-bad0-f5c0e14456c6)

    >**Note:** If you mostly work with Linux systems, Bash feels more familiar. If you mostly work with Windows systems, Azure PowerShell feels more familiar. 

1. On the **You have no storage mounted** screen select **Show advanced settings** and provide the required information. When completed select **Create storage**.

## Step 6: Using Azure PowerShell

In this task, you create a resource group and a group account by using Azure PowerShell session within the Cloud Shell. Azure PowerShell scripts will be provided throughout the course. 

>**Note:** You can use the arrow keys to move through the command history. It makes it easier to run prior commands instead of re-typing.

1. Azure PowerShell uses a *Verb*-*Noun* format for commands. For example, the command to create a new resource group is **New-AzResourceGroup**. To view how to use a command, run the Get-Help command.

   ```powershell
   Get-Help New-AzResourceGroup -detailed
   ```
 ![step13](https://github.com/loddysworld/Managing-Microsoft-Entra-ID-Identities/assets/134660738/6cf4989f-a3c2-4f1d-acdd-3e9562b22bc0)

1. To create a resource group, run the following commands. Note that the commands starting with a dollar sign ($) are creating variables. Ensure you receive a succeeded message. 

   ```powershell
   $location = 'eastus'
   $rgName = 'wh102-rg-ps'
   New-AzResourceGroup -Name $rgName -Location $location
   ```
![step14](https://github.com/loddysworld/Managing-Microsoft-Entra-ID-Identities/assets/134660738/00372f19-858b-4746-9c59-2809039a8dc6)

1. To confirm if all the information was entered correct for the new resource group, run the following command:

   ```powershell
   Get-AzResourceGroup -Name $rgName
   ```
 ![step15](https://github.com/loddysworld/Managing-Microsoft-Entra-ID-Identities/assets/134660738/d921eb23-a9fe-45c4-846d-691480a97cb0)

1. Now, let's try learn how to create an Azure group.

   ```powershell
   Get-Help New-AzureADGroup -detailed
   ```

1. Using the example in the Help, try these commands. Notice you must first connect to Azure AD.

   ```powershell
   Connect-AzureAD 
   New-AzureADGroup -DisplayName "MyPSgroup" -MailEnabled $false -SecurityEnabled $true -MailNickName "MyPSgroup"
   ```
 ![step16](https://github.com/loddysworld/Managing-Microsoft-Entra-ID-Identities/assets/134660738/d17e741e-490c-4237-8e08-2f182c67d5a0)

1. Return to the Azure portal. Confirm you have a new resource group and a new Azure group. You may need to Refresh the pages.
   
 ![step17](https://github.com/loddysworld/Managing-Microsoft-Entra-ID-Identities/assets/134660738/f423e968-d5c2-4b1f-9d8e-becb71e8075f)

## Step 7: Using the Bash shell

In this step, you will be creating a resource group and an Azure group by using Azure CLI within the Cloud Shell.

1. Continue in the Cloud Shell. Use the drop-down to switch to **Bash**.

![step18](https://github.com/loddysworld/Managing-Microsoft-Entra-ID-Identities/assets/134660738/3dc39024-8e80-411f-9002-2a143ecde53a)

>**Note:** You can use the arrow keys to move through the command history. It makes it easier to run prior commands instead of re-typing.

1. The Azure CLI uses an easy-to-read syntax. For example, to interact with resource groups, the command is **az group**.  

   ```sh
   az group --help
   ```
 ![step19](https://github.com/loddysworld/Managing-Microsoft-Entra-ID-Identities/assets/134660738/dbf663b8-58cf-4da1-9b78-8a892a0d950b)


1. The **create** option looks promising. Note the capitalized names create variables that you can reference in subsequent commands. 

   ```sh
   RGNAME='wh102-rg1-cli'
   LOCATION='eastus'
   az group create --name $RGNAME --location $LOCATION
   ```
 ![step20](https://github.com/loddysworld/Managing-Microsoft-Entra-ID-Identities/assets/134660738/3fd0e78d-3362-4cd0-a3cb-ee9088dcc439)
   
1. To verify and retrieve properties for the newly created resource group, use the **show** command. 

   ```sh
   az group show --name $RGNAME
   ```
1. Now, let's use help to learn more about creating an Azure group.

    ```sh
    az ad group --help
    ```
1. **Create** the group and **list** the groups to verify.

   ```sh
   az ad group create --display-name MyCLIgroup --mail-nickname MyCLIgroup
   az ad group list
   ```
 ![step21](https://github.com/loddysworld/Managing-Microsoft-Entra-ID-Identities/assets/134660738/f44ac5c0-1974-45cb-819d-44d3f43d61ed)


1. Return to the Azure portal. Confirm you have a new resource group and a new Azure group. You may need to Refresh the pages.
![step22](https://github.com/loddysworld/Managing-Microsoft-Entra-ID-Identities/assets/134660738/20e0b985-25ad-4d80-8146-cb1597d73371)

    
## Take-Aways

Thank you for following along on this setup. Here are some main take-aways from this exercise:

+ The Azure portal is a good way to get started with creating and managing Azure resources. Administrators can customize the portal and share dashboards.
+ Resource groups are the best way to group resources together.
+ There are different types of user accounts in Microsoft Entra ID. Each user account type has a level of access.
+ Group accounts group together related users or devices. Group membership can be assigned statically or dynamically. Whichever is best for the business.
+ Azure PowerShell and Bash provide a scripted way to create resources. 


## Cleanup your resources

If you are working with your own subscription take a minute to delete the lab resources. This will ensure resources are freed up and cost is minimized. The easiest way to delete the lab resources is to delete the lab resource group. 

+ In the Azure portal, select the resource group, select **Delete the resource group**, **Enter resource group name**, and then click **Delete**.
+ Using Azure PowerShell, `Remove-AzResourceGroup -Name resourceGroupName`.
![step23](https://github.com/loddysworld/Managing-Microsoft-Entra-ID-Identities/assets/134660738/b58eb9f6-526b-41fe-8bfa-6d1a8938dc96)
+ Using the CLI, `az group delete --name resourceGroupName`.
![Deleteresourcegroup](https://i.imgur.com/kJtpiio.png)



<p align="center">

</p>

<!--
 ```diff
- text in red
+ text in green
! text in orange
# text in gray
@@ text in purple (and bold)@@
```
--!>
