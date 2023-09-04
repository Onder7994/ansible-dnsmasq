Vagrant.configure("2") do |config|
    config.vm.provider "virtualbox" do |vb|
      vb.gui = false
      vb.memory = 1024
      vb.cpus = 1
      vb.check_guest_additions = false
      config.vm.box_check_update = false
      config.vm.box = "bento/ubuntu-22.04"
    end
  
    config.vm.define "dns" do |node|
      node.vm.hostname = "dns"
      node.vm.network "public_network", ip: "192.168.10.100", bridge: "wlo1"
  
      node.vm.provision "ansible_local" do |ansible|
        ansible.playbook = "ansible/playbook/dnsmasq.yaml"
        ansible.limit = "all,localhost"
      end
    end
  end
  