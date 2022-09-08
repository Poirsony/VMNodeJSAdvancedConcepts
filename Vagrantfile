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
    apt-get update
    apt-get upgrade -y
    apt-get install curl -y
    curl -fsSL https://deb.nodesource.com/setup_12.x | -E bash -
    apt install nodejs redis git -y
    cd /var
    mkdir www
    cd www
    git clone https://github.com/StephenGrider/AdvancedNodeStarter.git
    cd ..
    chown vagrant:vagrant www
    chown vagrant:vagrant www -R
  SHELL
end
