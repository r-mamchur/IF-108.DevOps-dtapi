# -*- mode: ruby -*-
# vi: set ft=ruby :
num_of_be = 2
num_of_fe = 2

Vagrant.configure("2") do |config| 

   config.vagrant.host = "windows"
   config.vm.box_check_update = true
   config.ssh.insert_key = false

   config.vm.define "my" do |my|
      my.vm.box = "centos/8"
      my.vm.hostname = 'my8'
      my.vm.network "private_network", ip: "192.168.56.31"
      my.vm.provider "virtualbox" do |vb|
         vb.memory = "768"
      end
      my.vm.provision "shell", path: "root_ssh.sh"	
      my.vm.provision "shell", path: "db.sh"	
   end

   (1..num_of_be).each do |i|
      config.vm.define "be#{i}" do |be|
         be.vm.box = "centos/7"
         be.vm.hostname = "be#{i}"
         be.vm.network "private_network", ip: "192.168.56.11#{i}"
         be.vm.provider "virtualbox" do |vb|
            vb.memory = "1024"
         end
         be.vm.provision "shell", path: "root_ssh.sh"	
         be.vm.provision "shell", path: "be.sh"	
      end
   end

   (1..num_of_fe).each do |i|
      config.vm.define "fe#{i}" do |fe|
         fe.vm.box = "centos/7"
         fe.vm.hostname = "fe#{i}"
         fe.vm.network "private_network", ip: "192.168.56.12#{i}"
         fe.vm.provider "virtualbox" do |vb|
            vb.memory = "1024"
         end
         fe.vm.provision "shell", path: "root_ssh.sh"	
         fe.vm.provision "shell", path: "fe.sh"	
      end
   end

   config.vm.define "hp" do |hp|
      hp.vm.box = "centos/7"
      hp.vm.hostname = 'hp'
      hp.vm.network "private_network", ip: "192.168.56.32"
      hp.vm.provider "virtualbox" do |vb|
         vb.memory = "1024"
      end
      hp.vm.provision "shell", path: "root_ssh.sh"	
      hp.vm.provision "shell", path: "hp.sh"	
   end

end

