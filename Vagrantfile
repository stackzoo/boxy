# -*- mode: ruby -*-
# vi: set ft=ruby :
VAGRANTFILE_API_VERSION = "2"


Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|
  config.vm.box = "hluaces/ubuntu-gnome"
  #Expanding VM disk via virtual box provider
  #config.disksize.size = '70GB' # uncomment this to expand vm disk, you will need to expand again from within the host (or from the ansible playbook)
  # Mapping folder between host and guests
  config.vm.synced_folder ".", "/home/vagrant/sync", disabled: true
  config.vm.synced_folder ".", "/vagrant", type: "virtualbox"
  # execute a bash script against the vm
  #config.vm.provision "shell", path: "bootstrap.sh", privileged: false

 # Change N in order to deploy more than 1 VM
 N = 1
 (1..N).each do |id|
 config.vm.define "ubuntu-dev-#{id}" do |machine|
   machine.vm.hostname = "ubuntu-dev-#{id}"
   machine.vm.network "private_network", ip: "192.168.56.#{10+id}"

    config.vm.provider "virtualbox" do |vb|
    # Display the VirtualBox GUI when booting the machine
      vb.gui = true
      # Customize the amount of memory and cpu on the VM:
      vb.memory = 4096
      vb.cpus = 4
    end

   # Only execute once the Ansible provisioner,
    # when all the machines are up and ready.
    if id == N
       machine.vm.provision :ansible do |ansible|
        ansible.become = true
        ansible.galaxy_role_file = "ansible/requirements.yml"
        ansible.galaxy_roles_path = "/etc/ansible/roles"
         # Install required roles
        ansible.galaxy_command = "sudo ansible-galaxy install --role-file=%{role_file} --roles-path=%{roles_path} --force"
        ansible.playbook = "ansible/config.yml"
      end
    end
  end
 end
end