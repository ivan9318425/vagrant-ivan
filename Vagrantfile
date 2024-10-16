Vagrant.configure("2") do |config|
  config.vm.define "vm1" do |vm1|
    vm1.vm.box = "geerlingguy/centos7"
    vm1.vm.network "private_network", ip: "192.168.33.11"
    vm1.vm.network "forwarded_port", guest: 22, host: 2222
    vm1.vm.network "public_network"
    vm1.vm.provision "shell", inline: <<-SHELL
      sudo yum install httpd wget unzip -y
      sudo systemctl enable httpd
      sudo systemctl start httpd
      cd /tmp/
      wget https://www.tooplate.com/zip-templates/2135_mini_finance.zip
      unzip -o 2135_mini_finance.zip
      cp -r 2135_mini_finance/* /var/www/html/
      sudo systemctl restart httpd
    SHELL
  end
  config.vm.define "sql" do |sql|
    sql.vm.box = "geerlingguy/centos7"
    sql.vm.network "private_network", ip: "192.168.33.12"
    sql.vm.network "forwarded_port", guest: 22, host: 2223  # Cambiar el puerto
    #sql.vm.network "public_network"
  end
    
end

