Vagrant.configure("2") do |config|
	config.hostmanager.enabled = true
	config.hostmanager.manage_host = true
	config.hostmanager.manage_guest = false

	config.vm.define "hamlet-test" do |node|
		node.vm.box = "ubuntu/xenial64"
		node.vm.hostname = "hamlet-test"
		node.vm.network "private_network", ip: "192.168.33.10"
		node.vm.synced_folder ".", "/vagrant", disabled: true

		node.vm.provision "file",
			source: "~/.ssh/id_rsa.pub",
			destination: "/tmp/id_rsa.pub"
		node.vm.provision "shell",
			inline: "cat /tmp/id_rsa.pub >> /home/vagrant/.ssh/authorized_keys"
	end
end