$script_mysql = <<-SCRIPT 
        apt-get update && \
        apt-get install -y mysql-server-5.7 && \
        mysql -e "create user 'administrador'@'%' identified by 'mestre';" && \
        cat /configs/mysqld.cnf > /etc/mysql/mysql.conf.d/mysqld.cnf && \
        service mysql restart
SCRIPT

Vagrant.configure("2") do |config|
    config.vm.box = "ubuntu/bionic64"
    config.vm.network "forwarded_port", guest: 80, host:8080
    config.vm.network "public_network"
    config.vm.provision "shell", inline: $script_mysql
    config.vm.synced_folder "./configs", "/configs"
    config.vm.synced_folder ".", "/vagrant", disabled: true
end
