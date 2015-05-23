# TGIFramework Vagrant

A LAMP stack necessary to bootstrap [TGIFramework](https://github.com/tychay/TGIFramework) development via Vagrant using VirtualBox as the provider and
Ansible as the provisioner.

## Requirements
* [Apple XCode](https://developer.apple.com/xcode/)
* [VirtualBox](https://www.virtualbox.org)
* [Vagrant](http://vagrantup.com)
* [Ansible](https://devopsu.com/guides/ansible-mac-osx.html)
```shell
$ sudo easy_install pip
$ sudo -H pip install ansible --quiet
```
* [vagrant-hostmanager](https://github.com/smdahlen/vagrant-hostmanager)
```shell
$ vagrant plugin install vagrant-hostmanager
```

## Installation and Usage

Install the requirements above.

Clone this repository

```shell
$ git clone git@github.com:tychay/tgif_vagrant.git tgivagrant
```

Clone TGIFramework into tgif

```shell
$ cd tgivagrant
$ git clone git@github.com:tychay/TGIFramework.git
```

Make (or clone) your project into a directory and edit the first lines in
`VagrantFile` to point `project_name` to the directory of the cloned project.
Then run `vagrant up`. The following example installs the sample project:

```shell
$ git clone git@github.com:tychay/tgiframework_sample.git sample
$ cp Vagrantfile.dist Vagrantfile
$ nano Vagrantfile
$ vagrant up
$ vagrant reload --provision
```

(Currently you have to run the provisioning twice due to a restart bug in nginx
pecl interaction.) You can now access your project at
[http://sample.dev/](http://sample.dev/) (or whatever you named it to if you
changed `host_name` in the `Vagrantfile`).
TGIFramework samples should successfully run in
[http://tgif.dev/](http://tgif.dev/).

![Screenshot of up-and-running server](http://i.imgur.com/TP1i9Zd.png)

### Database dump import
TODO:
Chef will automatically try to import the database dump specified by the filename set in the `:db_dump` option of your Vagrantfile.

If you are using the default configuration, just create a `dump.sql` file in the root directory with your table structure and/or content and it will be imported automatically when you run `vagrant up`.

## Installed Server
* Ubuntu Trusty Tahir (14.04)

## Installed software
* Nginx
* MySQL (actually MariaDB)
* PHP 5.6 (with mysql, curl, mcrypt, memcached, gd, tidy, apcu, gmp, igbinary)
* PHP dev extensions (xdebug, xhprof, inclued)
* memcached
* postfix
* vim, git, screen, curl, composer, yuicompressor

## Default credentials
### MySQL
* Username: root
* Password: root
* Host: localhost
* Port: 3306

**Note:** Remote MySQL access is enabled by default, so you can access the MySQL database using your favorite MySQL client with the above credentials (and using e.g. *projectname.local* as hostname).

### Memcached
* Port: 11211

[![Bitdeli Badge](https://d2weczhvl823v0.cloudfront.net/tychay/tgif_vagrant/trend.png)](https://bitdeli.com/free "Bitdeli Badge")