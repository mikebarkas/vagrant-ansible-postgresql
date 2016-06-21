# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.require_version ">= 1.7.0"

Vagrant.configure(2) do |config|

  #
  # Vagrant box.
  #
  config.vm.box = "ubuntu/trusty64"
  config.ssh.insert_key = false

  #
  # Network configuration.
  #
  config.vm.hostname = "postgres"
  config.vm.network :private_network, ip: "10.10.10.100"

  #
  # VM config.
  #
  config.vm.provider :virtualbox do |vb|
    vb.name = "postgres"
    vb.customize ["modifyvm", :id, "--memory", "1024"]
  end

  #
  # Provision with Ansible.
  #
  config.vm.provision "ansible" do |ansible|
    ansible.verbose = "v"
    ansible.playbook = "provision/postgres_playbook.yml"
  end

end
