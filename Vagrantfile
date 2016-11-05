Vagrant.configure("2") do |config|
    config.vm.box = "debian/jessie64"

    # Configure the network interfaces
    config.vm.network "private_network", ip: "10.20.30.2"
    config.vm.network :forwarded_port,  guest: 80,    host: 8080
    config.vm.network :forwarded_port,  guest: 3306,  host: 3306

    # Configure shared folders
    config.vm.synced_folder ".",  "/vagrant", :nfs => true

    # Configure VirtualBox environment
    config.vm.provider :virtualbox do |v|
        # v.name = (0...8).map { (65 + rand(26)).chr }.join
        v.customize [ "modifyvm", :id, "--memory", 512 ]
    end

    # Provision the box
    config.vm.provision :ansible do |ansible|
        ansible.playbook = "ansible/site.yml"
    end
end
