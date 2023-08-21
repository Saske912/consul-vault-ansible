Vagrant.configure("2") do |config|
	config.vm.box = "ubuntu/bionic64"
	config.vm.network "private_network", type: "dhcp", virtualbox__intnet: true
	config.vm.provision "hostmanager"
  
	(1..3).each do |i|
	  config.vm.define "host#{i}" do |node|
		node.vm.hostname = "facecast#{i}"
		node.vm.provider "virtualbox" do |vb|
		  vb.name = "facecast#{i}"
		  vb.memory = 1024
		  vb.cpus = 1
		end
  
		node.vm.provision "ansible_local" do |ansible|
		  ansible.playbook = "consul_setup.yml"
		  ansible.verbose = "vv"
		end
	  end
	end
  
	# (1..3).each do |i|
	#   config.vm.define "host#{i}" do |node|
	# 	node.vm.provision "ansible_local" do |ansible|
	# 	  ansible.playbook = "ansible_playbooks/vault_setup.yml"
	# 	end
	#   end
	# end
  end
  