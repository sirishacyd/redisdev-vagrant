# Every Vagrant development environment requires a box to build off of.
Vagrant.configure("2") do |config|
  # Use Ubuntu 18.04 as base image
  config.vm.box = "ubuntu/bionic64"

  # The forwarded_port option allows you to access a port on your host machine and have all data forwarded to a port on the guest machine, over TCP or UDP.
  config.vm.network "forwarded_port", guest: 6379, host: 9001

  # User-configurable Redis source location
  redis_source_path = File.expand_path("~") + "/path-to-your-redis-repo" # Replace 'path-to-your-redis-repo' with the path to your local redis clone

  # If you want your users to specify the path to their Redis repo as an environment variable:
  # redis_source_path = ENV['REDIS_SOURCE_PATH']

  # Synced folders enable Vagrant to sync a folder on the host machine to the guest machine.
  config.vm.synced_folder redis_source_path, "/home/vagrant/redis"

  # The provider line configures provider-specific configuration, which allows you to fine-tune provider-specific settings.
  config.vm.provider "virtualbox" do |v|
    # Name the VM 'redisdev'
    v.name = "redisdev"
    # Customize the amount of memory on the VM:
    v.memory = 1024
    # Customize the number of virtual CPUs on the VM:
    v.cpus = 2
  end

  # Provisioning is the process of getting your VM 'up and running'. This can mean a lot of things, but usually involves installing and configuring software on the machine.
  config.vm.provision "shell", inline: <<-SHELL
    sudo apt-get update
    sudo apt-get install -y build-essential tcl git
    # Optional: Clone Redis if not already cloned on the host
    # git clone https://github.com/redis/redis.git /home/vagrant/redis
    # Build Redis
    cd /home/vagrant/redis
    make
  SHELL
end
