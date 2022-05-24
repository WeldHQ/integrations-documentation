
# How To Connect Snowflake
For Weld to be able to connect to Snowflake, you need a user with the right credentials.   

>Psst. New to snowflake? No worries, in order to use Weld for snowflake, you just need to know the basics. Here is a good place to start: https://docs.snowflake.com/en/user-guide-getting-started.html  

To facilitate this, you need to create a Snowflake user for Weld, as well as create a default role for that user. Furthermore you need to assign the following privileges to this users default role. It is important that you create a new user, and a new role for this, and only attach this policy to that role. This ensures that Weld can only access what is required, and helps secure your Snowflake account.

## Setting Up - The Fast & Easy Way
>Want to run all commands yourself? Sure, just skip ahead to the **Setting Up - The Manual Way** section.

Don't want to do all this yourself? We got your back! Just run our script in your Snowflake instance as accountadmin, and it will be ready for Weld!

**1.** To run the script, go and log in to the *classic console* in snowflake ![enter image description here](https://lh3.googleusercontent.com/pw/AM-JKLXNC0uH8lYRGwdAIKeDbh-uvg91hD9tJFEDvTMH4aV9zruMuXAMQiDa3wk8M8W2VD1eCbd8r5PhZbw23ybB1LR4bBVWFTud8ynjY_5_jLOesxwxir5SDcu-6liApibkKBn4s8VoMW9_7g28yibKjAU=w1254-h680-no?authuser=0)
>If this is your first time in the Classic Console, minimize the 'welcome' window.

**2.** Paste in the script found below:  

		-- create variables for role / user / database (needs to be uppercase for objects)
		set user_weld_password = 'SET_PASSWORD_HERE';

		set user_weld = 'WELD_USER';	   
		set role_weld = 'WELD_ROLE';

		set database_landing = 'WELD_LANDING';
		set database_models = 'WELD_MODELS';

		set warehouse_name = 'compute_wh';


		use warehouse identifier($warehouse_name); 

		-- change role to securityadmin for user / role steps
		use role securityadmin;

		-- create role for weld
		create role if not exists identifier($role_weld);

		-- create user for weld
		create user if not exists identifier($user_weld)
			password = $user_weld_password
			default_role = $role_weld 
			must_change_password = false;

			grant role identifier($role_weld) to user identifier($user_weld);

			grant usage on warehouse identifier($warehouse_name) to role identifier($role_weld);
		-- change role to sysadmin for database steps
		use role sysadmin;

		-- create databases
		create database if not exists identifier($database_landing);
		create database if not exists identifier($database_models);

		-- grant role access to landing and model databases

		grant CREATE SCHEMA, USAGE
			on database identifier($database_models)
			to role identifier($role_weld);

		grant CREATE SCHEMA, USAGE
			on database identifier($database_landing)
			to role identifier($role_weld);

		use role accountadmin;

		grant CREATE TABLE, CREATE VIEW, USAGE
			on future schemas
			in database identifier($database_models)
			to role identifier($role_weld);

		grant CREATE TABLE, CREATE VIEW
			on future schemas
			in database identifier($database_landing)
			to role identifier($role_weld);	
			
		USE DATABASE WELD_MODELS;
		CREATE SCHEMA WELD_RAW;

**3.** Change the  **SET_PASSWORD_HERE** value on line 2, to a password you decide. Make sure to note it somewhere safe, as it is needed later. 
It should look like this. 
`set user_weld_password = 'the password you decide here';`

**4.** check the **All Queries**, and press **Run**

![enter image description here](https://lh3.googleusercontent.com/pw/AM-JKLV0zTfbd206H_fAL-Wy-J3hW4TS8otL3o-kngS9XOveFCl45y01cuUiAD2GbP3cgxaDL_UKYedbfajIy6XDO29WcNBXt8JVMn1e0c7ZzAEIlsZ_7WEh_BFectF2muh2DHm_FVnP2-dZlEixCSTz2bw=w1354-h496-no?authuser=0)

The bottom of your query editor should now show the following: 

![enter image description here](https://lh3.googleusercontent.com/pw/AM-JKLUtx6Z6O-78_aJkN-DowQFcBjdahrA4zNRcLEFg1LpOd3B7IVBX1_i4_10Kjeu6yZQDK50DftjyOJJPa5nJVZBWLCiAb9k8oHcgo40Z1ThqKORlbCn1PEXK0OXYuJtXD9xczY07DAmAN0Z-CQR2nNg=w1054-h720-no?authuser=0)

Did you successfully run the script? 
Great! You can now skip ahead to the **Wheres My Credentials** part of this documentation, sign in with your snowflake credentials and begin your Weld journey. If you didn't do the setup script, continue below:

## Setting Up - The Manual Way
Start by creating a role and a user for Weld.
The default role of the weld user will need access to the following databases. You might have to create them

 - WELD_MODELS
 - WELD_LANDING

It can be done by granting the following privileges for each of the above databases: 

`GRANT CREATE SCHEMA, USAGE ON DATABASE databaseName TO ROLE roleName`  
`GRANT CREATE TABLE ON FUTURE SCHEMAS IN DATABASE databaseName TO ROLE roleName`  
`GRANT CREATE VIEW ON FUTURE SCHEMAS IN DATABASE databaseName TO ROLE roleName`  

Also make sure to create the follwing schema in the **WELD_MODELS** db
`USE DATABASE WELD_MODELS;`
`CREATE SCHEMA WELD_RAW;`  

Lastly, the default role must also have **USAGE** rights to the warehouse 
`GRANT USAGE ON warehouseName TO ROLE roleName`

**note:** please remember to assign your created role to the weld user, as well as assign it as the default role for that user.

You are now all set up, and ready to go! Fill in your snowflake credentials, and start welding! 

## Wheres my credentials?
**Account**  
Account can be found in the URL of your snowflake instance, in the following format: 
`app.snowflake.com/region.cloudProvider/identifier`. 
Rearranged into the correct format for weld would be: 
`identifier.region.cloudprovider`

**Warehouse**  
the default warehouse is `COMPUTE_WH`

**Database**  
The database should be `WELD_LANDING`

**User name**  
The default User name is `WELD_USER`

**Password**  
This is the password you should have decided on yourself.