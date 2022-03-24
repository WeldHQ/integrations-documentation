
# How To Connect Bigquery
For Weld to be able to connect to Bigquery, you need a service account with the right credentials.   

To facilitate this, you need to create a Google Cloud Platform (GCP) service account for Weld. Furthermore you need to assign the following roles to this service account. We recommend that you create a new service account for this, and only attach these roles to that service account. This ensures that Weld can only access what is required, and helps secure your GCP account.

**1.** Enable **Cloud Resource Manager API** in GCP
Go to **Cloud Resource Manager API** and press **Enable**
![enter image description here](https://lh3.googleusercontent.com/pw/AM-JKLWnwqZ5bObR5-xdZh1WSFbHiO22elK7vJ9znVh-OtkC-JKDLqqPcY2rrGuu5Hjfu7u8n2UGvMG9u4yeuSAAaDEI0VSEua99FKiFEO30BmkRQoJ3Ft2huZyuDp312tqA1_WBRkdtVqrHJcED2DX_nIU=w1414-h706-no?authuser=0)


>This is required for us to verify that the service account provided to weld, has the correct permissions to operate.
>If there is no **Enable** button, it might be enabled already.

**2.** Create service account
Go to **Service Accounts**, and press create new account.  
![enter image description here](https://lh3.googleusercontent.com/pw/AM-JKLX5r-XzFpLy0awX4QSPQ5mBhjVEKbrXkfpDjwUvuLZ7M4laHbjnHdLOROAUtvZGMqYOxRE94lGb3Le6MahZrh15T23X9FXuzry8q8svnlAYwZ1poXZzQe_SN-XqKsKgEccKfGna8XjCLy9kbnh2beQ=w1532-h500-no?authuser=0)
Give it a name and press **Create and continue**. 
Grant the service account the following roles:  
-   BigQuery User
-   BigQuery Job User
-   BigQuery Metadata Viewer
-   BigQuery Data Editor

now press **Done**

**3.** Download your service account key
In the **Service accounts** window, click the service account you just created, and then press **Keys**. 
![enter image description here](https://lh3.googleusercontent.com/pw/AM-JKLVLCTaID3Qb51DveC8KeF9JsS2j5tiiG9WBNOou2iNU-Co1rubTnlZi1G6lti-PZozKm7PgQoYLYaX6H03nFZqQkXx5p6lofbvaaU-XikMBPQHMf_0Y0Nn2LaaalW5wwffhd9ANrf3m8WXAX7i1Eeo=w1470-h612-no?authuser=0)
Now click **Add Key**, and then **Create New Key**. 
Select **JSON**, and then press **Create**. 

**4.** Almost done!
With your freshly created service account key file downloaded, all that is left to do is to drop it into the box in the weld app here, select your GCP hosting location, and you are ready to start welding!