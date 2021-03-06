# -*- mode: ruby -*-
# vi: set ft=ruby :

# All Vagrant configuration is done below. The "2" in Vagrant.configure
# configures the configuration version (we support older styles for
# backwards compatibility). Please don't change it unless you know what
# you're doing.
Vagrant.configure("2") do |config|
  config.hostmanager.enabled = true
  config.hostmanager.manage_host = false
  config.hostmanager.manage_guest = true
  config.hostmanager.ignore_private_ip = false
  config.hostmanager.include_offline = true

  # The most common configuration options are documented and commented below.
  # For a complete reference, please see the online documentation at
  # https://docs.vagrantup.com.

  # Every Vagrant development environment requires a box. You can search for
  # boxes at https://atlas.hashicorp.com/search.
  config.vm.box = "ubuntu/xenial64"

  # Disable automatic box update checking. If you disable this, then
  # boxes will only be checked for updates when the user runs
  # `vagrant box outdated`. This is not recommended.
  config.vm.box_check_update = false

  # If true, then any SSH connections made will enable agent forwarding.
  # Default value: false
  config.ssh.forward_agent = true

  # use insecure key
  # config.ssh.insert_key = true

  # Create a forwarded port mapping which allows access to a specific port
  # within the machine from a port on the host machine. In the example below,
  # accessing "localhost:8080" will access port 80 on the guest machine.
  # config.vm.network "forwarded_port", guest: 80, host: 8080

  # Create a private network, which allows host-only access to the machine
  # using a specific IP.
  # config.vm.network "private_network", ip: "192.168.33.10"

  # Create a public network, which generally matched to bridged network.
  # Bridged networks make the machine appear as another physical device on
  # your network.
  # config.vm.network "public_network"

  # Share an additional folder to the guest VM. The first argument is
  # the path on the host to the actual folder. The second argument is
  # the path on the guest to mount the folder. And the optional third
  # argument is a set of non-required options.
  # config.vm.synced_folder "../data", "/vagrant_data"

  # Provider-specific configuration so you can fine-tune various
  # backing providers for Vagrant. These expose provider-specific options.
  # Example for VirtualBox:
  #
  # config.vm.provider "virtualbox" do |vb|
  #   # Display the VirtualBox GUI when booting the machine
  #   vb.gui = true
  #
  #   # Customize the amount of memory on the VM:
  #   vb.memory = "1024"
  # end

  config.vm.define "ansible-vm", autostart: true do |machine|
    machine.vm.provider "virtualbox" do |vb|
      # vb.gui = true
      vb.memory = "2048"
      vb.cpus = "1"

      if Vagrant::Util::Platform.windows? then
        # Fix for slow external network connections for Windows 10
        vb.customize ['modifyvm', :id, '--natdnshostresolver1', 'on']
        vb.customize ['modifyvm', :id, '--natdnsproxy1', 'on']
      end

    end

    machine.vm.network "private_network", ip: "192.168.33.10"
    machine.vm.hostname = "ansible-vm"

    # machine.vm.provision "shell" do |sh|
    #   sh.path = "ansible/ansible_install.sh"
    #   sh.args = "ansible/playbook.yml"
    # end

    machine.vm.provision "ansible_local" do |ansible|
      ansible.install_mode = "pip"
      ansible.version = "2.3.1.0"
      ansible.provisioning_path = "/vagrant/ansible"
      ansible.galaxy_role_file = "requirements.yml"
      ansible.playbook = "playbook.yml"
    end
  end

  config.vm.define "vm1", autostart: false do |machine|
    machine.vm.hostname = "vm1"
    machine.hostmanager.aliases = %w(vm1.localdomain)

    machine.vm.provider "virtualbox" do |vb|
      # vb.gui = true
      vb.memory = "1024"
      vb.cpus = "1"

      if Vagrant::Util::Platform.windows? then
        # Fix for slow external network connections for Windows 10
        vb.customize ['modifyvm', :id, '--natdnshostresolver1', 'on']
        vb.customize ['modifyvm', :id, '--natdnsproxy1', 'on']
      end
    end
    machine.vm.network "private_network", ip: "192.168.33.21"
    # do not need guest additions as will not share files
    machine.vbguest.auto_update = false
  end

  config.vm.define "vm2", autostart: false do |machine|
    machine.vm.hostname = "vm2"
    machine.hostmanager.aliases = %w(vm2.localdomain)

    machine.vm.provider "virtualbox" do |vb|
      # vb.gui = true
      vb.memory = "1024"
      vb.cpus = "1"

      if Vagrant::Util::Platform.windows? then
        # Fix for slow external network connections for Windows 10
        vb.customize ['modifyvm', :id, '--natdnshostresolver1', 'on']
        vb.customize ['modifyvm', :id, '--natdnsproxy1', 'on']
      end
    end

    machine.vm.network "private_network", ip: "192.168.33.22"
    # do not need guest additions as will not share files
    machine.vbguest.auto_update = false
  end

  config.vm.define "vm3", autostart: false do |machine|
    machine.vm.hostname = "vm3"
    machine.hostmanager.aliases = %w(vm3.localdomain)

    machine.vm.provider "virtualbox" do |vb|
      # vb.gui = true
      vb.memory = "1024"
      vb.cpus = "1"

      if Vagrant::Util::Platform.windows? then
        # Fix for slow external network connections for Windows 10
        vb.customize ['modifyvm', :id, '--natdnshostresolver1', 'on']
        vb.customize ['modifyvm', :id, '--natdnsproxy1', 'on']
      end
    end

    machine.vm.network "private_network", ip: "192.168.33.23"
    # do not need guest additions as will not share files
    machine.vbguest.auto_update = false
  end

  config.vm.define "vm4", autostart: false do |machine|
    machine.vm.hostname = "vm4"
    machine.hostmanager.aliases = %w(vm4.localdomain)

    machine.vm.provider "virtualbox" do |vb|
      # vb.gui = true
      vb.memory = "1024"
      vb.cpus = "1"

      if Vagrant::Util::Platform.windows? then
        # Fix for slow external network connections for Windows 10
        vb.customize ['modifyvm', :id, '--natdnshostresolver1', 'on']
        vb.customize ['modifyvm', :id, '--natdnsproxy1', 'on']
      end
    end

    machine.vm.network "private_network", ip: "192.168.33.24"
    # do not need guest additions as will not share files
    machine.vbguest.auto_update = false
  end

  # View the documentation for the provider you are using for more
  # information on available options.

  # Define a Vagrant Push strategy for pushing to Atlas. Other push strategies
  # such as FTP and Heroku are also available. See the documentation at
  # https://docs.vagrantup.com/v2/push/atlas.html for more information.
  # config.push.define "atlas" do |push|
  #   push.app = "YOUR_ATLAS_USERNAME/YOUR_APPLICATION_NAME"
  # end

  # Enable provisioning with a shell script. Additional provisioners such as
  # Puppet, Chef, Ansible, Salt, and Docker are also available. Please see the
  # documentation for more information about their specific syntax and use.
  # config.vm.provision "shell", inline: <<-SHELL
  #   apt-get update
  #   apt-get install -y apache2
  # SHELL
end
