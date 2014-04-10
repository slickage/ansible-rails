Vagrant.configure("2") do |config|
  config.vm.box       = "precise64"
  config.vm.box_url   = "http://files.vagrantup.com/precise64.box"
  config.vm.host_name = "slickage-prototype-host"

  private_ip = "192.168.13.37"
  config.vm.network(:private_network, :ip => private_ip)
  config.vm.provider "virtualbox" do |vb|
    vb.customize(["modifyvm", :id, "--natdnshostresolver1", "off"  ])
    vb.customize(["modifyvm", :id, "--natdnsproxy1",        "off"  ])
    vb.customize(["modifyvm", :id, "--memory",              "1024" ])
  end

  #config.vm.provision :ansible do |ansible|
  #  ansible.extra_vars = { ansible_ssh_user: 'vagrant' }
  #  ansible.playbook = "rails-app-local.yml"
  #end

  if defined?(VagrantPlugins::HostsUpdater)
    config.hostsupdater.aliases = ["local-seer.slickage.com"]
  end
end
