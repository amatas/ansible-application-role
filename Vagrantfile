# -*- mode: ruby -*-
# vi: set ft=ruby :

# Vagrantfile API/syntax version. Don't touch unless you know what you're doing!
VAGRANTFILE_API_VERSION = "2"

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|

  config.vm.define "appserver" do |appserver|

    appserver.vm.box = "centos65"
    appserver.vm.box_url = "https://github.com/2creatives/vagrant-centos/releases/download/v6.5.1/centos65-x86_64-20131205.box"

    appserver.vm.hostname = 'appserver'
    appserver.vm.network "private_network", ip: "192.168.50.11"
    appserver.vm.provider "virtualbox" do |v|
      v.gui = true
    end 
    appserver.vm.provision "ansible" do |ansible|

      ansible.host_key_checking = false
      ansible.sudo = true
      ansible.extra_vars = { 
        ansible_ssh_user: 'vagrant',
      } 
            
      ansible.playbook = "site.yml"
      ansible.groups = {
        "webservers" => ["appserver"],
        "all_groups:children" => ["webservers"]
      }
      ansible.limit = 'all'
#     ansible.raw_arguments  = "--ask-vault-pass"
#     Debug option
#     ansible.raw_arguments  = "--vault-password-file=secret_file_plain_pass"
      ansible.verbose = 'vvvv'
    end
  end
end
