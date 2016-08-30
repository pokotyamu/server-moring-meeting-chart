# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure(2) do |config|

  config.vm.define :test1 do |test1|
    test1.vm.box = "morning-app-vm"
    test1.vm.box_url = "http://opscode-vm-bento.s3.amazonaws.com/vagrant/virtualbox/opscode_centos-6.5_chef-provisionerless.box"

    test1.vm.network "forwarded_port", guest: 80, host: 1234
    test1.vm.network :private_network, ip: "192.168.33.10"

    test1.ssh.forward_agent = true

    # vagrant-omnibus の有効化
    test1.omnibus.chef_version = :latest

    test1.vm.provision :chef_solo do |chef|
      chef.cookbooks_path = ["./cookbooks", "./site-cookbooks"]

      chef.add_recipe 'yum-epel'
      chef.add_recipe 'nginx'
    end
  end

  config.vm.define :test2 do |test2|
    test2.vm.box = "morning-app-vm"
    test2.vm.box_url = "http://opscode-vm-bento.s3.amazonaws.com/vagrant/virtualbox/opscode_centos-6.5_chef-provisionerless.box"

    test2.vm.network :private_network, ip: "192.168.33.11"

    test2.vm.provider "virtualbox" do |vb|
      vb.memory = "1024"
    end
  end
  
end
