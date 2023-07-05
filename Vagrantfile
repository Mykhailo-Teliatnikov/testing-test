Vagrant.configure("2") do |config|
	config.vm.define 'Master' do |node|
		node.vm.box =  "bento/ubuntu-20.04"  #"centos/7"
		node.vm.hostname = "master"
		node.vm.network "public_network"
		node.vm.synced_folder ".", "/vagrant"
		node.vm.provision "shell", path: "provision/1.sh"
		node.vm.provider "virtualbox" do |vb|
			vb.name = "Master"
			vb.memory = 4456
			vb.cpus = 4
		end

	end
end

