Title: Owncloud 7 - custom mail messages
Modified: 2015-01-18 22:00
Category: External memory
Tags: owncloud
Authors: Věroš Kaplan
Summary: How to change mail message sent by OwnCloud sharing 
Slug: owncloud-share-by-mail
X-Status: testing

[OwnCloud 7][owncloud] came packed with lots of new features. Many happy users of
OwnCloud uses it as file transfer solution (me including).

The default mail message sent to the user receiving the file is a bit unformal
and is considered unpolite. It starts *Hey there*. How to change the message? 

The good news is file is stored in  `core/templates/mail.php` (HTML version) 
and `core/templates/altmail.php` (plain text version). 
mc
If you change that templates, the messages can be a bit more polite.

[owncloud]: http://www.owncloud.com/

