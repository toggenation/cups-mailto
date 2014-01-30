cups-mailto
===========

This is a modified version http://cups-mailto.sourceforge.net/ script which runs pdftotext to attach PDF text content to the body of email.

The default information inserted in to the body of the email by cups-mailto isn't what I wanted so I have modified it.

This is used on a Debian 6.0.8 box

The mailto file is copied to /usr/lib/cups/backend 

Use the PDF-Convertor.ppd downloaded from http://cups-mailto.sourceforege.net. I loaded it using system-config-printer. (it will end up in /etc/cups/ppds)

The mailto file is mostly standard except it runs pdftotext with the "-layout" option to extract the text and format it as closely as possible to the orinal PDF text layout.

Further setup information is at http://cups-mailto.sourceforge.net/


