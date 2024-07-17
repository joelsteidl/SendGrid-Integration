SendGrid Integration Module
---------------------------

This project is not affiliated with SendGrid, Inc. If you want more info about
SendGrid services, contact [SendGrid](https://sendgrid.com).

This module uses a wrapper library for the SendGrid API. At the moment the
wrapper library is for V2 of the API. V3 upgrade is being developed.

Requirements
------------

This module requires that the following module is also enabled:

* [Mail System](https://backdropcms.org/project/mailsystem)

One of the following two is required:

* [Composer Manager](https://backdropcms.org/project/composer_manager) - if you
  want to manage libraries across multiple modules with Composer. See the
  [module's README](https://github.com/backdrop-contrib/composer_manager/blob/1.x-2.x/README.md)
  for more detailed information.
* [X Autoload](https://backdropcms.org/project/xautoload) - if you want to use
  the bundled `vendor/` directory with this module.

Optional

 * [Maillog / Mail Developer](https://backdropcms.org/project/maillog)

Installation
------------

1. Navigate to Functionality Tab and enable SendGrid Integration in the Mail category.

2. Configure your SendGrid API-Key in admin/config/services/sendgrid

3. Confirm that the mail system is setup to use SendGrid for how you wish to run
   you website. If you want it all to run through SendGrid then you set the
   System-wide default MailSystemInterface class to "SendGridMailSystem".

Documentation
------------

Additional documentation is located in [the Wiki](https://github.com/backdrop-contrib/sendgrid_integration/wiki).

Issues
------

Bugs and feature requests should be reported in [the Issue Queue](https://github.com/backdrop-contrib/sendgrid_integration/issues).

Current Maintainers
-------------------

- [Michael R. Bagnall](https://github.com/ElusiveMind).
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
