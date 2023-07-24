Create Policies

In this step we will create Okta Priviledge Access policies

Click **Policy**
Click **Create Policy**
Enter **DemoBiz** as the Policy Name

Select Principals  
Click **Add or Modify**
Select **Okta PA Full Administrators**
Click **Save**

Define Rules  
Click **Add Rule**
Enter `Gateways` as the Rule Name
Choose Session Type **SSH Session**  

Select the resources you want to protect with this rule
Enable Select resource by system generated label
Add resource label

Start typing 'hostname' and select your Gateway server

How do you want Principals to access resources?

Tick Access resources by individual account

Session Recording
Tick **Enable traffic forwarding through gateways**
Tick **Record session through gateways**
Click **Save Rule**

Click **Save Policy**