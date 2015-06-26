# -*- mode: ruby -*-
# vi: set ft=ruby :

# Vagrantfile API/syntax version. Don't touch unless you know what you're doing!
VAGRANTFILE_API_VERSION = "2"

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|
  # Vagrant
  config.vm.box = "CentOS7"
  config.vm.network "public_network", ip: "10.10.0.254", bridge: 'en1: Wi-Fi (AirPort)'
  config.vm.synced_folder "./zimbra", "/vagrant"
  config.vm.hostname  = "zimbra.ansible.local"

  # VirtualBox:
   config.vm.provider "virtualbox" do |vb|
    vb.customize ["modifyvm", :id, "--memory", "2048"]
    vb.name = "zimbra_ansible"
   end
 
  # Provisioner
   config.vm.provision "ansible" do |ansible|
     ansible.playbook = "provision/playbook.yml"
     ansible.extra_vars = { ansible_ssh_user: 'vagrant' }
     ansible.sudo = true
   end

end
