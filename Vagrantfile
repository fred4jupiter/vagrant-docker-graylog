# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure(2) do |config|  
  config.vm.box = "ubuntu/xenial64"
 
 config.vm.network "forwarded_port", guest: 9000, host: 9000
 config.vm.network "forwarded_port", guest: 12201, host: 12201

 config.vm.provider "virtualbox" do |vb|
    vb.customize ["modifyvm", :id, "--memory", "4096"]
	vb.customize ["modifyvm", :id, "--cpus", "4"]
  end  
 
  # install the 'vagrant plugin install vagrant-cachier' vagrant plugin to cache downloaded artifacts
  if Vagrant.has_plugin?("vagrant-cachier")
	# Configure cached packages to be shared between instances of the same base box.
	# More info on http://fgrehm.viewdocs.io/vagrant-cachier/usage
	config.cache.scope = :box

	# OPTIONAL: If you are using VirtualBox, you might want to use that to enable
	# NFS for shared folders. This is also very useful for vagrant-libvirt if you
	# want bi-directional sync
	# config.cache.synced_folder_opts = {
	#  type: :nfs,
	  # The nolock option can be useful for an NFSv3 client that wants to avoid the
	  # NLM sideband protocol. Without this option, apt-get might hang if it tries
	  # to lock files needed for /var/cache/* operations. All of this can be avoided
	  # by using NFSv4 everywhere. Please note that the tcp option is not the default.
	#  mount_options: ['rw', 'vers=3', 'tcp', 'nolock']
	# }
  end

  # to prevent tty errors
  config.ssh.shell = "bash -c 'BASH_ENV=/etc/profile exec bash'"
  config.vm.provision "shell", path: "install_docker.sh" 
  config.vm.provision "shell", path: "install_docker-compose.sh"
  config.vm.provision "shell", inline: "cd /vagrant && docker-compose up -d"
end
