VAGRANTFILE_API_VERSION = "2"

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|
    config.vm.box = "centos/7"

    config.vm.provider "virtualbox" do |vb|
        vb.gui = false
        vb.customize ['modifyvm', :id, '--memory', '1024']
        vb.customize ["modifyvm", :id, "--cpus", "1"]
        vb.customize ["modifyvm", :id, "--nictype1", "virtio"]
    end

    config.vm.provision "ansible" do |ansible|
        ansible.playbook = "ansible-master.yaml"
        ansible.sudo = true
    end

    #### Initial Vagrantbox for testing

    config.vm.define :vagrantbox do |vagrantbox|
      vagrantbox.vm.hostname = "vagrantbox"
      vagrantbox.vm.network :private_network, ip: "10.0.0.10"
      vagrantbox.vm.provision :shell, inline: "echo Your IP address: http://10.0.0.10"
    end

    #### Hosts for the load balancer

    ["one", "two", "three", "four"].each_with_index do |name, i|
      
      ipAddr = "192.168.0.10#{i+1}"

      config.vm.define name do |vmInstance|
        vmInstance.vm.hostname = "#{name}.cluster"
        vmInstance.vm.network :private_network, ip: ipAddr
        vmInstance.vm.provision :shell, inline: "echo Your IP address: http://#{ipAddr}"
        vmInstance.vm.provider :virtualbox do |vb|
          vb.name = name
          vb.customize ["modifyvm", :id, "--memory", 1024]
          vb.customize ["modifyvm", :id, "--cpus", "1"]
        end
      end
    
    end

end
