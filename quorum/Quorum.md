
## Azure Data Factory

  
Whilst having a conversation with one of the members of the marketing department. One of the weekly tasks is to extract data manually from three systems for social media metrics: Twitter, LinkedIn, and Google Analytics. So what I have done is to start creating an Azure Data Factory Pipeline, which will extract the data and place it in an Azure SQL database.

The Twitter extraction pipeline has been completed. This will get the required details of Azure Key Vault, where the details are securely held. The required credentials are then passed to the necessary ADF components. Next, using a Twitter RestfulAPI call passed a bearer token to authenticate the call. The JSON returned is then passed to a stored procedure to insert the data into a table in SQL Server. This will insert records of any new tweets created since the latest one was recorded in the table.

The next step is to get the non-public metrics for any less than 30 days old tweet. To do this, that requires Auth 1.0a credentials. To achieve this, a python script was created, which is called using an Azure Function. The function accepts as a parameter which is the tweet ID to return the metrics for, the JSON that returned is the passed to stored procedure and the appropriate record updated with the metrics

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

  

**Defender project**

  

One of our teams, had been able to secure a managed security service. Providing various reports based on the standard reports provided by the Defender portal. The security lead would spend up to 5 days per month producing the reports. We took original KQL queries then divided the work into parts. The data engineering wrote python notebooks to extract data from the Defender API automatically on a daily basis. The data

  
  
  

**Syngerist**
The financial controller had chosen to move on to another role. As a result the utilisation report which had been manually created each month required to be reproduced.  The data director gave me the a copy of the original excel spreadsheet to create the report from.

Data was extracted on a daily basis to a SQL server which was in its own VNET. This required an Azure VM to be set up in the same VNET. With a on premise Power BI Data gateway running on the Azure VM to allow a connection to the data source on the SQL server database.  This had to be configured to run in the Quorum Power BI service, which was then extracted via a Dataflow.

  
  

**Utilisation**

**Sales Pipeline**

  

**PMO project**

  
  

**Non-Profit organisation**

Client had a Dataflow with numerous dependences which is key to day to day running of the organisation. This Gen 1 dataflow took over 2.5 hours to complete. This consumed considerable amounts of the Fabric capcity. Following a review of the Dataflow we determine that it could run faster if translated to a SQL server Stored procedure. Following analysis and extensive test the dataflow and all the required dependencies were migrated.

 - When run in an Azure SQL database S0 (lowest tier) it took 4 mins 30 seconds 
 -   When run in an Azure SQL database S4 (DB was scaled up to this for data loads) it took 1 mins 30 seconds

Approximately 250k rows outputted.

**RLS Project**
The our client wanted to create POC, we given a relatively straightforward specification. For this project a person (tradesperson) would visit a clients house. 

The client wanted to the tradesperson to see who they were visiting. Only showing their records of the visit, start and end time, address details etc. They should only see their own records.

At the same the person who was receiving a visit would only be able to see those tradesperson who was visit them.  Only showing their records of the visit, start, end time, name of the tradesperson.

To add to this, client add the requirement that those persons being visited should be able to see a picture of the tradesperson who was visiting. We used a Power BI report to allow use to implement the RLS. So we had to embed the pictures into the report. The pictures of the tradesperson could not be stored on a publicly accessible URL. This for reasons for GDPR and security reasons. So we converted the images to Base64 encoder [Base64 Image Encoder](https://www.base64-image.de/). Next the resulting string was stored in a VARCHAR field in SQL server, which we were then able to display on the report securely.