# Get Familiar with Important Apache Files and Directories

Now that you know how to manage the service itself, you should take a few minutes to familiarize yourself with a few important directories and files.


 ## Content


+ ```/var/www/html```: The actual web content, which by default only consists of the default Apache page you saw earlier, is served out of the /var/www/html directory. This can be changed by altering Apache configuration files.


## Server Configuration

+ ```/etc/apache2```: The Apache configuration directory. All of the Apache configuration files reside here.


+ ```/etc/apache2/apache2.conf```: The main Apache configuration file. This can be modified to make changes to the Apache global configuration. This file is responsible for loading many of the other files in the configuration directory.


+ ```/etc/apache2/ports.conf```: This file specifies the ports that Apache will listen on. By default, Apache listens on port 80 and additionally listens on port 443 when a module providing SSL capabilities is enabled.


+ ```/etc/apache2/sites-available/```: The directory where per-site "Virtual Hosts" can be stored. Apache will not use the configuration files found in this directory unless they are linked to the sites-enabled directory (see below). Typically, all server block configuration is done in this directory, and then enabled by linking to the other directory with the a2ensite command.


+ ```/etc/apache2/sites-enabled/```: The directory where enabled per-site "Virtual Hosts" are stored. Typically, these are created by linking to configuration files found in the sites-available directory with the a2ensite. Apache reads the configuration files and links found in this directory when it starts or reloads to compile a complete configuration.


+ ```/etc/apache2/conf-available/, /etc/apache2/conf-enabled/```: These directories have the same relationship as the sites-available and sites-enabled directories, but are used to store configuration fragments that do not belong in a Virtual Host. Files in the conf-available directory can be enabled with the a2enconf command and disabled with the a2disconf command.


+ ```/etc/apache2/mods-available/, /etc/apache2/mods-enabled/```: These directories contain the available and enabled modules, respectively. Files in ending in .load contain fragments to load specific modules, while files ending in .conf contain the configuration for those modules. Modules can be enabled and disabled using the a2enmod and a2dismod command.


## Server Logs


+ ```/var/log/apache2/access.log```: By default, every request to your web server is recorded in this log file unless Apache is configured to do otherwise.


+ ```/var/log/apache2/error.log```: By default, all errors are recorded in this file. The LogLevel directive in the Apache configuration specifies how much detail the error logs will contain.

