Note: These tutorials are created by Okta team members and may not be 100% accurate. We will do our best to provide updates and make sure they are accurate as the product evolves.

Purpose & Goal:

This tutorial will guide you through setting up Advanced Server Access and GitLab to provide a security CI/CD pipline by eliminating the need to manage SSH keys. The service account used by the gitlab-runner leverages ASA's ephemeral credential mechanism to authenticate to ASA protected servers. There are no SSH keys to create, deploy, revoke or rotate, and no passwords to steal.

The tutorial assumes that you have the following in place;

Base ASA Environment including;
2 Linux Servers
Gitlab Account

Setup:

Testing: