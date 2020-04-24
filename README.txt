= Drupal Perimeter Defence =

This module attempts to block hackers from accessing your website.

Hackers sometimes scan your website for known vulnerabilities by
requesting paths to pages that are known to have once contained
these vulnerabilities. These requests can be easy to recognise when
hackers brute-force the scan by asking for paths that are uncommon to
Drupal.

For example, /user and /sites are commonly requested Drupal-paths, and
should not cause alarm if requested. On the other hand, common Wordpress
paths are /wp-admin and /wp-content, so if a visitor is requesting these
on a Drupal-based website, this may indicate that said visitor is a hacker.

In turn this makes it possible to automate banning such hackers from
accessing the website altogether by adding their IP address to Drupal's
built-in banned addresses table.

This is a Drupal 7 version of the Drupal Perimeter Defence module. It
was derived from the Drupal 8 original.

== Installation ==

Install as any other module.

== Usage notes ==

* It is possible to lock yourself out of your website by using this
module. If that happens, use a (remote) database manager to get into the
database, go to the table 'blocked_ips' and remove the records that contain
your computer's IP address.

* If you need to unblock someone else, go to
/admin/config/people/ip-blocking and delete their IP address. This is also
where you can ban users manually.

== Developer notes ==

* This module operates on a low level (two degrees of separation from
index.php). If you need to patch the module, try and stay away from
perimeter_page_delivery_callback_alter() and add your changes to
perimeter_html_delivery_callback() instead.

