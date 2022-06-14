
# How To Connect BigQuery
For Weld to be able to connect to Bigquery, you need a service account with the right credentials.   

To facilitate this, you need to create a Google Cloud Platform (GCP) service account for Weld. Furthermore you need to assign the following roles to this service account. We recommend that you create a new service account for this, and only attach these roles to that service account. This ensures that Weld can only access what is required, and helps secure your GCP account.

**1.** Enable **Cloud Resource Manager API** in GCP
Go to [**Cloud Resource Manager API**](https://console.cloud.google.com/marketplace/product/google/cloudresourcemanager.googleapis.com) and press **Enable**


>This is required for us to verify that the service account provided to Weld, has the correct permissions to operate.
>If there is no **Enable** button, it might be enabled already.

**2.** Create service account
Go to [**Service Accounts**](https://console.cloud.google.com/iam-admin/serviceaccounts), and press create new account.  

Give it a name and press **Create and continue**. 
Grant the service account the following roles:  
-   BigQuery User
-   BigQuery Job User
-   BigQuery Metadata Viewer
-   BigQuery Data Editor

now press **Done**

**3.** Download your service account key

In the **Service accounts** window, click the service account you just created, and then press **Keys**. 


Now click **Add Key**, and then **Create New Key**. 
Select **JSON**, and then press **Create**. 

**4.** Almost done!

With your freshly created service account key file downloaded, all that is left to do is to drop it into the box in the weld app here, select your GCP hosting location, and you are ready to start welding!
