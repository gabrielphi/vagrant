$script = <<-SCRIPT
sudo su -
sed -i 's/PasswordAuthentication no/PasswordAuthentication yes/g' /etc/ssh/sshd_config
systemctl reload sshd
useradd foundry
echo "batata" | passwd foundry --stdin
echo "foundry ALL=(ALL) NOPASSWD: ALL" >> /etc/sudoers
ip addr
SCRIPT


$script2 = <<-SCRIPT
sudo su -
sed -i 's/PasswordAuthentication no/PasswordAuthentication yes/g' /etc/ssh/sshd_config
systemctl reload sshd
useradd ansible
echo "batata" | passwd ansible --stdin
echo "ansible ALL=(ALL) NOPASSWD: ALL" >> /etc/sudoers
yum install -y ansible
ip addr
SCRIPT

Vagrant.configure("2") do |config|

  
  config.vm.box = "generic/centos9s"
  config.vm.network "public_network"
  


  config.vm.define "foundry" do |foundry|
    foundry.vm.provision "shell", inline: $script
    foundry.vm.provider "virtualbox" do |v|
      v.memory = 4096
      v.cpus = 2
      v.name = "Centos 9 - Foundry"

    end
  end

  config.vm.define "ansible" do |ansible|
    ansible.vm.provision "shell", inline: $script2
    ansible.vm.provider "virtualbox" do |v1|

      v1.memory = 4096
      v1.cpus = 2
      v1.name = "Centos 9 - Ansible"

    end
  end

end
