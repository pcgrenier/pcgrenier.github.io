# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|
  config.vm.box = "precise64"
  config.vm.box_url = "http://files.vagrantup.com/precise64.box"
  config.vm.network :forwarded_port, guest: 4000, host: 4000

  config.vm.provider :virtualbox do |vb|
    vb.memory = 2048
    vb.cpus = 2
  end
    
  config.vm.provision "shell", 
      inline: "sudo apt-get -y install build-essential git npm; sudo apt-get update; sudo apt-get -y install ruby1.9.3; sudo gem install jekyll rdiscount bundler --no-ri --no-rdoc;cd /vagrant && bundle install;"
end
