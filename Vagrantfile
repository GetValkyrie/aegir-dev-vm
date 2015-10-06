# -*- mode: ruby -*-
# vi: set ft=ruby :
Vagrant.configure(2) do |config|
  config.vm.box = "debian/jessie64"

  config.vm.provider "virtualbox" do |v|
    v.memory = 1024
    v.cpus = 2
  end

  config.vm.hostname = 'aegir.local'
  config.vm.network 'private_network', ip: '10.55.55.55'

  config.vm.provision "shell",
    path: "https://raw.githubusercontent.com/GetValkyrie/ansible-bootstrap/master/install-ansible.sh"
  config.vm.provision "shell",
    inline: "ansible-galaxy install -r /vagrant/ansible/requirements.yml -p /vagrant/ansible/roles/ --ignore-errors"
  config.vm.provision "shell",
    inline: "PYTHONUNBUFFERED=1 ANSIBLE_FORCE_COLOR=true ansible-playbook /vagrant/ansible/site.yml -i /vagrant/ansible/inventory",
    keep_color: true

end
