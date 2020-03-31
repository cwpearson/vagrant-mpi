Vagrant.configure("2") do |config|
    config.vm.provision "shell", inline: "echo Hello"

    # add synced folder for host file
    config.vm.synced_folder "generated/hostfile", "/etc/hostfile"

    # install mpi
    config.vm.provision "shell", inline: "sudo apt-get update && sudo apt-get install -y openmpi-bin"

    config.vm.define "master" do |master|
        master.vm.box = "hashicorp/bionic64"
        master.vm.box_version = "1.0.282"

        master.vm.network "private_network", type: "dhcp"

        # and ssh keys
        master.vm.provision "file", source: "ssh/id_rsa", destination: "$HOME/.ssh/id_rsa"
        master.vm.provision "file", source: "ssh/id_rsa.pub", destination: "$HOME/.ssh/id_rsa.pub"
        master.vm.provision "shell", inline: "ln -s /etc/hostfile/config /home/vagrant/.ssh/config"

        # all workers have the same key
        master.vm.provision "shell", inline: "cat /home/vagrant/.ssh/id_rsa.pub >> /home/vagrant/.ssh/authorized_keys"

    end
  
    (1..1).each do |i|
        config.vm.define "worker#{i}" do |worker|
            
            worker.vm.box = "hashicorp/bionic64"
            worker.vm.box_version = "1.0.282"

            worker.vm.network "private_network", type: "dhcp"

            worker.vm.provider "virtualbox" do |v|
                v.memory = 1024
                v.cpus = 2
                v.linked_clone = true
            end

            # and ssh keys
            worker.vm.provision "file", source: "ssh/id_rsa", destination: "$HOME/.ssh/id_rsa"
            worker.vm.provision "file", source: "ssh/id_rsa.pub", destination: "$HOME/.ssh/id_rsa.pub"
            worker.vm.provision "shell", inline: "ln -s /etc/hostfile/config /home/vagrant/.ssh/config"

            # all workers have the same key
            worker.vm.provision "shell", inline: "cat /home/vagrant/.ssh/id_rsa.pub >> /home/vagrant/.ssh/authorized_keys"

        end
    end

  end
  