
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
    apt-get install -y zip unzip sed
  SHELL

  config.vm.provision "shell", privileged: false, inline: "curl -s http://get.sdkman.io | bash"
  config.vm.provision "shell", privileged: false, inline: "source '/home/vagrant/.sdkman/bin/sdkman-init.sh' && yes | sdk install java 8.0.272-zulu"
  config.vm.provision "shell", privileged: false, inline: "source '/home/vagrant/.sdkman/bin/sdkman-init.sh' && yes | sdk install maven"
  config.vm.provision "shell", privileged: false, inline: "source '/home/vagrant/.sdkman/bin/sdkman-init.sh' && yes | sdk install gradle"

  config.vm.provision "shell", privileged: false, inline: <<-SHELL
    mkdir -p /home/vagrant/.vim/pack/local/start
    cd /home/vagrant/.vim/pack/local/start
    git clone https://github.com/editorconfig/editorconfig-vim.git
  SHELL

end

