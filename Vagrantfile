$script = <<-SCRIPT
sudo su -
useradd foundry
echo "batata" | passwd foundry --stdin
echo "foundry ALL=(ALL) NOPASSWD: ALL" >> /etc/sudoers
SCRIPT

Vagrant.configure("2") do |config|
  config.vm.provision "shell", inline: $script
end



Vagrant.configure("2") do |config|

  config.vm.box = "generic/centos9s"
  config.vm.network "public_network"

  config.vm.provider "virtualbox" do |v|
  v.memory = 4096
  v.cpus = 2
  v.name = "Centos 9"

  end
  
end
