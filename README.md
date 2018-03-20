# FEBNotificationManager
A utility for sending out email reminders for in-progress forms that are stale.

#Deployment Instructions
1. Deploy .nitro_s file to your FEB server
2. Save the .jar, .properties and .bat to the server where you will run the utility.

#Run-time Instructions
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
