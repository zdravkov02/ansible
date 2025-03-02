# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure(2) do |config|
    
  config.ssh.insert_key = false

  config.vm.define "ans" do |ans|
    ans.vm.box = "merev/centos-stream-8"
    ans.vm.hostname = "ansible"
    ans.vm.network "private_network", ip: "192.168.99.99"
    ans.vm.synced_folder "shared/", "/shared"
    ans.vm.provision "shell", path: "initial-config/add_hosts.sh"
    ans.vm.provision "shell", path: "initial-config/redhat_ansible_setup.sh"

    ans.vm.provider "virtualbox" do |v|
      v.gui = false
      v.memory = 2048
      v.cpus = 2
    end
  end

  config.vm.define "web" do |web|
    web.vm.box = "merev/centos-stream-8"
    web.vm.hostname = "web"
    web.vm.network "private_network", ip: "192.168.99.100"
    web.vm.network "forwarded_port", guest: 80, host: 8080
    web.vm.synced_folder "shared/", "/shared"
    web.vm.provision "shell", path: "initial-config/add_hosts.sh"
    web.vm.provision "shell", path: "initial-config/ansible_clients_setup.sh"

    web.vm.provider "virtualbox" do |v|
      v.gui = false
      v.memory = 1024
      v.cpus = 1
    end
  end
  
  config.vm.define "db" do |db|
    db.vm.box = "merev/centos-stream-8"
    db.vm.hostname = "db"
    db.vm.network "private_network", ip: "192.168.99.101"
    db.vm.synced_folder "shared/", "/shared"
    db.vm.provision "shell", path: "initial-config/add_hosts.sh"
    db.vm.provision "shell", path: "initial-config/ansible_clients_setup.sh"

    db.vm.provider "virtualbox" do |v|
      v.gui = false
      v.memory = 1024
      v.cpus = 1
    end
  end

  config.vm.define "docker" do |docker|
    docker.vm.box = "merev/centos-stream-8"
    docker.vm.hostname = "docker"
    docker.vm.network "private_network", ip: "192.168.99.102"
    docker.vm.synced_folder "shared/", "/shared"
    docker.vm.provision "shell", path: "initial-config/add_hosts.sh"
    docker.vm.provision "shell", path: "initial-config/ansible_clients_setup.sh"
    docker.vm.provision "shell", path: "initial-config/docker_setup.sh"

    docker.vm.provider "virtualbox" do |v|
      v.gui = false
      v.memory = 1024
      v.cpus = 1
    end
  end
 
end
