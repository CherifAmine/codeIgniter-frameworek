# mini-project-codeIgniter

Since you are working on CodeIgniter, I will guide you step by step to use Vagrant to avoid the problems you face with XAMPP. Let's get started:

# Step 1: Install Vagrant and VirtualBox
Download and install cmder Download Full (https://cmder.app/).
Download and install Vagrant 2.4.1 AMD64 (https://developer.hashicorp.com/vagrant/install).
Download and install VirtualBox 6.1.0 (https://www.virtualbox.org/wiki/Download_Old_Builds_6_1).

# Step 2: Create a Vagrant Project
Open your CodeIgniter project folder (exemple : located in XAMPP, e.g. C:\xampp\htdocs\CodeIgniter).
Inside the folder, create a new file called Vagrantfile. This file will define how the virtual environment will be set up.

cd C:\xampp\htdocs\CodeIgniter

# Create a Vagrantfile: In the project folder, type the following command to create a Vagrantfile:

vagrant init

# Step 3: Set up Vagrantfile to run CodeIgniter
In this Vagrantfile, add the following settings:

--------------

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




--------



Start the virtual machine using the command:

vagrant up or vagrant up --provider=virtualbox



After the download is complete, you can enter the virtual environment using:

vagrant ssh




## Run the project now after this installation.

#Open your CodeIgniter project folder 

cd C:\workspaces\workspace\CodeIgniter


#Start the virtual machine using the command:

vagrant up or vagrant up --provider=virtualbox


#After the download is complete, you can enter the virtual environment using:

vagrant ssh

##Test access to your application:
#After running Vagrant, open your browser and go to:

http://192.168.33.10


## Result :

![image](https://github.com/user-attachments/assets/a94d635f-09a0-4424-926e-8b4a6523c954)
