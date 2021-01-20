**KRISP application**
Microsoft Access Database Application
The company hired me to work within the hospital design team, and my role was to maintain the Microsoft Access database.  When I started with the company, the team used an Access database to store room datasheets.  This link gives some details regarding what is stored on a typical room datasheet - https://www.designingbuildings.co.uk/wiki/Room_data_sheet.

One of the goals was to maintain a central library of equipment components that could be used across multiple projects.  Reports which were generated had to be A3 landscape.

More projects choose to use the application to manage the room datasheets for their project as time went on.   As a result of this demand, several features were added to the application.

The application was split into two parts, those were;
 1. Front end which contained the GUI and application code
 2. Dedicated backend database
 
The front end part of the application was installed on a clients PC; it would check for a newer version when the application was started.  If there was a newer version available, it would be downloaded and installed automatically.  The user could also connect to different backend databases using a straightforward menu.

There were at least two custom components for each project; those are the room data sheet input forms and reports.  Each project had a dedicated backend database which contained a configuration table, detailing the specific form and report for that project.  So this meant that a single front end was maintained and distributed to each user.  When updates or updates were deployed, all users received the same single front end update.  The dedicated backend database was stored on a shared network drive; this location was backed-up and managed by a central IT resource. 

For each room datasheet, there was a corresponding room layout drawing.  The room layout drawing and the room datasheet would be reviewed and edited.  Part of the review process, required a person to ensure the number of equipment items on the room layout drawing, matched the room datasheet for the corresponding room.  For anyone involved, this was both labour and time-intensive process.

The company used a third-party application to add the equipment graphics to the room layout drawings.  This 3rd party application used an access database to store a count of each room's equipment graphics.  Using some VBA code and SQL, I added a class to the Krisp application to reconcile equipment levels between the two applications.  The result was a time saving of approximately 90% compared to the previous manual process.