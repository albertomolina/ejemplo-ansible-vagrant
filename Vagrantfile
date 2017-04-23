# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|
  config.ssh.insert_key = false
  config.vm.define :nodo1 do |nodo1|
    nodo1.vm.box = "ubuntu/trusty64"
    nodo1.vm.hostname = "nodo1"
    nodo1.vm.network :private_network, ip: "10.1.1.101"
    nodo1.vm.provider "virtualbox" do |vb|
      vb.memory = "512"
    end
  end
  config.vm.define :nodo2 do |nodo2|
    nodo2.vm.box = "ubuntu/trusty64"
    nodo2.vm.hostname = "nodo2"
    nodo2.vm.network :private_network, ip: "10.1.1.102"
    nodo2.vm.provider "virtualbox" do |vb|
      vb.memory = "512"
    end
  end
  config.vm.define :dns do |dns|
    dns.vm.box = "ubuntu/trusty64"
    dns.vm.hostname = "dns"
    dns.vm.network :private_network, ip: "10.1.1.103"
    dns.vm.provider "virtualbox" do |vb|
      vb.memory = "512"
    end
  end
  config.vm.provision "ansible" do |ansible|
    ansible.playbook = "site.yaml"
    ansible.inventory_path = "ansible_hosts"
  end
end
