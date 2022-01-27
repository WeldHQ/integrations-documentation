# Setup Guide

## Prerequisites
To connect Stripe to Weld, you need:
- An active Stripe account with permission to access data from accounts you would like to sync.
- Administratior or Developer access to the account.


## Setup Instructions
### Step 1 - Create API Keys
1. Log into the account that you will connect to Weld.
2. Go to the main dashboard.
3. Go to <b> 'Restricted Keys'</b> then <b>'Create Restricted Key'</b>
4. Create a name for your Key.
5. Under 'Resource Type', grant Read permissions for all resources.
6. Create your Key
### Step 2 - Weld Configuration and finalize
1. On the Weld connector setup page, enter a destination schema name.
> This value is used for identifying the connection in destinations and cannot be changed later
2. Enter the Stripe API key.
3. Click Connect
4. When authorization is complete, you will be redirected back to the Weld connections overview. The configuration is complete.

