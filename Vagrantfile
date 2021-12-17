# -*- mode: ruby -*-
# vi: set ft=ruby :
Vagrant.configure("2") do |config|
  config.vm.box = "ubuntu/bionic64"

  # Webserver: Linux, Apache and PHP
  config.vm.define "web-server" do |web|
    web.vm.network "private_network", ip: "10.10.10.50"
    web.vm.synced_folder "www", "/www"
    web.vm.hostname = "web"

    web.vm.provider "virtualbox" do |vb|
      vb.name = "web"
      vb.cpus = 1
      vb.memory = "512"
      vb.customize [ "modifyvm", :id, "--uartmode1", "disconnected" ]
    end
    
    web.vm.provision "shell", path: "setup/scripts/copy_ansible_pub_key.sh"
  end

  # Database: MySQL 5.7
  config.vm.define "db" do |db|
    db.vm.network "private_network", ip: "10.10.10.51"
    db.vm.hostname = "db"

    db.vm.provider "virtualbox" do |vb|
      vb.name = "db"
      vb.cpus = 1
      vb.memory = "512"
      vb.customize [ "modifyvm", :id, "--uartmode1", "disconnected" ]
    end
    
    db.vm.provision "shell", path: "setup/scripts/copy_ansible_pub_key.sh"
  end

  # Ansible
  config.vm.define "ansible" do |ansible|
    ansible.vm.network "private_network", ip: "10.10.10.60"
    ansible.vm.synced_folder "setup/ansible/", "/ansible"
    ansible.vm.hostname = "ansible"

    ansible.vm.provider "virtualbox" do |vb|
      vb.name = "ansible"
      vb.cpus = 1
      vb.memory = "256"
      vb.customize [ "modifyvm", :id, "--uartmode1", "disconnected" ]
    end

    # Copy a private key to be used with Ansible
    ansible.vm.provision "shell", path: "setup/scripts/copy_ansible_priv_key.sh"

    # Ansible Install
    ansible.vm.provision "shell", path: "setup/scripts/setup_ansible.sh"

    # Run Ansible Playblook
    ansible.vm.provision "shell",
      inline: "ansible-playbook -i /ansible/hosts /ansible/playbook.yaml"
  end  
end
