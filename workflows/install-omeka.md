# Install Omeka

Omeka is a flexible content management system that makes it possible to curate a collection of Dublin Core metadata records and publish them online. Neatline is built as a modular add-on that sits on top of Omeka, similar to a plugin for Wordpress or a module for Drupal. Before installing Neatline, you'll first need a working installation of Omeka.

## Before you get started

Omeka and Neatline are written on the LAMP stack (Linux, Apache, MySQL, PHP), which is supported by almost any all commercial web hosting providers. Before you start, you'll need:

 - A hosting environment that supports PHP and MySQL. This could be a commercial provider like Webfaction or Dreamhost, and you can also install an local development server like MAMP on you own computer if you just want to test-drive Omeka and Neatline offline.

 - A way to transfer files onto your server space and make simple text edits to configuration files. If you don't have direct ```ssh``` access to the server, a simple FTP client like [FileZilla](http://filezilla-project.org/) works well.

 - Login credentials for a MySQL user and a clean database for the Omeka installation. If you don't already have a database user account, most commercial hosting providers provide access to point-and-click database administration tools like phpMyAdmin that make it possible to create databases and users.

Once you're ready, head over to the [official Omeka documentation](http://omeka.org/codex/Installation).

## Preventing Mixed Content Errors in HTTPS

Omeka will attempt to detect which protocol (http or https) a site visitor is using so that it can use the same protocol in retrieving asset files like the ones Neatline provides. In certain hosting environments, Omeka may fail to detect the use of https, resulting in mixed content errors when the page tries to load Neatline assets over http. If you support https in your installation, you can avoid these errors by adding the following lines to the .htaccess file in your Omeka directory:

```
SetEnv HTTPS "on"
<FilesMatch ".(eot|ttf|otf|woff)">
	Header set Access-Control-Allow-Origin "*"
</FilesMatch>
```
