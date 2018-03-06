Vagrant.configure("2") do |config|
  config.vm.box = "centos_atomic_7"
  config.ssh.username = "root"
  config.ssh.password = "vagrant"


  config.vm.define "manager" do |manager|
    manager.vm.hostname = "manager"
    manager.vm.network "private_network", ip: "192.168.56.201"
    manager.vm.provider "virtualbox" do |vb|
      vb.customize ["modifyvm", :id, "--memory", "1024"]
    end
    manager.vm.provision "ansible" do |ansible|
        ansible.playbook = "manager-playbook.yml"
    end
  end

  config.vm.define "master" do |master|
    master.vm.hostname = "master"
    master.vm.network "private_network", ip: "192.168.56.202"
        master.vm.provider "virtualbox" do |vb|
      vb.customize ["modifyvm", :id, "--memory", "2048"]
    end
    master.vm.provision "ansible" do | ansible|
        ansible.playbook = "ocp-playbook.yml"
    end
  end

  config.vm.define "infra" do |infra|
    infra.vm.hostname = "infra"
    infra.vm.network "private_network", ip: "192.168.56.203"
    infra.vm.provider "virtualbox" do |vb|
      vb.customize ["modifyvm", :id, "--memory", "1024"]
    end
    infra.vm.provision "ansible" do | ansible|
        ansible.playbook = "ocp-playbook.yml"
    end
  end

  config.vm.define "router" do |router|
    router.vm.hostname = "router"
    router.vm.network "private_network", ip: "192.168.56.204"
    router.vm.provider "virtualbox" do |vb|
      vb.customize ["modifyvm", :id, "--memory", "1024"]
    end
    router.vm.provision "ansible" do | ansible|
        ansible.playbook = "ocp-playbook.yml"
    end
  end

  config.vm.define "node" do |node|
    node.vm.hostname = "node"
    node.vm.network "private_network", ip: "192.168.56.205"
    node.vm.provider "virtualbox" do |vb|
      vb.customize ["modifyvm", :id, "--memory", "1024"]
    end
    node.vm.provision "ansible" do | ansible|
        ansible.playbook = "ocp-playbook.yml"
   end
  end

end

