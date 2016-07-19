# -*- mode: ruby -*-
# vi: set ft=ruby :
#
# Copyright 2016 Eric Romo
# Distributed under the Apache License

gui      = true

box      = 'centos/6'
url      = 'https://atlas.hashicorp.com/centos/boxes/6/versions/1606.01'
hostname = 'dov'
domain   = 'domino.dev'
ip       = '10.3.3.3'
ram      = '2048'

VAGRANTFILE_API_VERSION = "2"

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|
  config.vm.box = box
  config.vm.box_url = url
  config.vm.host_name = hostname + '.' + domain

  config.vm.network :private_network, ip: ip

  config.vm.synced_folder "./notesdata/", "/local/notesdata", type: "rsync", rsync__exclude: "./notesdata/domino/adm-bin/"
  config.vm.synced_folder "./", "/vagrant/"

  config.vm.provider :virtualbox do |vb|
    vb.customize ["modifyvm", :id, "--memory", ram, "--name", hostname, "--natdnshostresolver1", "on"]

  	# VirtualBox console
    vb.gui = gui
  end

  config.vm.provision "shell", path: "scripts/provision.sh"


end
