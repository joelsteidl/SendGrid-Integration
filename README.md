SendGrid Integration
======================

This project is not affiliated with SendGrid, Inc.

This module works with Backdrop mail system to offer a flexible way of sending
emails out of Backdrop. Emails are sent through SendGrid's cloud-based email
delivery services by using their Web API (RESTful) that allows for quick and
fast email transactions out of a Backdrop website instead of slow SMTP
transactions.

Requirements
------------

This module requires that the following modules are also enabled:

* [X Autoload](https://backdropcms.org/project/xautoload)

Optional

 * [Mail System](https://backdropcms.org/project/mailsystem)
 * [Maillog / Mail Developer](https://backdropcms.org/project/maillog)

Installation
------------

- Install this module using the official Backdrop CMS instructions at
  https://backdropcms.org/guide/modules.

Installing this module requires some more advanced knowledge, use of the command
line and the use of [Composer](https://getcomposer.org/).

1. Install the libraries with composer on the command line:
```
cd path/to/sendgrid_integration
composer install --no-dev
```
2. Enable the SendGrid Integration module

3. Create or use an existing SendGrid API Key.

4. Configure your SendGrid API-Key Administration > Configuration > Web services in admin/config/services/sendgrid

5. Drupal's Mailsystem needs to be changed to use SendGrid. This can be done with
one Mailsystem module or hardcode in settings.php:
```
$conf['mail_system'] = array('default-system' => 'SendGridMailSystem');
```
If you
want it all to run through Sendgrid then you set the
   System-wide default MailSystemInterface class to "SendGridMailSystem". As an
   example, see this [image](https://www.drupal.org/files/issues/sengrid-integration-mailsystem-settings-example.png).

Documentation
-------------

If sending email fails with certain (pre-defined) response codes the message be
added to Cron Queue for later delivery. In order for this to function, you must
configure Cron running period and when it is possible also add your Backdrop
site to crontab (Linux only), read more about cron at
https://backdropcms.org/cron.

If you would like a record of the emails being sent by the website, installing
Maillog (https://www.backdropcms.org/project/maillog) will allow you to store
local copies of the emails sent. Sendgrid does not store the content of the
email.

In order to send HTML email. Your installation of Drupal must generate an email
with the proper headers. Sendgrid Integration modules looks for the content type
of the email to be set to "text/html" in the header
(i.e. "Content-Type"="text/html").
A text version of the email is also sent at the same time.

If the message does not have the content type set to "text/html" the message
will be stripped of any tags and converted to text.

We do not recommend MIMEmail module because it sets the content-type header of a
message to "multipart/mixed" instead of strictly "text/html". In addition, the
MIMEmail module attempts to template emails and include inline CSS that is not
compatible with SendGrid template system. If you want to use
MIMEmail, we suggest using the
[SMTP module](https://backdropcms.org/project/smtp) and not this module.

Information about the Sendgrid PHP Library is availabe on Github:
https://github.com/taz77/sendgrid-php-ng

Additional documentation is located in the Wiki:
https://github.com/backdrop-contrib/sendgrid_integration/wiki/Documentation.

Issues
------

Bugs and Feature requests should be reported in the Issue Queue:
https://github.com/backdrop-contrib/sendgrid_integration/issues.

Current Maintainers
-------------------

- [Joel Steidl](https://github.com/joelsteidl).
- Seeking additional maintainers.

Credits
-------

- Ported to Backdrop CMS by [Joel Steidl](https://github.com/joelsteidl).
- Originally written for Drupal by
  [Brady Perignon](https://www.drupal.org/u/perignon).
- Originally written for Drupal by
  [Henri Hirvonen](https://www.drupal.org/u/exlin).

License
-------

This project is GPL v2 software.
See the LICENSE.txt file in this directory for complete text.
