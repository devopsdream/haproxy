# -*- mode: ruby -*-
# vi: set ft=ruby :

# All Vagrant configuration is done below. The "2" in Vagrant.configure
# configures the configuration version (we support older styles for
# backwards compatibility). Please don't change it unless you know what
# you're doing.
Vagrant.configure("2") do |config|
### loadbalancer01
   config.vm.define "loadbalancer01" do |loadbalancer01|
       loadbalancer01.vm.box = "rchouinard/oracle-65-x64"
       loadbalancer01.vm.hostname = "loadbalancer01"
       loadbalancer01.vm.network "private_network", ip:"192.168.50.4"
       loadbalancer01.vm.provider "virtualbox" do |v|
         v.memory = 512
         v.cpus = 2
       end
    end
###loadbalancer02
   config.vm.define "loadbalancer02" do |loadbalancer02|
       loadbalancer02.vm.box = "rchouinard/oracle-65-x64"
       loadbalancer02.vm.hostname = "loadbalancer02"
       loadbalancer02.vm.network "private_network", ip:"192.168.50.5"
       loadbalancer02.vm.provider "virtualbox" do |v|
         v.memory = 512
         v.cpus = 2
       end
    end
###web2
   config.vm.define "web2" do |web2|
       web2.vm.box = "rchouinard/oracle-65-x64"
       web2.vm.hostname = "web2"
       web2.vm.network "private_network", ip:"192.168.50.6"
       web2.vm.provider "virtualbox" do |v|
         v.memory = 512
         v.cpus = 2
       end
    end
end
