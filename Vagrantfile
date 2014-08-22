# vim: set autoindent ft=ruby : 
VAGRANTFILE_API_VERSION = "2"

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|
  #config.vm.box = "phusion/ubuntu-14.04-amd64"
  #config.vm.network "private_network", ip: "192.168.33.10"
  config.vm.provider "docker" do |d|
    d.build_dir = "docker"
    d.name = "repos"
    d.has_ssh = true
    d.ports = ["8081:8081"]
  end
  config.vm.provision "puppet" do |puppet|
    puppet.manifests_path = "puppet/manifests"
    puppet.manifest_file  = "site.pp"
    puppet.module_path    = "puppet/modules"
    puppet.options        = "--verbose --debug"
  end
  command = "if [ ! -d ~git/.ssh ] ; then mkdir ~git/.ssh ;install -g git -o git #{File.join('/vagrant/keys', 'authorized_keys')} ~git/.ssh ; git init --bare ~git/demo.git ; chown -R git:git ~git/.ssh ~git/demo.git; fi"
  config.vm.provision :shell, :inline => command
end
