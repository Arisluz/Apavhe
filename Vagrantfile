Vagrant.configure("2") do |config|
  config.vm.box = "ubuntu/bionic64"  # Puedes usar "ubuntu/focal64" o cualquier otra box compatible.
  config.vm.network "forwarded_port", guest: 80, host: 8080  # Para acceder al servidor en el puerto 8080.

  # Asignar recursos
  config.vm.provider "virtualbox" do |vb|
    vb.memory = "512"
    vb.cpus = 1
  end

  # Configurar la carpeta compartida
  config.vm.synced_folder "./public_html", "/var/www/html", type: "virtualbox"

  # Provisionamiento para instalar Apache
  config.vm.provision "shell", inline: <<-SHELL
    sudo apt-get update
    sudo apt-get install -y apache2
    sudo systemctl enable apache2
    sudo systemctl start apache2
  SHELL
end

  