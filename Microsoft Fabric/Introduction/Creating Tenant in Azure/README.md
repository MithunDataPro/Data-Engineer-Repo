# How to Create an Azure Active Directory Tenant for Microsoft Fabric

## Why Create an Azure AD Tenant for Microsoft Fabric?

Microsoft Fabric requires an **organizational account** (work or school account) tied to an **Azure Active Directory (AAD)** tenant. Personal accounts, such as `@outlook.com` or `@gmail.com`, cannot manage Microsoft Fabric resources. By creating a new AAD tenant, you can:

- **Manage Organizational Users**: Allow multiple users (or guest users) to collaborate in an organizational setting.
- **Manage Permissions and Licenses**: Control access to Microsoft services like Fabric, Power BI, and more.
- **Enable Microsoft Fabric**: Fabric is tied to organizational capacities, so you’ll need an AAD tenant to activate and manage Fabric capacities and services.

---

## Steps to Create a New Azure Active Directory Tenant

### 1. Sign In to the Azure Portal
   - Go to the [Azure Portal](https://portal.azure.com/).
   - Sign in using your existing account (this can be a personal account for now, but we will transition to an organizational account).

### 2. Navigate to Azure Active Directory
   - In the **Azure Portal**, in the left-hand sidebar, search for and select **Azure Active Directory**.

### 3. Create a New Tenant
   - In the Azure AD Overview window, click on **Manage tenants** located at the top.
   - In the **Manage Tenants** pane, click **+ Create** at the top.
   - Choose **Azure Active Directory** and click **Next**.

### 4. Enter Tenant Details
   - **Organization Name**: Enter the name of your organization (e.g., `MyOrg`).
   - **Initial Domain Name**: Choose a domain name in the format `yourorganization.onmicrosoft.com`. This domain name is unique and will serve as the tenant's identity.
   - **Region**: Choose the appropriate geographic location for your organization.

   Click **Review + Create**, then click **Create** to complete the setup.

### 5. Switch to Your New Tenant
   - Once your tenant is created, you need to **switch to the new directory**.
   - Click your **account icon** in the top-right corner of the Azure Portal, then select **Switch Directory**.
   - Choose the newly created tenant from the list.

---

## Step 6: Set Up Users and Assign Licenses

Now that your tenant is set up, you need to manage users and licenses:

### 1. Add Users to Your Tenant
   - Go to **Azure Active Directory** in the sidebar, then click **Users**.
   - Click **+ New User** to add new users. You can also invite external users (guest users) if required.
   - You will need to set up their username, roles (e.g., User or Admin), and group memberships.

### 2. Assign Licenses (Optional for Fabric Usage)
   - Certain services like **Microsoft Fabric** may require specific licenses (e.g., Power BI Premium).
   - Go to **Azure Active Directory** > **Licenses** > **All Products**.
   - Assign licenses to the required users.

---

## Step 7: Enabling Microsoft Fabric

Now that your organizational account is set up, you can enable and use **Microsoft Fabric**.

### 1. Access Power BI to Use Microsoft Fabric
   - Go to [Power BI](https://app.powerbi.com/) in your browser.
   - Log in with your **organizational account** (created under the new AAD tenant).
   - Once logged in, you can create workspaces and start using **Microsoft Fabric** for tasks like Data Engineering, Data Science, and Real-Time Analytics.

### 2. Manage Fabric Capacity in Azure
   - If you need to manage the capacity for **Microsoft Fabric** (e.g., to allocate or monitor resources), you can go back to the **Azure Portal**.
   - Navigate to **Azure Active Directory** > **Subscriptions**, and ensure that you have a valid subscription that supports **Microsoft Fabric**.
   - Allocate **Fabric Capacity** through **Azure Marketplace** or **Power BI Admin Portal**.

### 3. Create Fabric Workspaces
   - In **Power BI**, go to **Workspaces** and create new workspaces where you can use various Fabric services such as **Data Pipelines**, **Data Science**, and **Lakehouse**.
   - Add users from your organization or guest users who need access to Fabric resources.

---

## Key Points About Using Azure AD Tenant for Fabric

1. **Organizational Requirement**: Microsoft Fabric only works with organizational accounts tied to Azure Active Directory, not personal accounts.
   
2. **Centralized User Management**: An Azure AD tenant allows you to manage users, permissions, and security settings in a centralized manner.

3. **Licensing**: Some features in Fabric may require specific licenses like **Power BI Premium** or **Pro**. Ensure users are assigned the appropriate licenses to use Fabric features fully.

4. **Fabric Capabilities**: With **Microsoft Fabric**, you can perform tasks such as Data Engineering, Data Science, Real-time Analytics, and Machine Learning, all managed through Power BI and integrated with Azure services.

---

## Conclusion

By setting up an **Azure AD Tenant**, you can effectively manage **Microsoft Fabric** resources, assign users, and utilize organizational accounts for collaborative data projects. Follow the steps outlined above to create a new tenant, set up your organizational users, and enable access to **Microsoft Fabric** through Azure and Power BI.

Let me know if you have any other questions or need further assistance!

