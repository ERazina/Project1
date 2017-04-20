Vagrant.configure('2') do |config|
  # No automatic updates
  #config.vbguest.auto_update = false
  config.vm.box_check_update = false

  # Uncomment and complete the below three lines to set up the proxy
  # config.proxy.http = ''
  # config.proxy.https = ''
  # config.proxy.no_proxy = 'localhost,127.0.0.1'

  config.vm.define 'experteese', primary: true do |experteese|
    # We're going to use Ubuntu 16.04 x64
    experteese.vm.box = 'ubuntu/xenial64'
    # experteese.vm.box = 'bento/ubuntu-16.04'

    # Disabling anytime updates
    experteese.vm.box_check_update = false

    # Forwarding all necessary ports
    experteese.vm.network 'forwarded_port', # Default Rails app port
                          guest: 3000,
                          host: 3000
    experteese.vm.network 'forwarded_port', # Default Postgres port
                          guest: 5432,
                          host: 5432

    # Virtual machine's hostname
    experteese.vm.hostname = 'experteese'

    # Initial configuration script
    experteese.vm.provision 'shell', path: 'setup.sh'

    # We are going to use the following virtual environment:
    # - VirtualBox as a hypervisor
    # - Maximum 2GB RAM
    # - One CPU core
    experteese.vm.provider 'virtualbox' do |vm|
      vm.memory = 2048
      vm.name = 'experteese'
      vm.cpus = 1
    end
  end
end