## **Data Scotland**

As part of the organising committee, we wanted to use images which included the speakers' name, session title, location and time.  All of this data was in the Sessionize.com application.  

 1. Some python to extracts the data  from  Sessionize.com, the data the code writes a table in SQL server
 2. Using the OPENJSON function query the data stored in the table to extract the required information
 3. Finally using SSRS report builder, created a report which used the SQL Server table to create a single page for each speaker. The report was rendered as PDF and converted to JPEG to be used as the image for the tweets.

Importing sessions from sessionise restful_api imported the JSON file into SQL server and populated tables
See - https://github.com/rwlpf/Sessionize_Json_Data_to_MS_SQL_2016 for the code used to import the data.

## Web Scraping Tour De France results
One of my passions outside of technology is cycling, and this has lead to an interest in the Tour De France, which is one of the most recognisable professional cycle races in the world.  There are some datasets which list the winners and times.  That said these do not include all the finishers for each stage of the race, typically they only have the top 10 finishers and results.  
Whilst looking at various websites, I found https://www.procyclingstats.com which lists all the finishers for each stage going back to the first race.  So the next step was to look at using some web scraping technology to extract the results.  Finally, I settled on using Python using Beautiful Soup to scrape the website.  The data which is scraped from the website is then written to a set of tables hosted in a SQL server database.