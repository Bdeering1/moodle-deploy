# vi: set ft=ruby

Vagrant.configure("2") do |config|
  config.vm.box = "debian/bookworm64"

  config.ssh.forward_agent = true
  config.vm.network "private_network", ip: "192.168.33.10"

  # VirtualBox settings
  config.vm.provider "virtualbox" do |vb|
    vb.name = "Debian-Moodle-Practice"
    vb.memory = "1024" # Allocate 1GB RAM
    vb.cpus = 2
  end
end
