# -*- mode: ruby -*-
# vi: set ft=ruby :

# General project settings
#################################

# IP Address for the host only network, change it to anything you like
# but please keep it within the IPv4 private network range
ip_address = "172.22.22.22"

# The project name is base for directories, hostname and alike
project_name = "projectname"

# MySQL and PostgreSQL password - feel free to change it to something
# more secure (Note: Changing this will require you to update the index.php example file)
database_password = "root"

# All Vagrant configuration is done below. The "2" in Vagrant.configure
# configures the configuration version (we support older styles for
# backwards compatibility). Please don't change it unless you know what
# you're doing.
Vagrant.configure(2) do |config|
  # The most common configuration options are documented and commented below.
  # For a complete reference, please see the online documentation at
  # https://docs.vagrantup.com.

  # Every Vagrant development environment requires a box. You can search for
  # boxes at https://atlas.hashicorp.com/search.
  # https://vagrantcloud.com/ubuntu
  # Need to use trusty for now as vivid has a hostname control masking
  # https://github.com/mitchellh/vagrant/issues/5673
  # https://help.ubuntu.com
  config.vm.box = "ubuntu/trusty64"

  # Disable automatic box update checking. If you disable this, then
  # boxes will only be checked for updates when the user runs
  # `vagrant box outdated`. This is not recommended.
  # config.vm.box_check_update = false

  # Create a forwarded port mapping which allows access to a specific port
  # within the machine from a port on the host machine. In the example below,
  # accessing "localhost:8080" will access port 80 on the guest machine.
  #config.vm.network "forwarded_port", guest: 80, host: 8080

  # Create a private network, which allows host-only access to the machine
  # using a specific IP. Use hostmanager to have custom domain added to host
  # machine's host file
  #config.vm.network "private_network", ip: "192.168.33.10"
  config.hostmanager.enabled = true
  config.hostmanager.manage_host = true
  config.vm.define project_name do |node|
    node.vm.hostname = project_name + ".local"
    node.vm.network :private_network, ip: ip_address
    node.hostmanager.aliases = [ "www." + project_name + ".local" ]
  end
  # probably need to move this and set enabled = false to fix for vivid
  config.vm.provision :hostmanager
  # VVV uses Hostsupdater https://github.com/cogitatio/vagrant-hostsupdater
  # however that doesn't look like it updates the /etc/hosts of the client
  # systems.
  # Consider hosts-provisioner?
  # https://github.com/mitchellh/vagrant/wiki/Available-Vagrant-Plugins

  # Create a public network, which generally matched to bridged network.
  # Bridged networks make the machine appear as another physical device on
  # your network.
  #config.vm.network "public_network"

  # Share an additional folder to the guest VM. The first argument is
  # the path on the host to the actual folder. The second argument is
  # the path on the guest to mount the folder. And the optional third
  # argument is a set of non-required options.
  # config.vm.synced_folder "../data", "/vagrant_data"

  # Provider-specific configuration so you can fine-tune various
  # backing providers for Vagrant. These expose provider-specific options.
  # Example for VirtualBox:
  #
  # config.vm.provider "virtualbox" do |vb|
  #   # Display the VirtualBox GUI when booting the machine
  #   vb.gui = true
  #
  #   # Customize the amount of memory on the VM:
  #   vb.memory = "1024"
  # end
  #
  # View the documentation for the provider you are using for more
  # information on available options.

  # Define a Vagrant Push strategy for pushing to Atlas. Other push strategies
  # such as FTP and Heroku are also available. See the documentation at
  # https://docs.vagrantup.com/v2/push/atlas.html for more information.
  # config.push.define "atlas" do |push|
  #   push.app = "YOUR_ATLAS_USERNAME/YOUR_APPLICATION_NAME"
  # end

  # Enable provisioning with Ansible
  config.vm.provision "ansible" do |ansible|
    ansible.playbook = "playbook.yml"
  end
end
