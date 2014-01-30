cups-mailto
===========

modified http://cups-mailto.sourceforge.net/ script which runs pdftotext to attach PDF text content to body of email.

The default iformation attached to the email by cups-mailto isn't what I wanted so I have modified it.

This is used on a Debian 6.0.8 box

The mailto file is copied to /usr/lib/cups/backend 

Use the PDF-Convertor.ppd downloaded from the above site, I load it using system-config-printer.

The mailto file is mostly standard except it runs pdftotext with the "-layout" option to extract the text and 
format it as closely as possible to the orinal PDF

Further setup information is at http://cups-mailto.sourceforge.net/

is already a standard part of cups
