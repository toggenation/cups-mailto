cups-mailto
===========

modified http://cups-mailto.sourceforge.net/ script which runs pdftotext to attach PDF text content to body of email.

The default iformation attached to the email by cups-mailto isn't what I wanted so I have modified it.

I am doing the following:

EDI Application on Windows 2012 Server ==> Prints to a Samba Shared Printer named "PDF-Convertor" 
on Debian 6.0.8 configured for mailto:// backend

The mailto file is located in /usr/lib/cups/backend

The mailto file is mostly standard except it runs pdftotext with the "-layout" option to extract the text and 
format it as closely as possible to the orinal PDF

Further setup information is at http://cups-mailto.sourceforge.net/

I used the PDF-Convertor.ppd located at the above site, but the pstopdf filter mentioned 
is already a standard part of cups
