# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.require_version ">= 1.8.6"

VAGRANTFILE_API_VERSION = "2"

VM_MEMORY ||= 1024
VM_CPUS ||= 1

HAPROXY_PORT ||= 8080
NGINX_PORT ||= 9080

ansible_groups = {
  "haproxy" => ["default"],
  "nginx" => ["default"],
}

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|

  config.vm.box = "wittman/centos-7.2-ansible"
  config.vm.host_name = "clearscore"

  config.vm.network :forwarded_port, guest: HAPROXY_PORT, host: HAPROXY_PORT
  config.vm.network :forwarded_port, guest: NGINX_PORT, host: NGINX_PORT
  
  config.vm.provider "virtualbox" do |vb|
    vb.name = "clearscore"
    vb.memory = VM_MEMORY
    vb.cpus = VM_CPUS
  end

  config.vm.provision "ansible", type: "ansible_local", run: "always" do |ansible|
   ansible.playbook = "ansible/site.yml"
   ansible.groups = ansible_groups
  end

end
