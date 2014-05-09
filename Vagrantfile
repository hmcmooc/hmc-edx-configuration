VAGRANTFILE_API_VERSION = "2"

MEMORY = 2048
CPU_COUNT = 2

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|

  # Creates an edX fullstack VM from an official release
  config.vm.box     = "gugelhupf"
  config.vm.box_url = "http://files.edx.org/vagrant-images/20140210-gugelhupf-fullstack.box"

  config.vm.network :private_network, ip: "192.168.33.10"
  config.hostsupdater.aliases = ["preview.localhost"]
  config.vm.network "forwarded_port", guest: 80, host: 8083
  config.vm.network "forwarded_port", guest: 18010, host: 8084

  config.vm.provider :virtualbox do |vb|
    vb.customize ["modifyvm", :id, "--memory", MEMORY.to_s]
    vb.customize ["modifyvm", :id, "--cpus", CPU_COUNT.to_s]

    # Allow DNS to work for Ubuntu 12.10 host
    # http://askubuntu.com/questions/238040/how-do-i-fix-name-service-for-vagrant-client
    vb.customize ["modifyvm", :id, "--natdnshostresolver1", "on"]
  end

end
