CONTENTS OF THIS FILE
---------------------

 * summary
 * configuration

SUMMARY
-------

This module provides the ability to perform simple security restrictions to
objects within Islandora. Please note that it does not take advantage of XACML
so it'd likely be optimal to lock down the 8080 port on the webserver that
houses Solr and Fedora.  It will not play well with islandora_ip_embargo.
It will also break islandora_xml_site forms with redirects.
Objects can be in one of three states:
  * Public
    * Normal access rules apply and there is no change to the display of the
    object.

  * Restricted
    * Only users with explicit permission can see the object. All other users
    only see the object's label and a general access denied thumbnail.

  * Hidden
    * Only users with explicit permission can see the object. All others are
    unaware that the object exists.

If no state is present in the RELS-EXT an object is considered to be in the
"Public" state.

Roles and users are multisite aware but object state is not.

CONFIGURATION
-------------

The Solr RELS-EXT field for pulling allowed users needs to be configured if
the desired filtering functionality of Solr results is to work correctly. These
are expected to be multivalued string fields. The redirect URL is also
configurable.
