# -*- mode: ruby -*-
# vi: set ft=ruby :

# All Vagrant configuration is done below. The "2" in Vagrant.configure
# configures the configuration version (we support older styles for
# backwards compatibility). Please don't change it unless you know what
# you're doing.
Vagrant.configure("2") do |config|
# Install ansible
config.vm.provision "shell",
inline: 'yum -y install ansible' 
### loadbalancer01
   config.vm.define "loadbalancer01" do |loadbalancer01|
       loadbalancer01.vm.box = "rchouinard/oracle-65-x64"
       loadbalancer01.vm.hostname = "loadbalancer01"
       loadbalancer01.vm.network "private_network", ip:"192.168.50.4"
       loadbalancer01.vm.provider "virtualbox" do |v|
         v.memory = 512
         v.cpus = 2
       end
       loadbalancer01.vm.provision "shell",
         inline: 'ansible-playbook -i "localhost," -c local /vagrant/ansible/install-haproxy.yml'
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
       loadbalancer02.vm.provision "shell",
         inline: 'ansible-playbook -i "localhost," -c local /vagrant/ansible/install-haproxy.yml'
    end
###web2
{
 'web2' => '192.168.50.6',
 'web' => '192.168.50.2',
}.each do |host_name, ip| 
   config.vm.define host_name do |host|
        host.vm.box = 'rchouinard/oracle-65-x64'
        host.vm.boot_timeout = 600
        host.vm.network 'private_network', ip: ip
        host.vm.hostname = "#{host_name}.devopsdream.io"
        host.vm.provision "shell",
         inline: 'ansible-playbook -i "localhost," -c local /vagrant/ansible/install-web-haproxy.yml'
   end 
 end 

##end of file
end
