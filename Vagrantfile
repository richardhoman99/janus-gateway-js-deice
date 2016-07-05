Vagrant.configure('2') do |config|
  config.ssh.forward_agent = true
  config.vm.box = 'cargomedia/debian-7-amd64-default'

  config.vm.hostname = 'janus-gateway-js.dev.cargomedia.ch'

  config.vm.synced_folder '.', '/home/vagrant/janus-gateway-js'

  config.vm.network :private_network, ip: '10.10.11.17'
  config.vm.network :public_network, :bridge => 'en0: Wi-Fi (AirPort)'

  config.librarian_puppet.puppetfile_dir = 'puppet'
  config.librarian_puppet.placeholder_filename = '.gitkeep'
  config.librarian_puppet.resolve_options = {:force => true}

  config.vm.provision :puppet do |puppet|
    puppet.environment_path = 'puppet/environments'
    puppet.environment = 'development'
    puppet.module_path = 'puppet/modules'
  end

  if Vagrant.has_plugin? 'landrush'
    config.landrush.enable
    config.landrush.tld = 'dev.cargomedia.ch'
    config.landrush.host 'janus-gateway-js.dev.cargomedia.ch'
  end

end