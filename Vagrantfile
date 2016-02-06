# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure('2') do |config|

  config.vm.define "webserver" do |d|
    d.vm.box = 'centos-6.7'  
    d.vm.hostname = "my-webserver"
    d.ssh.username = 'root'
    d.ssh.password = 'vicky27'
    d.vm.synced_folder '.', '/vagrant', type: "rsync", rsync__exclude: ".git/", owner: "root", group: "root"
      config.vm.provider :virtualbox do |vb|
        vb.customize ["modifyvm", :id, "--memory", 256]
        vb.name = "CentOS_6.7"
      end
  end

   config.vm.provision :shell, :privileged => false, :inline => "pwd && whoami && echo $PATH && ls -l /usr/bin/ansible*"
   config.vm.provision :ansible_local do |ansible|
     ansible.sudo = true
     ansible.verbose = true
     ansible.playbook = "common.yml"
   end

end

