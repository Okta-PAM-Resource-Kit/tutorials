In this step we are going to setup and configure Okta Privileged Access to be integrated into your Okta tenant. After this step is completed, we will have a working Okta Privileged Access application and users and groups provisioned into it.

The following steps will be completed while you are logged into your Okta tenant.

**Create Okta Privileged Access Groups**  

Select **Directory** > **Groups** from the navigation menu.

Click **Add Group**

Enter **Okta PA Full Administrators** as the Group Name

Enter **Okta Privileged Access Full Administrators** as the Description 

Click **Save**  

Click **Add Group**

Enter **Okta PA Resource Administrator** as the Group Name

Enter **Users with this roles can manage configuration or settings for protected resources.** as the Description 

Click **Save**  

Click **Add Group**

Enter **Okta PA Security Administrators** as the Group Name

Enter **Users with this role can manage security policies for protected resources.** as the Description 

Click **Save**  
  
Click **Add Group**

Enter **Okta PA Users** as the Group Name

Enter **Users who can access PAM resources** as the Description 

Click **Save**  
 

**Integrate Okta Privileged Access Application**  


Select **Applications** > **Applications**

Click **Browser App Catalog**

Type **Okta Privileged Access** in the search bar

Click **Add Integration**

Enter an **OPA Team Name** - This will be the name of your Okta Privileged Access tenant

COMPLETE STEPS  

Okta Privileged Access is now enabled and integrated into your Okta Tenant, we just have some final configurations to complete.  

Click **Assignments**

Select **Assign** > **Assign to People**

In the Search bar enter `your username`

Click **Assign**  

Select **Assign** > **Assign to Groups**

In the Search bar enter **Okta PA Full Administrators**

Click **Assign**  

In the Search bar enter **Okta PA Resource Administrator**

Click **Assign**  

In the Search bar enter **Okta PA Security Administrators**

Click **Assign**  

In the Search bar enter **Okta PA Users**

Click **Assign**

Click **Done**  

We will now enable Provisioning from Okta into Okta Privileged Access.  

Click **Provisioning**

Click **Configure API Integration**

Select **Enable API Integration**

Click **Authenticate with Okta Privileged Access**

Enter your **Team Name** (This was enter when we added the Okta Privileged Access application into Okta)

Enter **okta-scim**

Click **Approve**

Click **Save**

Click **Edit**

Select **Create Users**

Select **Update User Attributes**

Select **Deactivate Users**

Click **Save**  

 We will now configure Push Groups.  

Click **Push Groups**

Select **Push Groups** > **Find Groups by Name**

In the Search bar enter **Okta PA Full Administrators**

Click **Save & Add Another**  

In the Search bar enter **Okta PA Resource Administrators**

Click: **Save & Add Another**  

In the Search bar enter **Okta PA Security Administrators**

Click **Save & Add Another**  

In the Search bar enter **Okta PA Users**

Click **Save**  
