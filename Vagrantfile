# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|
  config.vm.box = "bento/ubuntu-16.04"
  config.disksize.size = '300GB'

  config.vm.provider "virtualbox" do |vb|
    vb.gui = false
    vb.name = "AOSPbuilder"
    vb.cpus = 4
    vb.memory = 8192
  end

  config.vm.provision "shell", inline: <<-SHELL
    cd /vagrant/provision
    ./update-packages
    ./install-packages
    ./android-ndk
    ./guest-additions
    ./auto-gui
    ./auto-login
  SHELL

  config.vm.provision "sony-aosp", type: "shell", inline: <<-SHELL
    cd /vagrant/provision
    ./sony-aosp
  SHELL

  config.vm.provision "sony-build", type: "shell", privileged: false, inline: <<-SHELL
    cd /vagrant/provision
    ./sony-build
  SHELL
end
