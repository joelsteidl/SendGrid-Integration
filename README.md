

FUNCTIONALITY
--------------------------------------------------------------------------------
This module overrides default email sending behaviour and sending emails through
SendGrid Transactional Email service instead. Emails are sent via a web service
and does not function like SMTP therefore there are certain caveats with other
email formating modules. Read below for details.

Failures to send are re-queued for sending later. Queue of failed messages are
run on a 60 minute interval.

REQUIREMENTS
--------------------------------------------------------------------------------
Module dependencies:

Drupal's Mailsystem needs to be changed to use SendGrid.  This can be done with
one of:

* Mailsystem module.  A GUI for controlling which Mailsystem is used for which
emails.
* Hardcode in settings.php:

```
$conf['mail_system'] = array('default-system' => 'SendGridMailSystem');
```

This module requires that the SendGrid API Wrapper class is available. You may
accomplish this with:

* X Autoload module (see below).
* Roll your own.

X Autoload
--------------------------------------------------------------------------------




INSTALLATION
--------------------------------------------------------------------------------
Installing this module requires some more advanced knowledge, use of the command
line and the use of Drush.

1. Download and install
[X Autoload module](https://backdropcms.org/project/xautoload).
2. Move this folder under modules directory of your installation,
example modules/contrib
3. Install the libraries with composer:
```
cd path/to/sendgrid_integration
composer install --no-dev
```
4. Navigate to Modules and enable SendGrid Integration in the Mail category.

5. Configure your SendGrid API-Key in admin/config/services/sendgrid

6. Confirm that the mail system is setup to use Sendgrid for how you wish to run
   you website. If you want it all to run through Sendgrid then you set the
   System-wide default MailSystemInterface class to "SendGridMailSystem". As an
   example, see this [image](https://www.drupal.org/files/issues/sengrid-integration-mailsystem-settings-example.png).

HTML Email
--------------------------------------------------------------------------------
In order to send HTML email. Your installation of Drupal must generate an email
with the proper headers. Sendgrid Integration modules looks for the content type
of the email to be set to "text/html" in the header (i.e. "Content-Type"="text/html").
A text version of the email is also sent at the same time.

If the message does not have the content type set to "text/html" the message
will be stripped of any tags and converted to text.

We do not recommend MIMEmail module because it sets the content-type header of a
message to "multipart/mixed" instead of strictly "text/html". In addition, the
MIMEmail module attempts to template emails and include inline CSS that is not
compatible with SendGrid template system. If you want to use
MIMEmail, we suggest using the [SMTP module](https://backdropcms.org/project/smtp)
and not this module.

If you want to work on a solution for MIMEmail and contribute it back to the
module, we gladly accept community contributions!


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

 * [Bar](https://github.com/backdrop-contrib/bar)
 * [Baz](https://github.com/backdrop-contrib/baz)

Installation
------------

- Install this module using the official Backdrop CMS instructions at
  https://backdropcms.org/guide/modules.

- Visit the configuration page under Administration > Configuration > Category >
  Foo (admin/config/category/foo) and enter the required information.

- Any additional steps.

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

- [Chris Brown](https://github.com/username).
- [Pat Smith](https://github.com/username).
- Seeking additional maintainers.

Credits
-------

- Ported to Backdrop CMS by [Alex Baker](https://github.com/username).
- Originally written for Drupal by [Taylor Young](https://github.com/username).
- Based on the [MagicalCode project](https://github.com/example).
- Sponsored by [TechNoCorp](https://example.com)

License
-------

This project is GPL v2 software.
See the LICENSE.txt file in this directory for complete text.
