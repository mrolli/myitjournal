# Webapp Stack

## Goal

This project's goal is to setup a local LAMP-Stack to be able to install a PHP/MySQL-based
web application onto it. To learn a different aspects the following assumptions are made:

* We pretend that the app will use quite some resources and therefore we need two linux servers:
    * *webserver* will run the Apache webserver and listen to HTTP requests (80 first, 443 at a later stage)
    * *dbserver* is running the Mariadb database server and act as the database backend for the webapp
* The webserver needs to provide PHP 8 to be able to run PHP-based webapplications
* Communication to the Webserver is finally secured using SSL, which makes a x509-certificate necessary

You are free to choose the webapplication that you want to deploy. There are many PHP-webapplications out
there. A save choice might be a forum or a content management system, i.e. [Flarum], [phpBB], [Wordpress], ...

*[LAMP]: Linux-(MySQL|Mariadb)-PHP Stack*

[Flarum]: https://flarum.org/
[phpBB]: https://www.phpbb.com/
[Wordpress]: https://de.wordpress.org/

## Setup Local Virtual Servers

As we setup the local severs with the help of vagrant, we will generate at least a Vagrantfile but for
sure also scripts and the like. Therefore it's best to start off with a versioned project dir, always,
and keep in mind to create commits based on steps we successfully carry out.

!!! abstract "Project initialization and local server setup"
    * Create a project dir
    * Initialize an empty git repo (use `gh repo` for that and enjoy its convienience :smile:)
    * Create the Vagrantfile
      * Initialize a new Vagrantfile using the vagrant command
      * Work with the rockylinux 8 basebox provided by bento (bento/rockylinux-8)
      * Configure 2 severs in this Vagrant file: webserver and dbserver

Consider that the two linux server have to communicate with each otherh. Realize this using the private
networking feature by adding an additional netowrk interface to the server.

At least the webserver has to be reachable from the webbrowser on your laptop. Therefore you have to **forward ports 80 and 443**
of the guestOS to you laptop, good local ports on the host OS could be 8080 and 8443.  
(Optionally) forward the port 3306 to the host OS, i.e. to 8306.

## Provision the Databse Server

!!! abstract "Database server installation"
    * **Install** the database server - either [MariaDB] or [MySQL] - using `dnf`
    * **Configure** the database server using the ini files and
        * set default charet to *utf8mb4*
        * set default collation *utf8mb4_unicode_ci*
    * **Secure** the server for production use - try to figure out, which steps to carry out!

Is it working? Is it no longer possible to connect using user `root` with an empty password?

[MariaDB]: https://mariadb.org/
[MySQL]: https://dev.mysql.com/

## Provision the Webserver

### Install Apache

### Install PHP

!!! abstract "Installing PHP-8"
    Next we want to be able to run web applciations written in PHP. The latest available major verison of PHP is version 8.

    !!! warning "PHP-8 not available"
        Rocky Linux 8 comes with PHP-7.2.24, which is too old for most modern PHP webapps.

    So, in order to have a current PHP-8 version, you either compile your own PHP (discouraged and not the way to go here) or
    use some other source of RPMs, e.g. a third-party yum repository. Search the net to find a reliable source for PHP-RPMs
    for RHEL-7 and derivates like Rocky Linux (Hint: Ratatouille).

    Place the following script to `/var/www/html/index.php` and surf to https://localhost:8080

## Deploy an Application
