# FEBNotificationManager
A utility for sending out email reminders for in-progress forms that are stale.

Usage: NotificationManager [-options]

* -host <host> = The FEB server including the port(i.e. http://myserver.com:9080). Note: Do NOT include a trailing slash.

-context <context> = The application context (i.e. forms-basic). Note: OPTIONAL, if not specified then "forms-basic" will be used.  Do NOT include a preceding or trailing slash.
* -dir <dir> = The directory to save the attachments (i.e. c:\temp\myAttachments).

-ignoreSSL <true/false> = OPTIONAL. If true, bypass SSL verification and you must specify the protocol.

-protocol <protocol> = OPTIONAL. The security communication protocol to use when connecting to the server (i.e. TLS, TLSv1.2, SSL, etc).
* -usr <user> = The username that will be used to authenticate to the FEB REST API (i.e. cdawes@ca.ibm.com)
* -pwd <pwd> = The password for the specified user
* -notifAPPID <app_id> = The APP ID of the application where the notifications records are stored

-action <action> = Supported actions are 'deleteALL' - will delete all the notification records

-debug = Prints debug messages to the log file

-days = Previous notifications that are older than x days will be deleted. Default is 30.

-byAppID = Used for testing a notification of a specific application id.  Use this if you want to just run notifications on ONE app rather than all those registered.

-noEmail = Runs the utility but does not create any notifcation records and does not send emails (for debugging)

-cfgURL = The URL of the FEB form that holds the config information

-fik = The value to use for the freedomIdentifyKey

-usage or -help or -h = this message


# Deployment Instructions
1. Deploy .nitro_s file to your FEB server
2. Edit the FEB Application
  i) Click on Settings.
  ii) Click on Registered Forms (under Services on the left-side of the screen).
  iii) Edit the "Get Fields for Form" service by clicking the gear.
  iv) On the Inputs tab, edit the service URL by clicking on the gear (under the URL).
  v) In the URL field, change the "http://localhost:9080" to the host and port of your server.
  vi) Click OK (ignore any warning that may appear and click OK to save the change).
  vii) Deploy the application.
3. Save the .jar, .properties and .bat to the server where you will run the utility.

# Run-time Instructions
1. Launch the "F_RegisteredForms" form.
2. Enter the application ID of the app that you want to monitor for reminder notifications.
3. For each stage in that application add a row to the "Stages and People to Notify" table.
4. Enter the Forms ID.

5. Enter the Stage ID that you want to monitor.  
6. Determine who the "actor" is in that stage, that is the person that will receive the reminder notifications.  The form should have a field that contains that person's name and email.  Enter the ID of those fields in the "Actor Name" and "Actor Email" fields.
7. Enter the IDs of the fields that contain the information about the original submitter of the form into the "Submitter Name" and "Submitter Email" fields.
8. Enter the number of days to wait before sending out a reminder notifcation. Default is 7 days).
9. OPTIONAL. Specify the number of days to wait for subsequent notifcations. Default is 7 days).
10. OPTIONAL.  If your form has a field that captures a "due date", enter that ID in the "DueDate Field ID" field.
11. OPTIONAL.  If you want to configure a custom email, check the "Custom Email" check box and fill out the Subject and Body.
12. Modify the .bat script. Update the location of Java on your system, the username and password to use, the server host name and any other parameters of choice.
13. OPTIONAL. Setup the .properties file to define the level of logging.
14. The .jar, .properties and .bat should be in the same directory.
15. When ready run the .bat, which will start the notification process.
