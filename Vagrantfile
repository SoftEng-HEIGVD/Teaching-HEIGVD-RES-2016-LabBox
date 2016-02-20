# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure(2) do |config|

  # We have prepared our own base box with Packer and host it on atlas.hashicorp.com
  # If you want the gory details, see https://github.com/wasadigi/atlas-packer-vagrant-tutorial
  config.vm.box = "oliechti/labbox2016b"

  # Create a forwarded port mapping which allows access to a specific port
  # within the machine from a port on the host machine. In the example below,
  # accessing "localhost:8080" will access port 80 on the guest machine.
  # config.vm.network "forwarded_port", guest: 80, host: 8080

  # Create a private network, which allows host-only access to the machine
  config.vm.network "private_network", ip: "192.168.42.42"

  config.vm.hostname = "RES"

  # Forward the X protocol. This is very useful if you use Wireshark on the box and want to 
  # display the UI on your host
  #config.ssh.forward_x11 = true

  config.vm.provider "virtualbox" do |vb|
  #   vb.gui = true
  #   vb.memory = "1024"
  end

end
