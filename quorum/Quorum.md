## Azure Data Factory

Whilst having a conversation with one of the members of the marketing department.  One of the weekly tasks is to extract data manually from three systems for social media metrics: Twitter, LinkedIn, and Google Analytics.  So what I have done is to start creating an Azure Data Factory Pipeline, which will extract the data and place it in an Azure SQL database.

The Twitter extraction pipeline has been completed. This will get the required details of Azure Key Vault, where the details are securely held.  The required credentials are then passed to the necessary ADF components. Next, using a Twitter RestfulAPI call passed a bearer token to authenticate the call.  The JSON returned is then passed to a stored procedure to insert the data into a table in SQL Server.  This will insert records of any new tweets created since the latest one was recorded in the table.

The next step is to get the non-public metrics for any less than 30 days old tweet.  To do this, that requires Auth 1.0a credentials.  To achieve this, a python script was created, which is called using an Azure Function.  The function accepts as a parameter which is the tweet ID to return the metrics for, the JSON that returned is the passed to stored procedure and the appropriate record updated with the metrics

## Power Bi 

*A Quorum Journey*
During the pandemic Quorum wanted to encourage
In this session, you will learn how Quorum used the Power Platform to create a virtual road trip across the continental United States to keep employees active and engaged during the pandemic. The team faced a difficult challenge: to create an engaging and interactive experience that could be shared with everyone in the company, regardless of their technical expertise.

Using their extensive experience with user interface design and data storytelling, the Marketing, Apps Dev, and Data Teams at Quorum produced an elegant and easy to use Power BI dashboard showing the daily progress towards the goal. The data was also distributed to Teams and SharePoint for anyone to see. Further, through the Power Platform, the team created interactive postcards as they crossed each state boundary on their USA road trip.

The road trip is now in its 5th iteration, and the team is excited to share their story of how they combined Teamwork and Technology to build this virtual journey.

In this session, you will learn:

    How to use the Power Platform to create engaging and interactive experiences
    How to design user interfaces that are easy to use for everyone
    How to tell stories with data using Power BI
    How to use the Power Platform to share information and collaborate with others

This session is ideal for anyone who wants to learn more about the Power Platform and how it can be used to create innovative and engaging solutions.

*Defender project* 

One of our teams, had been able to secure a managed security service. Providing various reports based on the standard reports provided by the Defender portal. The secuirty lead would spend up to 5 days per month producing the reports. We took orginal KQL queries then divided the work into parts. The data engineering wrote python notebooks to extract data from the Defender API automatacailly on a daily basis. The data 



Syngerist


Utilisation 
Sales Pipeline

PMO project


*Non-Profit organsisation*
Client had a Dataflow with numerous dependances which is key to day to day running of the organsation.  This Gen 1 dataflow took over 2.5 hours to complete. This consumed considerable amounts of the Fabric capcity. Following a review of the DataFlow we determine that it could run faster if translated to a SQL server Stored proceedure. Following analysis and extenstive test the dataflow and all the required depedancies were migrated.
When run in an Azure Sql database S0 (lowest tier) it took 4 mins 30 seconds
When run in an Azure Sql database S4 (db was scaled up to this for data loads) it took 1 mins 30 seconds
Approxiately 250k rows outputed.

RLS Project