# -*- mode: ruby -*-
# vi: set ft=ruby :

# NetBSD doesn't yet support Virtualbox shared folders, so
# we're using NFS to share.

Vagrant.configure(2) do |config|
  # This box can be downloaded from HashiCorp's "Atlas", and should
  # just Do The Right Thing at "vagrant up".
  config.vm.box = "riz/netbsd7-amd64"
  config.vm.network :private_network, ip: "192.168.33.10"
  config.vm.synced_folder ".", "/vagrant", :nfs => true

  #config.vm.provider "virtualbox" do |v|
  #  v.gui = true
  #end

  # Ansible provisioning happens at the end, reads from playbook.yml
  # in the current directory.
  config.vm.provision "ansible" do |ansible|
    ansible.playbook = "playbook.yml"
  end
end
