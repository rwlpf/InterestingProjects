## SSIS

Using SSIS extracted data from cloud based help desk the company had not access to the backend database.  So had to generate a custom URL which included a jql statement, that would return the records required. 

Using a custom script task with code in C# able to execute the custom generated URL to download a Json file. Once the Json file was downloaded the file was processed and the data output from the task to other tasks in the package.

The data would be placed into the stating database, using another custom script using C# a hash value would be added to the record.  This hashvalue would be used to confirm if the record had been updated.  This was implemented to improve the time taken to process the updates.

## Database migration
Required to migrate from SQL 2012 instance using two database servers, the HA was set up using database mirroring.  The client databases needed to be migrated to SQL 2016 the server pair would use Windows Failover Cluster and Basic Availablity Groups (BAG) for HA. Additionally, the migration had to be carried out whilst the application was being used by the client or with minimum downtime.

There was several parts to this task
 - Check full backup of database has been taken
 - Create back up of existing client database
 - Break database mirroring
 - Restore the client database to new server
 - Create Basic Avialablity Group (BAG)
 - Add restored databases on the newserver to the newly created BAG
 - Update relevant config files on the web server for application
 
This was done using a Powershell script, using DBATools module, TSQL and a few moments of frustration.
Each client database was migrated at a time, typically the downtime was approximately 30 mins, the entire process took about 15 mins.  The additional time was to complete a required set of tests to confirm the migration has completed successfully.

## SQL Bites Training

After working in the company for some time, looking at the client databases and dealing with helpdesk calls, it became clear that whilst the developers had fantastic C# and Java skills, I realised that there was some scope for teaching some SQL.  So I volunteered to do some SQL teaching monthly for the developers.  The training started with the syntax of a simple select statement and reviewing joins.  Later lessons looked at Group By, Windows Functions, cursors, temporary objects, and Apply keyword.

## Managing SQL server transactional replication
Two of the largest and most important clients, had requested, that they required access to a dedicated database for reporting purposes.  They specified that data had to be in sync with the primary application database, ideally a realtime representation.  I made several different suggestions, such as log shipping or other similar processes.  The requirement to have as near to realtime I was informed, was non-negotiable.

One technology which I was aware of is database replication which met all the requirements the client had laid out.  As a result, I worked with the systems administrator to set up and then maintain transactional replication for these two clients. 

## Delivery of the Redgate SQL clone and masking project
One of the bottlenecks when diagnosing some issues for clients, developers required a backup copy of the client's application database.  To get the database restored to suitable location could be a long process to complete depending on the size of the database.  The management team decided to purchase the Redgate SQL Clone and masking software, which I had recommended having seen it demonstrated at SQLBits conference.  So the task was delegated to me to configure the software, coordinating deployment and training the developers.   

A large charitable organaistion choose Grant Tracker software to replace the old software they had used to manage their grants.  Part of the migration project requirements was to migrate the data from the existing system mainframe system to the SQL server environment.   Some of the data once migrated required to be adjusted.  To achieve several times, I was given the task work with the client to make changes to the data.  The way that I achieved this required the use of various SQL scripts written to identify and make the required adjustments to the data.

## Data Dictonary
The schema used for the Grant Tracker application is somewhat complex and takes some time to comprehend fully, even for an experienced database developer. One approach used is the creation of "reporting views" these are made available to the client,  With the specific purpose of exposing data to the clients so that our clients could use them as a data source for reports.  Over time the application developed, so developers added additional fields to the reporting views.  As developers added more functionality to the application, the developers added more reporting views.
The responsibility to maintain and communicate a data dictionary to each customer who requested one was down to me.  This task is complicated by the issue that each customer may only have access to a subset of the reporting views.  Developers would check in changes to production, and my team would not always be told about the additions or changes.   So I created an SSIS package which would monitor a specific database for any changes to the reporting views.  These changes would be logged with the date and nature of the change.  In the database which recorded the change, details regarding the reporting view and specific field were recorded.  With this database, we could give the client a complete reporting view data dictionary as and when required.

## Dedicated reporting data for client
One of the clients contacted us regarding accessing application data for reporting purposes.  Previously we had implmented this for other clients using transactional replication the database for this was placed on to a dedicated server.  This client did not have the budget for a dedicated server they were very keen to have a suitable data made available. After some disucssions with the client we established that they did not require real-time data in the reporting database, or access outside of working hours.

We decided to create a maintance plan this would peform several tasks each night.
One of the clients contacted us regarding accessing application data for reporting purposes.  Previously we had implemented this for other clients using transactional replication, the reporting (subscriber) database for this was on a dedicated server.  This client did not have the budget for a dedicated server; they were very keen to have the data made available. After some discussions with the client, we established that they did not require real-time data in the reporting database, or access outside of working hours.

We decided to create a maintenance plan; this would perform several tasks each night.

Step 1 - Remove the previous backup file.
Step 2 - Backup Production DB to the reporting server
Step 3 - Restore Production DB to the reporting server.
Step 4 - Delete users from Restored DB on the reporting server.
Step 5 - Add the account that will be used to access the database only grant select permissions to the reporting views (RV's)
