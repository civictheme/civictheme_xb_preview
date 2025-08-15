# civictheme_xb_preview

A development version of Civictheme UI Kit and theme to test XB integration.

## Installation:

Use the commands below to install a clean site with `civictheme_xb_preview`:

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

These can be copied into an `install.sh` file and run as `bash install.sh` for easy setup.

These steps are based on https://github.com/phenaproxima/xb-demo, but with the `civictheme_xb_preview` specific implementation added. 

### Troubleshooting

If you run into issues installing with the above commands please check the following:

1. `ddev` will complain if it finds another `xb_demo` project already installed. In this case you can either remove your existing installation (`ddev delete`) and try again, or run the all the commands below `# These commands are civictheme specific` to integrate `civictheme_xb_preview` into your existing project.
2. The `civictheme_xb_demo_media` recipe expects the imported media assets to have a particular entity id, so if you've added the `civictheme_xb_preview` to your existing project which has new media items, you may encounter an error that the `target_id` of an image was not found.
