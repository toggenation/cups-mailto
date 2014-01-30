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

Use the PDF-Convertor.ppd downloaded from http://cups-mailto.sourceforege.net. I loaded it using system-config-printer. (it will end up in /etc/cups/ppds)

Further setup information is at http://cups-mailto.sourceforge.net/

How I use it
------------
I have some Windows EDI software configured to automatically print whenever a new order comes in.

The Windows computer is configured with \\debian_box\PDF-Convertor as it's default printer for the user that is running the EDI Software.

On the debian_box I have added a user account with the same name as the one running on the Windows box. The mailto script matches the incoming user with the local user to deliver mail. I have added an entry into /etc/aliases that redirects that users email to an email address of my choosing.







