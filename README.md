# Vagrant LAMP stack
A dead-simple LAMP stack without any bells and whistles for your basic Linux/Apache/MySQL/PHP install, using Ansible for provisioning.

This was based on [Vagrant LAMP Stack](https://github.com/MiniCodeMonkey/Vagrant-LAMP-Stack), but since it hasn't worked since Chef dev tools came out (weird Chef dependencies were not kept to date), I rolled my own.

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
vagrant plugin install vagrant-hostmanager
```

## Installation

Install the requirements above.

Clone this repository

    $ git clone ?? project_name

Place your website in the `??` folder

## Usage
Start the VM

	$ cd project_name
	$ vagrant up

You can now access your project at [http://projectname.local](http://projectname.local)

![Screenshot of up-and-running server](http://i.imgur.com/TP1i9Zd.png)

### Database dump import
Chef will automatically try to import the database dump specified by the filename set in the `:db_dump` option of your Vagrantfile.

If you are using the default configuration, just create a `dump.sql` file in the root directory with your table structure and/or content and it will be imported automatically when you run `vagrant up`.

## Installed Server
* Ubuntu Vivid Vervet (15.04)

## Installed software
* Apache 2
* MySQL
* PHP 5.4 (with mysql, curl, mcrypt, memcached, gd)
* memcached
* postfix
* vim, git, screen, curl, composer

## Default credentials
### MySQL
* Username: root
* Password: root
* Host: localhost
* Port: 3306

**Note:** Remote MySQL access is enabled by default, so you can access the MySQL database using your favorite MySQL client with the above credentials (and using e.g. *projectname.local* as hostname).

### Memcached
* Port: 11211


[![Bitdeli Badge](https://d2weczhvl823v0.cloudfront.net/MiniCodeMonkey/vagrant-lamp-stack/trend.png)](https://bitdeli.com/free "Bitdeli Badge")

