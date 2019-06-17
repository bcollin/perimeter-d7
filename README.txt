= Drupal Perimeter Defence =

This module attempts to block hackers from accessing your website.

Hackers sometimes scan your website for known vulnerabilities by
requesting paths that hide these vulnerabilities. These requests can be
easy to recognise when hackers brute-force the scan by asking for paths
that are uncommon to Drupal.

In turn this makes it possible to automate banning such hackers from accessing
the website altogether by adding their IP address to Drupal's built-in banned
addresses table).

This is the Drupal 7 version of the Drupal Perimeter Defence module. It
was derived from the Drupal 8 original.

== Installation ==

Install as any other module.

== Usage notes ==

* It is possible to lock yourself out of your website by using this
module. If that happens, use a (remote) database manager to get into the
database, go to table 'blocked_ips' and remove the records that contain
your computer's IP address.

* If you need to unblock someone else, go to
/admin/config/people/ip-blocking and delete their IP address. This is also
where you can ban users manually.

* In order to test the module without locking the tester out of the
website, add the following to the site's settings.php file:

  // Perimeter module: enable test mode.
  $conf['perimeter_test_mode'] = TRUE;

In order to switch the test mode off, comment out or remove the above line
from the site's settings.php file or change its value from TRUE to FALSE.

== Developer notes ==

* This module operates on a low level (two degrees of separation from
index.php). If you need to patch the module, stay away from
perimeter_page_delivery_callback_alter() and make your changes in
perimeter_html_delivery_callback() instead.

