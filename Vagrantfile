# -*- mode: ruby -*-
# vi: set ft=ruby :
$script = <<-SCRIPT
apt-get update
apt-get install -y ansible sshpass
echo "192.168.56.11 controller" >> /etc/hosts
echo "192.168.56.12 node1" >> /etc/hosts
echo "192.168.56.13 node2" >> /etc/hosts
SCRIPT
Vagrant.configure("2") do |config|
  config.vm.define "controller" do |controller|
  controller.vm.box = "ubuntu/focal64"
  controller.vm.network "private_network", ip: "192.168.56.11"
  controller.vm.hostname = "controller"
  controller.vm.provider "virtualbox" do |vb|
    vb.memory = "2048"
  end
 controller.vm.provision "shell", inline: $script
end
config.vm.define "node1" do |node1|
  node1.vm.box = "ubuntu/focal64"
  node1.vm.network "private_network", ip: "192.168.56.12"
  node1.vm.hostname = "node1"
  node1.vm.provider "virtualbox" do |vb|
   vb.memory = "1024"
  end
  node1.vm.provision "shell", inline: $script
end
end
