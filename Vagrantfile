# -*- mode: ruby -*-
# vi: set ft=ruby :

# All Vagrant configuration is done below. The "2" in Vagrant.configure
# configures the configuration version (we support older styles for
# backwards compatibility). Please don't change it unless you know what
# you're doing.
Vagrant.configure("2") do |config|
  # The most common configuration options are documented and commented below.
  # For a complete reference, please see the online documentation at
  # https://docs.vagrantup.com.

  # Every Vagrant development environment requires a box. You can search for
  # boxes at https://vagrantcloud.com/search.
  config.vm.box = "ubuntu/xenial64"   # Done this part

  # Disable automatic box update checking. If you disable this, then
  # boxes will only be checked for updates when the user runs
  # `vagrant box outdated`. This is not recommended.
  # config.vm.box_check_update = false

  # Create a forwarded port mapping which allows access to a specific port
  # within the machine from a port on the host machine. In the example below,
  # accessing "localhost:8080" will access port 80 on the guest machine.
  # NOTE: This will enable public access to the opened port
  # config.vm.network "forwarded_port", guest: 80, host: 8080

  # Create a forwarded port mapping which allows access to a specific port
  # within the machine from a port on the host machine and only allow access
  # via 127.0.0.1 to disable public access
  # config.vm.network "forwarded_port", guest: 80, host: 8080, host_ip: "127.0.0.1"

  # Create a private network, which allows host-only access to the machine
  # using a specific IP.
  # config.vm.network "private_network", ip: "192.168.33.10"
  config.vm.network "private_network", ip: "192.168.30.30"

  # S3 Configuration

  # Create a public network, which generally matched to bridged network.
  # Bridged networks make the machine appear as another physical device on
  # your network.
  # config.vm.network "public_network"

  # Share an additional folder to the guest VM. The first argument is
  # the path on the host to the actual folder. The second argument is
  # the path on the guest to mount the folder. And the optional third
  # argument is a set of non-required options.
  # config.vm.synced_folder "../data", "/vagrant_data"
  config.vm.synced_folder "./magento_dev/", "/var/www/html/magento_dev"
  #config.vm.synced_folder "./magento_without_data", "/var/www/html/magento2_without_data"
  #config.vm.provision "shell", inline: "sudo ln -s /vagrant_magento_source/ /var/www/html"
  # config.vm.provision "shell", inline: "sudo mkdir -p /var/www/html/magento2"
  # config.vm.synced_folder "../B05032-Magento-Box", "/var/www/html/magento-dev" # , owner: "magento_user", group: "www-data", type: "rsync"
  # config.vm.share_folder "mag-dev", "/var/www/html/magento2", "../B05032-Magento-Box", :owner => "magento_user", :group => "www-data"
  #config.vm.provision "shell", inline: "sudo chown -R root:www-data /var/www/html/magento2"  

  # Provider-specific configuration so you can fine-tune various
  # backing providers for Vagrant. These expose provider-specific options.
  # Example for VirtualBox:
  #
  config.vm.provider "virtualbox" do |vb|
  #   # Display the VirtualBox GUI when booting the machine
      vb.gui = false
  #
  #   # Customize the amount of memory on the VM:
      vb.memory = "4096"
  end
  #
  # View the documentation for the provider you are using for more
  # information on available options.

  # Enable provisioning with a shell script. Additional provisioners such as
  # Puppet, Chef, Ansible, Salt, and Docker are also available. Please see the
  # documentation for more information about their specific syntax and use.
  # config.vm.provision "shell", inline: <<-SHELL
  #   apt-get update
  #   apt-get install -y apache2
  # SHELL
  # config.vm.provision "file", source: "~/.gitconfig", destination: ".gitconfig"
  config.vm.provision "shell", inline: "sudo apt-get update"
  # Apache Provisioning start here
  config.vm.provision "shell", inline: "sudo apt-get -y install apache2"

  # PHP Provisioning start here
  config.vm.provision "shell", inline: "sudo apt-get -y install software-properties-common"
  config.vm.provision "shell", inline: "sudo add-apt-repository ppa:ondrej/php"
  config.vm.provision "shell", inline: "sudo apt-get update"
  config.vm.provision "shell", inline: "sudo apt-get -y install php7.1"
  config.vm.provision "shell", inline: "sudo apt-get -y install libapache2-mod-php7.1 php7.1-common php7.1-gmp php7.1-curl php7.1-soap php7.1-bcmath php7.1-intl php7.1-mbstring php7.1-xmlrpc php7.1-mcrypt php7.1-mysql php7.1-gd php7.1-xml php7.1-cli php7.1-zip"
  config.vm.provision "shell", inline: "sudo apt-get -y install zip unzip php7.0-zip"
  #config.vm.provision "shell", inline: "sudo apt-get -y install php7.1-xdebug phpunit"
  config.vm.provision "shell", inline: "sudo a2enmod rewrite"
  config.vm.provision "shell", inline: "sudo service apache2 restart"

  # MySQL Provisioning start here
  config.vm.provision "shell", inline: "sudo debconf-set-selections <<<'mysql-server mysql-server/root_password password m@g1t786'"
  config.vm.provision "shell", inline: "sudo debconf-set-selections <<<'mysql-server mysql-server/root_password_again password m@g1t786'"
  config.vm.provision "shell", inline: "sudo apt-get install -y mysql-server mysql-client"
  config.vm.provision "shell", inline: "sudo service mysql start"
  config.vm.provision "shell", inline: "sudo update-rc.d mysql defaults"

  # Install GIT , CURL and COMPOSER 
  config.vm.provision "shell", inline: "sudo apt-get -y install curl git"
  config.vm.provision "shell", inline: "sudo curl -s https://getcomposer.org/installer | php"
  config.vm.provision "shell", inline: "sudo mv composer.phar /usr/local/bin/composer"

  # Clear the Magento Installation directory /var/www/html/magento2
  


end


