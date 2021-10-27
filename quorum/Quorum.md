## Azure Data Factory

Whilst having a conversation with one of the members of the marketing department.  One of the weekly tasks is to extract data manually from three systems for social media metrics: Twitter, LinkedIn, and Google Analytics.  So what I have done is to start creating an Azure Data Factory Pipeline, which will extract the data and place it in an Azure SQL database.

The Twitter extraction pipeline has been completed. This will get the required details of Azure Key Vault, where the details are securely held.  The required credentials are then passed to the necessary ADF components. Next, using a Twitter RestfulAPI call passed a bearer token to authenticate the call.  The JSON returned is then passed to a stored procedure to insert the data into a table in SQL Server.  This will insert records of any new tweets created since the latest one was recorded in the table.

The next step is to get the non-public metrics for any less than 30 days old tweet.  To do this, that requires Auth 1.0a credentials.  To achieve this, a python script was created, which is called using an Azure Function.  The function accepts as a parameter which is the tweet ID to return the metrics for, the JSON that returned is the passed to stored procedure and the appropriate record updated with the metrics

## Power Bi 
