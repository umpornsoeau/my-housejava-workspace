
Vagrant.configure("2") do |config|
  config.vm.box = "hashicorp/bionic64"
  config.vm.box_check_update = false
  config.vm.network "forwarded_port", guest: 80, host: 8080

  config.vm.provider "virtualbox" do |vb|
 	vb.gui = false
    	vb.memory = "4096"
	vb.cpus = 2
	vb.name = "housejava"
  end

  config.vm.provision "shell", inline: <<-SHELL
  	apt-get update
	apt install -y default-jre
	apt install -y default-jdk
	apt install -y maven
  SHELL

end

