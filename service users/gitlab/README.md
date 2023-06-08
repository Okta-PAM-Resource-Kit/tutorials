Note: These tutorials are created by Okta team members and may not be 100% accurate. We will do our best to provide updates and make sure they are accurate as the product evolves.

# Purpose & Goal:

This tutorial will guide you through setting up Advanced Server Access and GitLab to provide a security CI/CD pipline by eliminating the need to manage SSH keys. The service account used by the gitlab-runner leverages ASA's ephemeral credential mechanism to authenticate to ASA protected servers. There are no SSH keys to create, deploy, revoke or rotate, and no passwords to steal.

The tutorial assumes that you have the following in place;

Base ASA Environment including;
2 Linux Servers (Ubuntu in this example)
- 1 Assigned Web Server (WEBSERVER)
- 1 Assigned Gitlab Runner Server (GITLABRUNNERSERVER)
Gitlab Account (https://gitlab.com/users/sign_up)

# Setup GitLab

Create Repository using the code in this folder (INSERT LINK)
Edit 'gitlab-ci.yml' so that SERVERNAME is replaced by the hostname of your Assigned Web Server
Save repo

Settings -> CICD -> Runners -> Expand
New Project Runner
Tick 'Run untagged jobs'
Create Runner
Make a copy of the Step 1 code
Go to runner pages

## Prepare WEBSERVER

Use ASA to connect to WEBSERVER
Elevate to root 
Run: apt-get install nginx

## Prepare Gitlab Runner Server

Use ASA to connect to GITLABRUNNERSERVER
Install ASA Client: sudo apt-get install scaleft-client-tools
Install Gitlab Runner:

### Download the binary for your system
sudo curl -L --output /usr/local/bin/gitlab-runner https://gitlab-runner-downloads.s3.amazonaws.com/latest/binaries/gitlab-runner-linux-amd64

### Give it permission to execute
sudo chmod +x /usr/local/bin/gitlab-runner

### Create a GitLab Runner user
sudo useradd --comment 'GitLab Runner' --create-home gitlab-runner --shell /bin/bash

### Install and run as a service
sudo gitlab-runner install --user=gitlab-runner --working-directory=/home/gitlab-runner
sudo gitlab-runner start

### Register Gitlab Runner
Paste Step 1 code and run command. It should look something like;

EXAMPLE: sudo gitlab-runner register --url https://gitlab.com/ --registration-token GR13234567876543_IucnsW

Run: sudo su -
Run: su gitlab-runner
Run: id
Make a note of the ID shown on screen

### Associate ASA Service User

Open ASA
Navigate to Users
Click Service Users
Click Create Service User
Username: gitlab
Click: Create Service User
Click: Create API Key
Click: OK
Click: Groups
Click: Create Group
Group Name: gitlab
Click: Create Group
Click: Users
Usrname: gitlab
Click: Add User

Click: Home
Click: GITLABRUNNERSERVER
Click: Services
Click: Add Service
Service User: gitlab
Server UID: Id of Gitlab Runner User displayed earlier
Click: Submit

Click: Projects
Open Project where WEBSERVER exists
Click: Groups
Click: Add Group to Project
Group: gitlab
Server Account Permissions: Admin
Click: Add Group
Repeat for GITLABRUNNERSERVER

### Complete GITLABRUNNERSERVER Setup

Navigate back to GITLABRUNNERSERVER Terminal Window
Run: sudo su gitlab-runner
Run: sft config service_auth.enable true
Run: sft ssh-config >> .ssh/config
Run: sft ssh WEBSERVER

You should now be able to authenticate as service user 'gitlab' from GITLABRUNNER to WEBSERVER using ASA.


# Testing

Navigate to Gitlab
Click Build > Pipelines
Click Run Pipeline

# Thanks

Shad Lutz @ Okta