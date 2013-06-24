drupalspinner
=============

Drupal Spinner (a.k.a. makeisland) is a tool to spin up new drupal
multi-site instances that have islandora in place and configured to
use a common Fedora et al install.

This tool relies on a particular approach to drupal
multi-site. There needs to be a primary drupal site that's used as the
shared/canonical source for all user info (username, passwords, auth
info, etc.) and which has the islandora modules installed (though the
site need not have them activated - the modules just need to be in the
sites/all tree). Each new island (i.e. new drupal multi-site) looks to
the primary site tables for user data.

This tool uses drush and bash script to create the new islands, so
drush needs to be installed.

There are 4.5 main parts to the tool:
      DEFAULT_SETTINGS.txt - the template settings file that's used for each island (this is shared here as an example file)
      ISLAND.ROOT.cfg - a bunch of configuration data that's common to all islands (this is shared here as an example file)
      ISLAND.site.islandname.cfg - configuration data specific to islandname (i.e. one of these exists for each island)
      (ISLAND.BASE.cfg) - an example/template for a specific ISLAND.islandname.cfg file)
      makeisland - the bash script that does all the work

To spin up a new islandora-enabled site:

0.a) make sure all the islandora modules are correctly installed (not necessarily activated) in the base site; you only need to do this the first time (i.e. this is part of setting up the base drupal install)
0.b) make sure the drupalspinner has all the base data it needs (copy ISLAND.ROOT.cfg.example to ISLAND.ROOT.cfg and edit all the appropriate settings in that file)

1) copy ISLAND.BASE.cfg to a new file called ISLAND.site.mynewsite.cfg, where mynewsite is the (computer) name of your new site
2) edit ISLAND.mynewsite.cfg to fill in the appropriate values
3) $ makeisland mynewsite

and that should be it.

TODO: expand and refine this file / instructions


