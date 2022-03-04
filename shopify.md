# Setup Guide

## Prerequisites
To connect your Shopify account to Weld, you need:

- Access to a Shopify account
- Authenticated access scopes for Shopify's Admin API. For more information, see [Shopify's documentation](https://shopify.dev/docs/admin-api/access-scopes).

## Setup Instructions
### Step 1 - Begin Configuration
1. In the connector setup form, enter the destination schema name of your choice.
2. Click Authorize. You will be redirected to Shopify's login page.
### Step 2 - Configure and finalize
1. Log in to your Shopify account. You will be redirected to the Shopify admin UI, which will prompt you to install the Weld app.
2. Click Install unlisted app. This will install the Weld app with the required access scopes. When authorization is complete, you will be redirected back to the Weld connections overview. The configuration is complete.

>Important: If you need to add Weld to multiple stores the following applies.<br>When clicking Authorize you'll be redirected to the Shopify App listing of Weld. Here you need to log out if logged in to be able to choose the correct store.
>1. Click Log out on the top left corner
>2. After logging out click Add app
>3. Log in to the account that holds the store
>4. You'll have a popup asking you to choose the store, here you can select the one you'd like to connect to
>5. Complete the authorization