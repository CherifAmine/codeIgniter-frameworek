Vagrant.configure("2") do |config|
# Select Ubuntu box (default OS)
  config.vm.box = "ubuntu/bionic64"

# Set up the network to allow you to access the local server
  config.vm.network "private_network", ip: "192.168.33.10"

# Installation commands to be Execute when Vagrant is running
  config.vm.provision "shell", inline: <<-SHELL
    # System update
    sudo apt-get update

    # Install Apache and PHP
    sudo apt-get install -y apache2
    sudo apt-get install -y php libapache2-mod-php php-mysql

    # Restart Apache
    sudo service apache2 restart
  SHELL

  # Share the project folder between your system and the default folder
  config.vm.synced_folder ".", "/var/www/html"
end
