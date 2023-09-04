https://github.com/hashicorp/vagrant/issues/7811

In the Vagrant file make sure to add the following type

Vagrant.configure("2") do |config|
  config.vm.synced_folder ".", "/vagrant", type: 'virtualbox'
  config.vbguest.auto_update = false if Vagrant.has_plugin?('vagrant-vbguest')
end

then


vagrant plugin install vagrant-vbguest

