Vagrant.configure("2") do |config|
    # Especificamos la máquina base
    config.vm.box = "ubuntu/bionic64"  

    # Asignamos una IP estática
    config.vm.network "private_network", ip: "192.168.56.10"

    # Compartimos la carpeta local con el servidor web de Apache
    config.vm.synced_folder "./html", "/var/www/html"

    # Asignamos recursos a la máquina virtual
    config.vm.provider "virtualbox" do |vb|
    vb.memory = "512"
    vb.cpus = 1
    end

    # Script de aprovisionamiento para instalar Apache
    config.vm.provision "shell", inline: <<-SHELL
    sudo apt update
    sudo apt install -y apache2
    echo "<h1>¡Hola Mundo desde Apache en Vagrant!</h1>" | sudo tee /var/www/html/index.html
    sudo systemctl restart apache2
    SHELL
end
