# vi: set ft=ruby :
Vagrant.configure("2") do |config|
  config.vm.box = "debian/jessie64"
  config.vm.provision "ansible" do |ansible|
     ansible.playbook = "site.yml"
	 ansible.groups = {
		"swarm"         => [
				"node-1", 
				"node-2", 
				"node-3", 
				"node-4", 
				"node-5"
		],
		"swarm-managers" => [
				"node-3", 
				"node-5"
		],
		"swarm-workers"  => [
				"node-2", 
				"node-4"
		],
		"swarm-heads"    => [
				"node-1"
		]
	}
  end

  (1..5).each do |i|
	config.vm.define "node-#{i}" do |node|
		node.vm.network "private_network", ip: "10.69.55.#{i+68}"
		node.vm.hostname = "node-#{i}"
	end
  end
end
