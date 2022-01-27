# Setup Guide

## Prerequisites
To connect Mixpanel to Weld, you need:
- An active Mixpanel account with permission to access data from projects you would like to sync.


## Setup Instructions
<!-- ### Step 1 - Begin Configuration -->
In the connector setup form enter the following fields:  
1. **Label**: Enter the destination schema name of your choice.
2. **Project ID**: 
    1. In Mixpanel, click the Settings icon in the top right corner.
    ![image settings](images/mixpanel_1_settings.png?raw=true)
    2. Choose Organization Settings
    ![image organization](images/mixpanel_2_organization.png?raw=true)
    3. In "Organization Settings", select "Projects"  
    ![image projects](images/mixpanel_3_projects.png?raw=true)
    4. Click on the relevant project name 
    ![image project list](images/mixpanel_4_project_list.png?raw=true)
    5. You will find the "Project ID" in the Project Details
    ![image project id](images/mixpanel_5_project_id.png?raw=true)

3. **Service Account**: For the Service Account username and secret, you will need to create a Service Account in Mixpanel.  
    1. In Mixpanel, click the Settings icon in the top right corner.  
    ![image settings](images/mixpanel_1_settings.png?raw=true)
    2. In "Organization Settings", select "Service Accounts"  
    ![image service accounts](images/mixpanel_6_service_accounts.png?raw=true)
    3. Select "+ Service Account" (top right corner)
    ![image add service account](images/mixpanel_7_add_service_account.png?raw=true)
    4. Fill in the details and create service account
        - *Name:* Give it a name e.g. "weld_service_account"
        - *Organization role:* Admin
        - *Projects:* Select relevant projects
        - *Project role:* Admin
        - *Expires:* Never
    ![image create service accoint](images/mixpanel_8_create_service_account.png?raw=true)
    4. Click "Create" and you will be shown the Service Account username and secret. Note that once you close this, you will never be able to access the secret again, so be sure to save it somewhere secure
4. Region: Select the region of your data warehouse
5. Click "Connect" to allow Weld to access your Mixpanel account.