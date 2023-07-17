# -*- mode: ruby -*-
# vi: set ft=ruby :

# Vagrantfile API/syntax version. Don't touch unless you know what you're doing!
VAGRANTFILE_API_VERSION = "2"

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|
  # https://vagrantcloud.com/ubuntu
  config.vm.box = "ubuntu/jammy64"
  config.vm.box_check_update = false
  
  #NETWORK!!!
  #config.vm.network "private_network", type: "dhcp"
  config.vm.network "public_network", bridge: "enp3s0"
  #config.vm.network "public_network",
  #use_dhcp_assigned_default_route: true
  
  #config.vm.provision "shell", inline: <<-SHELL
  #  echo "ubuntu:ubuntu" | sudo chpasswd
  #SHELL
  
  ###
  ###config.vm.provision :shell, :inline => "sudo sed -i 's/PasswordAuthentication no/PasswordAuthentication yes/g' /etc/ssh/sshd_config; sudo systemctl restart sshd;", run: "always"

  config.vm.provision "file", source: "~/.ssh/id_rsa.pub", destination: "/home/vagrant/.ssh/id_rsa.pub"
  config.vm.provision :shell, :inline => "cat /home/vagrant/.ssh/id_rsa.pub >> /home/vagrant/.ssh/authorized_keys", run: "always"

  # Forward ports
  #config.vm.network "forwarded_port", guest: 8080, host: 8080 # web server
  #config.vm.network "forwarded_port", guest: 5432, host: 5432 # Postgres

  #config.disksize.size = '20GB'

  config.vm.provider "virtualbox" do |v|
    v.memory = 1024
    v.cpus = 1
  end

  # If true, then any SSH connections made will enable agent forwarding.
  ###config.ssh.forward_agent = true

  # Share additional folders to the guest VM.
  ###config.vm.synced_folder "data", "/data"
  # Bash provision script
  ###config.vm.provision "shell", path: "provision.sh"

  #config.ssh.username = "user"
  #config.ssh.password = "password"
  
  ### Upload user's ssh key into box so it can be used for downloading stuff from stash
  #ssh_key_path = "~/.ssh/"
  #config.vm.provision "shell", inline: "sudo mkdir -p /home/datsyuk/.ssh"
  #config.vm.provision "file", source: "#{ ssh_key_path + 'id_rsa' }", destination: "/home/datsyuk/.ssh/id_rsa"
  #config.vm.provision "file", source: "#{ ssh_key_path + 'id_rsa.pub' }", destination: "/home/datsyuk/.ssh/id_rsa.pub"

end

