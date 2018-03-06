Vagrant.configure("2") do |config|
  config.vm.box = "centos_atomic_7"
  config.ssh.username = "root"
  config.ssh.password = "vagrant"


  config.vm.define "manager" do |manager|
    manager.vm.hostname = "manager"
    manager.vm.network "private_network", ip: "192.168.56.201"
    manager.vm.provider "virtualbox" do |vb|
      vb.customize ["modifyvm", :id, "--memory", "2048"]
      vb.cpus = 2
      vb.customize ["modifyvm", :id, "--cpuexecutioncap", "50"]
    end
    manager.vm.provision "ansible" do |ansible|
        ansible.playbook = "manager-playbook.yml"
    end
  end

  config.vm.define "master" do |master|
    master.vm.hostname = "master"
    master.vm.network "private_network", ip: "192.168.56.202"
    master.vm.provider "virtualbox" do |vb|
      vb.customize ["modifyvm", :id, "--memory", "3096"]
      vb.cpus = 2
      vb.customize ["modifyvm", :id, "--cpuexecutioncap", "50"]
    end
    master.vm.provision "ansible" do | ansible|
        ansible.playbook = "ocp-playbook.yml"
    end
  end

  config.vm.define "nodea" do |nodea|
    nodea.vm.hostname = "node-a"
    nodea.vm.network "private_network", ip: "192.168.56.203"
    nodea.vm.provider "virtualbox" do |vb|
      vb.customize ["modifyvm", :id, "--memory", "2048"]
    end
    nodea.vm.provision "ansible" do | ansible|
        ansible.playbook = "ocp-playbook.yml"
   end
  end

  config.vm.define "nodeb" do |nodeb|
    nodeb.vm.hostname = "node-b"
    nodeb.vm.network "private_network", ip: "192.168.56.204"
    nodeb.vm.provider "virtualbox" do |vb|
      vb.customize ["modifyvm", :id, "--memory", "2048"]
    end
    nodeb.vm.provision "ansible" do | ansible|
        ansible.playbook = "ocp-playbook.yml"
   end
  end


end

