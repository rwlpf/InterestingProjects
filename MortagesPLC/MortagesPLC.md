**

## Daily reports
Part of the daily routine for the role which I was recruited for was to extract data from the SQL server instance, place the data into excel spreadsheets.   These excel spreadsheets were then emailed to various people in the organisation.  During the interview process, I made various suggestions on how to automate the process, all of which had been tried or could not be implemented.

The report had to be presented in an excel document; this was a format which had been used for a considerable time and could not be changed.  The graphics used in the spreadsheet these could not be changed either so exporting from SSRS to Excel was not an option.  No additional software could be installed on the server which was hosting the SQL server instance. 

After some time, a solution was arrived at after some trial and error.  Using an SSIS package, the data was extracted from the database.  A new excel spreadsheet file was generated from a template.  An SQL statement was used to place the data into a specific named range in the excel spreadsheet.  When the user opens the excel spreadsheet, this action would execute some VBA code.   The primary purpose of this code was a format the numbers to the format the user expected. Once the code was run, a flag would be set to ensure the code was not to run again.

This was maybe the least elegant solution that I have put in place.  From the customers' point of view, it was seamless the customer was none the wiser as to how the report arrived.  The report was delivered in the same way it had been when manually created.  That said that was at least 30 mins time each weekday saved that could be used for other purposes.  Also, this was a task which several people before me had attempted to deliver and were unable to.

**
## Quarterly Report Regulatory Report

Every quarter there was a report which had to be prepared to for sending the Financial Conduct Authority (as it was known then).  The first time that I completed the report, it took me three full days to work through the instructions to compile the report.   After some work before I left the report was produced automatically in approximately 45 mins and emailed to the relevant.  This again freed up more time to find other tasks which could be improved.
**
