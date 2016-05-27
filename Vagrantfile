Vagrant.configure("2") do |config|
	config.vm.define "master" do |master|
	master.vm.box = "nrel/CentOS-6.6-x86_64"
	master.vm.hostname = 'master'
	master.vm.box_url = "nrel/CentOS-6.6-x86_64"
	master.vm.network :private_network, ip: "192.168.56.101"
	#master.vm.network :forwarded_port, guest: 22, host: 2222, id: "ssh"
	master.vm.provider :virtualbox do |v|
		v.customize ["modifyvm", :id, "--natdnshostresolver1", "on"]
		v.customize ["modifyvm", :id, "--memory", 512]
		v.customize ["modifyvm", :id, "--name", "master"]
	end
	config.vm.synced_folder "../../sync", "/home/vagrant/sync"
	config.vm.provision :shell, path: "bootstrap.sh"
	#config.vm.provision "shell", inline: <<-SHELL
	#	sudo yum update -y
	#	sudo yum install -y puppetmaster
	SHELL
  end

  config.vm.define "client1" do |client1|
    client1.vm.box = "nrel/CentOS-6.6-x86_64"
    client1.vm.hostname = 'client1'
    client1.vm.box_url = "nrel/CentOS-6.6-x86_64"
    client1.vm.network :private_network, ip: "192.168.56.102"
    client1.vm.network :forwarded_port, guest: 22, host: 2223, id: "ssh"
    client1.vm.provider :virtualbox do |v|
      v.customize ["modifyvm", :id, "--natdnshostresolver1", "on"]
      v.customize ["modifyvm", :id, "--memory", 512]
      v.customize ["modifyvm", :id, "--name", "client1"]
    end
	config.vm.provision :shell, path: "bootstrap.sh"
  end
  
  config.vm.define "client2" do |client2|
    client2.vm.box = "nrel/CentOS-6.6-x86_64"
    client2.vm.hostname = 'client2'
    client2.vm.box_url = "nrel/CentOS-6.6-x86_64"
    client2.vm.network :private_network, ip: "192.168.56.103"
   client2.vm.network :forwarded_port, guest: 22, host: 2224, id: "ssh"

    client2.vm.provider :virtualbox do |v|
      v.customize ["modifyvm", :id, "--natdnshostresolver1", "on"]
      v.customize ["modifyvm", :id, "--memory", 512]
      v.customize ["modifyvm", :id, "--name", "client2"]
    end
	config.vm.provision :shell, path: "bootstrap.sh"
  end

end
