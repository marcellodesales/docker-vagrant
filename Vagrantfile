VAGRANTFILE_API_VERSION = "2"

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|
    config.vm.box = "centos/7"
    config.vm.hostname = "vagrantbox"


    config.vm.network :private_network, ip: "10.0.0.10"


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

    config.vm.provision :shell, inline: "echo Your IP address: http://10.0.0.10"

end
