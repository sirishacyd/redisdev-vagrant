Vagrant.configure("2") do |config|
    config.vm.box = "ubuntu/bionic64"
    config.vm.hostname = "redisdev"
    config.vm.network "forwarded_port", guest: 6379, host: 9001
    config.vm.synced_folder ".", "/vagrant", disabled: true
  
    if ENV['REDIS_SRC_PATH']
      config.vm.synced_folder ENV['REDIS_SRC_PATH'], "/home/vagrant/redis"
    end
  
    config.vm.provision "shell", inline: <<-SHELL
      sudo apt-get update
      sudo apt-get install -y build-essential tcl
      
      cd /home/vagrant/redis
      make
      make test
  
      echo "You can start the Redis server with ./redis-server from the src directory."
    SHELL
  end
  