# -*- mode: ruby -*-
# vi: set ft=ruby :

VAGRANTFILE_API_VERSION = '2'.freeze

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|
  config.vm.define "k8s-node1" do |subconfig|
    subconfig.vm.box = "ubuntu/xenial64"
    subconfig.vm.hostname = "k8s-node1"
    subconfig.vm.network :private_network, ip: "10.0.0.10"
    subconfig.vm.provider :virtualbox do |vb|
      vb.customize [
        'modifyvm', :id,
        '--natdnshostresolver1', 'on',
        '--memory', '2048',
        '--cpus', '1'
      ]
      end
  end

  config.vm.define "k8s-node2" do |subconfig|
    subconfig.vm.box = "ubuntu/xenial64"
    subconfig.vm.hostname = "k8s-node2"
    subconfig.vm.network :private_network, ip: "10.0.0.11"
    subconfig.vm.provider :virtualbox do |vb|
      vb.customize [
        'modifyvm', :id,
        '--natdnshostresolver1', 'on',
        '--memory', '2048',
        '--cpus', '1'
      ]
      end
  end

  config.vm.define "k8s-node3" do |subconfig|
    subconfig.vm.box = "ubuntu/xenial64"
    subconfig.vm.hostname = "k8s-node3"
    subconfig.vm.network :private_network, ip: "10.0.0.12"
    subconfig.vm.provider :virtualbox do |vb|
      vb.customize [
        'modifyvm', :id,
        '--natdnshostresolver1', 'on',
        '--memory', '2048',
        '--cpus', '1'
      ]
      end
  end
  
  config.vm.provision 'shell', path: 'scripts/provision-docker.sh'
  config.vm.provision 'shell', path: 'scripts/setup-pki.sh'
  config.ssh.forward_agent = true
end
