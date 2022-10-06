Vagrant.configure("2") do |config|
	config.vm.box = "debian/bullseye64"
	config.vm.synced_folder ".", "/vagrant", disabled: true
	
	config.vm.define "cliente1" do |cliente1|
		cliente1.vm.hostname = "cliente1"
		cliente1.vm.network "private_network",
		:libvirt__network_name => "Redpriv",
		:libvirt__dhcp_enabled => false,
		:libvirt__forward_mode => "veryisolated"
	end
	
	config.vm.define "router" do |router|
		router.vm.network "public_network",
			:dev => "br0",
			:mode => "bridge",
			:type => "bridge",
			use_dhcp_assigned_default_route: true
		router.vm.hostname = "router"
		router.vm.network "private_network",
			:libvirt__network_name => "Redpriv",
			:libvirt__dhcp_enabled => false,
			:libvirt__forward_mode => "veryisolated"
	end
	
	config.vm.provision "ansible" do |ansible|
		ansible.playbook = "site.yaml"
		ansible.groups = {
			"commoms" => ["router","cliente1"],
			"clientes" => ["cliente1"]
		}
	end
end
