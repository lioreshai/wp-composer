# wp-composer
wp-composer allows you to convert your existing WordPress site (or new WordPress project) into a version-controlled Git repository where WordPress is installed as a Composer dependency.

The power of this package lies in the ability to create version-controlled WordPress project where rapid, collaborative theme and plugin development is made easy. **This method is not well-suited for WordPress sites which depend heavily on third-party plugins and themes which need to be updated through wp-admin.**

## What does wp-composer change in WordPress?
1. Makes a better directory structure for your WordPress project which looks like this:
  * /public/ - The publicly-accessible root
  * /public/wp - WordPress files installed by Composer (not included in version control)
  * /public/wp-content - The _wp-content_ directory contains all the plugins and themes unique to your WordPress project. Typically, when migrating an existing WordPress site to wp-composer, you would install using a "**composer install**" and copy the contents of your existing _wp-content_ to this directory
  * / - The project root is behind the publicly accessible web root and contains any other dependencies you might want to require in the _vendor_ directory.
2. Improvement in WordPress configuration. In the project root you'll find a local-config.sample.php - the modified wp-config.php located in the _public_ directory will look first for a production-config.php and then fall back on a local-config.php. This will allow you to seamlessly manage your local/production configuration.

## Installation
1. Clone this repo into a fresh directory
2. Copy the contents of your _wp-content_ directory into _public/wp-content_
3. Modify the .gitignore according to which parts of _wp-content_ you'd like to include in version control. **By default the _wp-content/uploads_ directory is ignored**
4. Copy local-config.sample.php to local-config.php and migrate your configuration values
5. Run _composer install_

### Recommendations
* In his article on [using Composer to manage Git](https://deliciousbrains.com/using-composer-manage-wordpress-themes-plugins/), Gilbert Pellegrom discusses using composer to manage the installation of WordPress plugins and themes. This package doesn't proclude you from doing so, but I've found it is much easier to solely deal with plugin and theme installations in the traditional way.
* The installation of plugins and themes often alters tables in the database. If your _public/wp-content/plugins_ is included in version control, take care to install the plugin on both environments (from within the WordPress admin).

## Acknowledgements
* This package was created based on [part 4](https://deliciousbrains.com/install-wordpress-subdirectory-composer-git-submodule/) of Gilbert Pellegrom's 4 part series on working with WordPress in Git and Composer.

#### Liore Shai
* liore@a.ai
* https://liore.com