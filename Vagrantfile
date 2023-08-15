Vagrant.configure("2") do |config|
  config.vm.box = "ubuntu/bionic64"

  config.vm.network "private_network", type: "dhcp"

  config.vm.provider "virtualbox" do |vb|
    vb.memory = "1024"
  end

  config.vm.provision "shell", inline: <<-SHELL
    sudo apt-get update
    sudo apt-get install -y postgresql-8.4
    sudo sed -i "s/#listen_addresses = 'localhost'/listen_addresses = '*'/" /etc/postgresql/8.4/main/postgresql.conf
    echo "host all all 0.0.0.0/0 trust" | sudo tee -a /etc/postgresql/8.4/main/pg_hba.conf
    sudo service postgresql restart
  SHELL
end

