biz.jmaconsulting.mte
=====================

Mandrill Transactional Emails Extension for CiviCRM

See https://github.com/JMAConsulting/biz.jmaconsulting.mte/wiki/About-mte-%28Mandrill-Transactional-Emails%29

Installation:

Install CiviCRM 4.2+
====================

1. Setup Mandrill

Register for or login to your Mandrill account at https://mandrillapp.com/login/
Create API key as follows:
Click on Settings (Gear icon top-right) >> SMTP & API Credentials.
Click +New API Key
Note SMTP Credentials, or leave window tab open for a few steps.



2. Setup From Email address

If you have not already done so, go to:
Administer >> Communications >> From Email Addresses.
Enter a from address you would like to display to users for CiviCRM emails, for example, info@yourorg.org.


3. Setup Outbound Email

Administer >> System Settings >> Outbound Email (SMTP/Sendmail).
Click on SMTP.
Enter the following:
SMTP Server: smtp.mandrillapp.com
SMTP Port: 587
Authentication: Yes
SMTP Username: (from step 1 above, e.g. mail@yourorg.org)
SMTP Password: (copy and paste API Key from step 1 above, e.g. 12345678-abcd-1234-efgh-123456789012)
Click Save & Send Test Email
Check that you received the test email.


4. Setup Extensions Directory 

If you have not already done so, go to:
Administer >> System Settings >> Directories
Set an appropriate value for CiviCRM Extensions Directory.
For example, for Drupal, /path/to/drupalroot/sites/all/modules/Extensions/
In a different window, ensure the directory exists and is readable by your web server process.
Click Save.


5. Setup Extensions Resources URL

If you have not already done so, go to:
Administer >> System Settings >> Resource URLs
Beside Extension Resource URL, enter an appropriate values such as 
http://yourorg.org/sites/all/modules/Extensions/


6. Install Mandrill Transactional Emails extension

Administer >> Customize Data and Screens >> Manage Extensions.
Beside Mandrill Transactional Emails, click Install.
Review the information, then click Install.


7. Configure Webhooks for Mandrill

To complete this step successfully, your website must be accessible from the Internet so that Mandrill can post to it. 
So if you are running a test site locally on your laptop that other computers cannot access, this step will fail.
Login or go to your Mandrill account at https://mandrillapp.com/login/
Click on Settings (ie the Gear icon on the top-right) >> Webhooks
Click on +Add a Webhook
Click to enable all entries _except_ Message Is Sent:
- Message Is Soft-bounced
- Message Is Clicked
- Message Recipient Unsubscribe
- Message Is Bounced
- Message Is Opened
- Message Is Marked As Spam
- Message Is Rejected
In Post to URL, enter the resource URL from 5. above, followed by biz.jmaconsulting.mte/CRM/Mte/Page/callback.php. 
For example: http://yourorg.org/sites/all/modules/Extensions/biz.jmaconsulting.mte/CRM/Mte/Page/callback.php


