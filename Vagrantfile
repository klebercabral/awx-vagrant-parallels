Vagrant.configure("2") do |config|
#  config.vm.box = "bento/centos-7.7"
  config.vm.box = "bento/ubuntu-18.04"
  config.vm.network "private_network", type: "dhcp"
  config.vm.provider "parallels" do |prl|
    prl.cpus = "1"
    prl.memory = "4096"
  end
#  config.vm.provision "shell", inline: "yum install epel-release -y;yum install ansible -y"
  config.vm.provision "shell", inline: "apt-add-repository --yes --update ppa:ansible/ansible;apt install ansible -y"
  config.vm.provision "ansible_local" do |ansible|
    ansible.become = true
    ansible.playbook = "awx.yml"
    ansible.galaxy_role_file = "req.yml"
    ansible.galaxy_roles_path = "/etc/ansible/roles"
    ansible.galaxy_command = "sudo ansible-galaxy install --role-file=%{role_file} --roles-path=%{roles_path} --force"
  end
end