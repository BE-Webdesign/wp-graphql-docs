# Installing
# Requirements

WordPress 4.7+
PHP 5.4+ (this is a must cut off as the library this project uses is 5.4+)
Composer (Composer is required to install the dependencies for this plugin)

### WordPress Setup

[Download WordPress:](https://wordpress.org/download/)
You can download WordPress manually and follow the wonderful instructions on
.org to figure out how to get a [WordPress development environment up and running.](https://developer.wordpress.org/themes/getting-started/setting-up-a-development-environment/)

[VVV:](https://github.com/Varying-Vagrant-Vagrants/VVV)
If you are a more experienced user or want to try something new, I highly recommend
VVV. VVV comes with all of the tools you need. Essentially you install [Vagrant](https://www.vagrantup.com/)
and a VM. I like [VirtualBox VM](https://www.virtualbox.org/) but Vagrant
supports many others.

[Chassis:](https://github.com/Chassis/Chassis)
Chassis is along the same line as VVV, but is more modularized. It requires more
set up than VVV in some ways but, is faster to boot and sometimes you don't need
all of the bells and whistles, and if you do well there are some awesome
extensions for Chassis.

Once you have WordPress installed and running you will want to clone this git
repository or download the zip and install it in your WordPress installs plugins
directory. [Here is a great guide for installing plugins.](https://codex.wordpress.org/Managing_Plugins#Manual_Plugin_Installation)
This plugin is not yet ready for the WordPress.org plugin repository but one of
the goals for this project is to make it compatible.

### Using Composer

Composer comes with things like VVV and is why VVV is a great choice for running
a developer environment. Composer is basically a tool that helps manage packages
and dependencies for PHP projects. Composer is used for three things on this
plugin: load WebOnyx GraphQL library, install PHPUnit for unit testing, and
finally it will auto-load all of the necessary files for the plugin.

When you have composer running on your developer environment you will want to
locate the directory for wp-graphql. Once you are in the wp-graphql directory
you will want to enter:

```
composer install
```

This will install all of the dependencies for the project and add a vendor
folder to the project containing these dependencies. When adding new files you
may notice that they are not loading into the project. If you follow the
namespaces already set up, you can easily load the new file by running:

```
composer dump-autoload
```

This will regenerate all of the auto loaded files bringing in the ones that are
missing. The top level namespace is `BEForever\WPGraphQL`.

**The plugin should now be functional!**
