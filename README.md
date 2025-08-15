# civictheme_xb_preview

A development version of Civictheme UI Kit and theme to test XB integration.

## Installation:

Follow the steps from https://github.com/phenaproxima/xb-demo project (copied below) to install the xbdemo using ddev. From there, this repo can be integrated.

```bash
mkdir xb-demo
cd xb-demo
ddev config --project-type=drupal11 --docroot=web
ddev composer create-project phenaproxima/xb-demo --stability=dev
ddev drush si -y
# ddev drush user:login xb/xb_page/1/editor

# These commands are civictheme specific
# Get repository
git clone git@github.com:civictheme/civictheme_xb_preview.git ./civictheme_xb_preview
# Create symlinks
cd ./recipes
ln -s ../civictheme_xb_preview/recipes/civictheme_xb_demo ./civictheme_xb_demo
ln -s ../civictheme_xb_preview/recipes/civictheme_xb_demo_media ./civictheme_xb_demo_media
cd ../web/themes/contrib
ln -s ../../../civictheme_xb_preview/themes/civictheme_xb ./civictheme_xb
# Install recipe
cd ../../../
ddev drush recipe /var/www/html/recipes/civictheme_xb_demo
ddev drush cr

# Now log in
ddev drush user:login xb/xb_page/2/editor
```
