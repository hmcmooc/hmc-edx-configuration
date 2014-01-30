MEMORY = 2048
CPU_COUNT = 2

Vagrant.configure("2") do |config|

  # Creates an edX fullstack VM from an official release
  config.vm.box     = "empanada"
  config.vm.box_url = "http://files.edx.org/vagrant-images/20131218-empanada-fullstack.box"

  config.vm.network :private_network, ip: "192.168.33.10"
  config.vm.network "forwarded_port", guest: 80, host: 8083
  config.vm.network "forwarded_port", guest: 18010, host: 8084
  config.hostsupdater.aliases = ["preview.localhost"]

  config.vm.provider :virtualbox do |vb|
    vb.customize ["modifyvm", :id, "--memory", MEMORY.to_s]
    vb.customize ["modifyvm", :id, "--cpus", CPU_COUNT.to_s]

    # Allow DNS to work for Ubuntu 12.10 host
    # http://askubuntu.com/questions/238040/how-do-i-fix-name-service-for-vagrant-client
    vb.customize ["modifyvm", :id, "--natdnshostresolver1", "on"]
  end

end
