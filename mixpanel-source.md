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
    ![image_setting](https://drive.google.com/uc?id=1ZiregpWdHvy7IbfmT4T30LgCYzWLMm_l)
    2. Choose Organization Settings
    ![image organization](https://drive.google.com/uc?id=176rrsIM6aw8XhYGXIIp6QMfE87fjOlWT)
    3. In "Organization Settings", select "Projects"  
    ![image projects](https://drive.google.com/uc?id=1Pzb09iQGOxxrJGh5dVTnrG8cndQLE5UD)
    4. Click on the relevant project name 
    ![image project list](https://drive.google.com/uc?id=15bXpXl0OrVIXJev-pAxTJ-1zzZLoals8)
    5. You will find the "Project ID" in the Project Details
    ![image project id](https://drive.google.com/uc?id=1KB5G5Z0b9o8ZemwJ0Hwpl6ORj60b7Kru)

3. **Service Account**: For the Service Account username and secret, you will need to create a Service Account in Mixpanel.  
    1. In Mixpanel, click the Settings icon in the top right corner.  
    ![image_setting](https://drive.google.com/uc?id=1ZiregpWdHvy7IbfmT4T30LgCYzWLMm_l)
    2. In "Organization Settings", select "Service Accounts"  
    ![image service accounts](https://drive.google.com/uc?id=1AC5PnBftFMr0ChRNVIGNqedGkT4ryrjq)
    3. Select "+ Service Account" (top right corner)
    ![image add service account](https://drive.google.com/uc?id=1CyTiZvjyUHA5OVE0_6YHXnz_s3VmwwME)
    4. Fill in the details and create service account
        - *Name:* Give it a name e.g. "weld_service_account"
        - *Organization role:* Admin
        - *Projects:* Select relevant projects
        - *Project role:* Admin
        - *Expires:* Never
    ![image create service accoint](https://drive.google.com/uc?id=19Wg_q6QBx-2KbVVEa5vqIMRInBuVwjzX)
    4. Click "Create" and you will be shown the Service Account username and secret. Note that once you close this, you will never be able to access the secret again, so be sure to save it somewhere secure
4. Region: Select the region of your data warehouse
5. Click "Connect" to allow Weld to access your Mixpanel account.
