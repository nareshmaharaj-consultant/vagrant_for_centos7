#if Vagrant::VERSION < "2.0.0"
#  $stderr.puts "Must redirect to new repository for old Vagrant versions"
#  Vagrant::DEFAULT_SERVER_URL.replace('https://vagrantcloud.com')
#end

Vagrant.configure("2") do |config|
  config.vm.box = "generic/centos7"
  config.vm.box_check_update = false
  config.vm.synced_folder "shared/", "/shared", create: true, type: 'virtualbox'
  config.vm.synced_folder "data/", "/data", create: true, type: 'virtualbox'
  config.vm.provision "shell", path: "swap.off.sh"
  config.vm.provision "shell", path: "add-fw-rules.sh"
  config.vm.provision "shell", path: "jdk11.sh"
  config.vbguest.auto_update = false if Vagrant.has_plugin?('vagrant-vbguest')

  config.vm.define "box1" do |server1|
    server1.vm.provider "virtualbox" do |vb|
      vb.customize ["modifyvm", :id, "--cpus", "2"]
      vb.customize ['modifyvm', :id, '--macaddress1', '080027000051']
      vb.customize ['modifyvm', :id, '--natnet1', '10.0.51.0/24']
      vb.name = "box1"
      vb.memory = 4096
    end
    server1.vm.hostname = "box1.aerospike.training"
    server1.vm.network :private_network, ip: "192.168.56.151"
  end

  config.vm.define "box2" do |server2|
    server2.vm.provider "virtualbox" do |vb|
      vb.customize ["modifyvm", :id, "--cpus", "2"]
      vb.customize ['modifyvm', :id, '--macaddress1', '080027000052']
      vb.customize ['modifyvm', :id, '--natnet1', '10.0.52.0/24']
      vb.name = "box2"
      vb.memory = 4096
    end
    server2.vm.hostname = "box2.aerospike.training"
    server2.vm.network :private_network, ip: "192.168.56.152"
  end
  
  config.vm.define "box3" do |server3|
    server3.vm.provider "virtualbox" do |vb|
      vb.customize ["modifyvm", :id, "--cpus", "2"]
      vb.customize ['modifyvm', :id, '--macaddress1', '080027000053']
      vb.customize ['modifyvm', :id, '--natnet1', '10.0.53.0/24']
      vb.name = "box3"
      vb.memory = 4096
    end
    server3.vm.hostname = "box3.aerospike.training"
    server3.vm.network :private_network, ip: "192.168.56.153"
  end
end
