# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|
  config.vm.box = "ubuntu/focal64"

  # ip assignment
  config.vm.network "public_network", ip: '192.168.1.250'
  
  # port forwarding
  config.vm.network "forwarded_port", guest: 22, host: 2222
  config.vm.network "forwarded_port", guest: 80, host: 8080
  config.vm.network "forwarded_port", guest: 443, host: 8443
  config.vm.network "forwarded_port", guest: 53, host: 5353, protocol: "tcp"
  config.vm.network "forwarded_port", guest: 53, host: 5353, protocol: "udp"
  config.vm.network "forwarded_port", guest: 51820, host: 51820, protocol: 'udp'
  config.vm.network "forwarded_port", guest: 67, host: 6767, protocol: "udp"

  config.vm.provision "shell", inline: <<-SHELL
    sudo apt-get update
    sudo apt-get install -y apt-transport-https ca-certificates curl software-properties-common nmap
    curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -
    sudo add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable"
    sudo apt-get update
    sudo apt-get install -y docker-ce
    sudo curl -L "https://github.com/docker/compose/releases/download/1.29.2/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose
    sudo chmod +x /usr/local/bin/docker-compose
    mkdir -p /home/vagrant/wireguard-pihole
    curl -L "https://github.com/NupaZzz/WireGuard-with-Pi-hole/raw/main/docker-compose.yaml" -o /home/vagrant/wireguard-pihole/docker-compose.yaml
    cd /home/vagrant/wireguard-pihole && docker-compose up
  SHELL
end
