cups-mailto
===========

How it differs from the original
-------------------------------
This is a modified version of the http://cups-mailto.sourceforge.net/ 'mailto' script which runs `pdftotext -layout` to insert as text the content of the attached PDF into the body of email.

It also removes the ugly smbprn.00000000 from the Subject of the email and filename of the attached PDF.

Install and config
------------------
This script is used on a Debian 6.0.8 box

The mailto file is copied to /usr/lib/cups/backend 

Use the PDF-Convertor.ppd downloaded from http://cups-mailto.sourceforge.net. I loaded it using system-config-printer. (it will end up in /etc/cups/ppds)

Further setup information is at http://cups-mailto.sourceforge.net/

How I use it
------------
I have some Windows EDI software configured to automatically print whenever a new order comes in.

The Windows computer is configured with \\debian_box\PDF-Convertor as it's default printer for the user that is running the EDI Software.

On the debian_box I have added a user account with the same name as the one running on the Windows box. The mailto script matches the incoming user with the local user to deliver mail. I have added an entry into /etc/aliases that redirects that users email to an email address of my choosing.


Old Readme from Sourceforge
---------------------------

CUPS mailto backend
cups-mailto is a backend for the Common Unix Printing System.

The mailto backend emails the filtered output to the user who requested the print job. The print job's output will be MIME attached to the email. cups-mailto is written in Python and depends on /usr/bin/file --mime-type to generate the MIME type for this attachment.

It also needs a working email system (MTA) that supports the "-t" switch for /usr/sbin/sendmail.

Installation
Place the downloaded file mailto into the backend directory of your CUPS installation (usually /usr/lib/cups/backend) and restart the CUPS daemon.

The mailto backend identifies itself as SMTP to the CUPS configuration system.

Setup
To add a "printer" using the mailto backend you can use lpadmin like this: lpadmin -p <printername> -m laserjet -v mailto

There is no need for a printer URI because the mailto backend uses the username of the print job. In fact you can specify anything as printer URI when using the web interface for CUPS.

Usage
The mailto backend knows about two command line options passed via lp:

-o mailto=user@domain.com
Sets the To:-address of the email generated to user@domain.com. This makes it possible to send the output to another email address instead using the username of the job's requestor.
-o mailfrom=user@domain.com
Sets the From:-address of the email generated to user@domain.com. This makes it possible to fake the sender. The standard sender address is "lp".
If mailto is set mailfrom will bet set to the requestor's username.

If both options are given and do not equal to the username of the requestor a custom X-CUPS-mailto-started-by:-header is added that contains the requestor's username for tracking purposes.

PDF Generation
One purpose of the mailto backend is to deliver a PDF generation service where the users get the PDF output back in an email.

To accomplish this you need a pstopdf filter for CUPS with the accompanying PPD.

There are some issue with the Postscript output of some Windows printer drivers. We have best results with the HP LaserJet 8500 Color tuned to archive mode and with Ctrl-D turned off before and after the job.






