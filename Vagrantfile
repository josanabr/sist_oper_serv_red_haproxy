Vagrant.configure("2") do |config|
  config.vm.define "haproxy" do |m|
    m.vm.box = "ubuntu/xenial64"
    m.vm.network "forwarded_port", guest: 80, host: 8080
    m.vm.network "private_network", ip: "192.168.33.10"
    m.vm.hostname = "haproxy-server"
    m.vm.provider :virtualbox do |vb|
  	vb.customize [ 'modifyvm', :id, '--name', 'haproxy' ]
  	vb.customize [ 'modifyvm', :id, '--cpus', '1' ]
  	vb.customize [ 'modifyvm', :id, '--memory', '1024' ]
    end  
  end
  config.vm.define "web1" do |m|
    m.vm.box = "ubuntu/groovy64"
    m.vm.provision "shell", path: "install-apache2.sh"
    #m.vm.network "forwarded_port", guest: 80, host: 8080
    m.vm.synced_folder "./web1", "/var/www/html"
    m.vm.network "private_network", ip: "192.168.33.11"
    m.vm.hostname = "web1"
    m.vm.provider :virtualbox do |vb|
  	vb.customize [ 'modifyvm', :id, '--name', 'web1' ]
  	vb.customize [ 'modifyvm', :id, '--cpus', '2' ]
  	vb.customize [ 'modifyvm', :id, '--memory', '1024' ]
    end  
  end
  config.vm.define "web2" do |m|
    m.vm.box = "ubuntu/groovy64"
    m.vm.provision "shell", path: "install-apache2.sh"
    #m.vm.network "forwarded_port", guest: 80, host: 8080
    m.vm.synced_folder "./web2", "/var/www/html"
    m.vm.network "private_network", ip: "192.168.33.12"
    m.vm.hostname = "web2"
    m.vm.provider :virtualbox do |vb|
  	vb.customize [ 'modifyvm', :id, '--name', 'web2' ]
  	vb.customize [ 'modifyvm', :id, '--cpus', '2' ]
  	vb.customize [ 'modifyvm', :id, '--memory', '1024' ]
    end  
  end
end

