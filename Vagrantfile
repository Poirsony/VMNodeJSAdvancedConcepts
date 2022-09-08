# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|

  config.vm.box = "debian/bullseye64"

  config.vm.network "forwarded_port", guest: 3000, host: 8080

  config.vm.network "private_network", ip: "192.168.33.10"

  config.vm.provider "virtualbox" do |vb|
    vb.cpus = 4
    vb.memory = "4096"
  end

  config.vm.provision "file", source: "~/.ssh/id_rsa.pub", destination: "~/.ssh/me.pub"

  config.vm.provision "shell", run: "once", inline: <<-SHELL
    cat /home/vagrant/.ssh/me.pub >> /home/vagrant/.ssh/authorized_keys
    apt update
    apt upgrade -y
    apt install curl git redis -y
  SHELL

  config.vm.provision "shell", run: "once", privileged: false, inline: <<-SHELL
    curl -fsSL https://deb.nodesource.com/setup_12.x | sudo -E bash -
    sudo apt update
    sudo apt install nodejs -y
    sudo mkdir /var/www
    sudo chown vagrant:vagrant /var/www
    sudo chown vagrant:vagrant /var/www -R
    cd /var/www
    git clone https://github.com/StephenGrider/AdvancedNodeStarter.git
    cd AdvancedNodeStarter
    npm install
    cd client
    npm install
  SHELL
end
