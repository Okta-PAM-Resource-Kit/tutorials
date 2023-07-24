Setup Okta

Log into Demo Eng Okta WIC Tenant

Create Okta Priviledged Access Groups

Click: Directory
Click: Groups
Click: Add Group
Name: Okta PA Full Administrators
Description: Okta Priviledged Access Full Administrators
Click: Save

Click: Add Group
Name: Okta PA Resource Administrator
Description: Users with this roles can manage configuration or settings for protected resources.
Click: Save

Click: Add Group
Name: Okta PA Security Administrators
Description: Users with this role can manage security policies for protected resources.
Click: Save

Click: Add Group
Name: Okta PA Users
Description: Users who can access PAM resources
Click: Save


Add Okta Priviledged Access Application

Click: Applications
Click: Applications
Click: Browser App Catalog
Search: Okta Privileged Access
Click: Add Integration
Team Name: Enter an OPA Team Name (Remember this value)
Follow Prompts etc

Click Assignments
Click: Assign
Click: Assign to People
Search: Your username
Click Assign

Click: Assign
Click: Assign to Groups
Search: Okta PA Full Administrators
Click Assign
Search: Okta PA Resource Administratos
Click Assign
Search: Okta PA Security Administrators
Click Assign
Search: Okta PA Users
Click Assign
Click: Done

Click: Provisioning
Click: Configure API Integration
Tick: Enable API Integration
Click: Autenticate with OPA
Type: Team Name
Type: okta-scim
Click: Approve
Click: Save
Click: Edit
Tick: Create Users
Tick: Update User Attributes
Tick: Deactivate Users
Click: Save

Click: Push Groups
Click: Push Groups
Click: Find Groups by Name
Search: Okta PA Full Administrators
Click: Save & Add Another
Search: Okta PA Resource Administrators
Search: Okta PA Security Administrators
Click: Save & Add Another
Search: Okta PA Users
Click: Save
