# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|
  config.vm.box = "fedora/38-cloud-base"
  
  config.vm.provider :libvirt do |provider|
    provider.memory = 4096
    provider.cpus = 4
  end

  config.vm.define "workstation" do |workstation|
    workstation.vm.hostname = "ws01"
    workstation.vm.network "private_network", ip: "192.168.10.10"
    workstation.vm.provision "ansible" do |ansible|
      ansible.playbook = "setup-workstation.yml"
      ansible.extra_vars = {
        user_git_name: "User John Doe",
        user_git_email: "user_johndoe@johndoe.com",
        work_git_name: "Work Jane Doe",
        work_git_email: "work_janedoe@janedoe.com"
    }
    end
  end
end
