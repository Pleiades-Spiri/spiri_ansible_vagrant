Vagrant.configure("2") do |config|
  config.vm.box = "pstizzy/ubuntu-xenial64-ros-kinetic-desktop-full"
  config.vm.box_version = "0.0.1"
end


Vagrant.configure("2") do |config|
    vm_name = 'default'
    config.vm.box = "pstizzy/ubuntu-xenial64-ros-kinetic-desktop-full"
    config.vm.box_version = "0.0.1"
    config.vm.synced_folder ".", "/vagrant", id: "vagrant-root", :mount_options => ["dmode=777","fmode=777"]

    config.vm.provider "virtualbox" do |v|
        v.customize ["modifyvm", :id, "--memory", "1536"]
        v.customize ["modifyvm", :id, "--cpus", "2"]
        v.customize ["modifyvm", :id, "--cpuexecutioncap", "75"]
        v.customize ["modifyvm", :id, "--vram", "12"]
        v.customize ["modifyvm", :id, "--ioapic", "on"]
        v.customize ["modifyvm", :id, "--audio", "none"]
        v.name = "spiri-vagrant-ros"
    end

    # Set up a private IP that can be added to the host machine's hosts file
    config.vm.network "private_network", ip: "192.168.99.99"

    # Ports to forward from the guest VM to the host
  	config.vm.network "forwarded_port", guest: 5432, host: 5432, auto_correct: false

    vagrant_arg = ARGV[0]

    if ENV['VAGRANT_HOSTNAME'].nil? and Dir.glob("#{File.dirname(__FILE__)}/.vagrant/machines/#{vm_name}/virtualbox/id").empty? and vagrant_arg == 'up'
        print "A hostname for virtual Spiri has not been provided. Please create one, or hit enter for the default.\n"
        print "Enter your hostname [vagrant.spiri.com]: "
        config.vm.hostname = STDIN.gets.chomp
        # If no input, use vagrant.spiri.com as the hostname
        if config.vm.hostname == ''
            config.vm.hostname = "vagrant.spiri.com"
        end
    else
        config.vm.hostname = ENV['VAGRANT_HOSTNAME']
    end

    config.vm.provision "ansible_local" do |ansible|
        ansible.playbook = "vagrant_playbook.yml"
    end
end

