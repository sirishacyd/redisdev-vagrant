# Vagrant Redis Development Environment

This repository provides a Vagrant configuration to create a development environment for Redis.

## Prerequisites

- [Vagrant](https://www.vagrantup.com/downloads)
- [VirtualBox](https://www.virtualbox.org/wiki/Downloads)
- Clone of [Redis](https://github.com/redis/redis) repository on your local machine

## Setup

1. **Clone this repository**:

    ```
    git clone https://github.com/sirishacyd/redisdev-vagrant.git
    ```

2. **Navigate to the cloned repository**:

    ```
    cd redisdev-vagrant
    ```

3. **Configure Redis Source Path**:

    Open the `Vagrantfile` in your favorite text editor. Find the line that says `redis_source_path = File.expand_path("~") + "/path-to-your-redis-repo"`. Replace `path-to-your-redis-repo` with the actual path to your Redis clone on your local machine.

    If you want to specify your Redis source path via an environment variable, you can comment out the above line and uncomment this line: `# redis_source_path = ENV['REDIS_SOURCE_PATH']`. Then set the `REDIS_SOURCE_PATH` environment variable in your shell before running `vagrant up`:

    ```
    export REDIS_SOURCE_PATH=path-to-your-redis-repo
    ```

4. **Start the VM and provision it**:

    ```
    vagrant up
    ```

    This command will download the base VM image (if it's not already downloaded), start the VM, and run the provisioning script.

5. **SSH into the VM**:

    ```
    vagrant ssh
    ```

    You are now logged into your VM. The Redis source code will be available in the `~/redis` directory.

## Building Redis

To build Redis, use the following command in the `~/redis` directory:

```
cd ~/redis
make
```

## Running Redis

To run the Redis server, use the following command in the `~/redis` directory:

```
cd ~/redis
./src/redis-server
```

## Testing

### Building Redis
- Once the virtual machine (VM) is up and running, Redis can be built using the make command. The process has been automated such that it is executed during the VM's provisioning stage.

However, if you need to rebuild Redis, you can do so manually as follows:

SSH into the VM:
```
vagrant ssh
```
You should now be logged in to the VM. The Redis source code will be in the ~/redis directory.

Navigate to the Redis directory:

```
cd ~/redis
```
Build Redis using the make command:
```
make
```
This will compile the Redis source code and create the Redis server binary. If everything is set up correctly, you should see output indicating that various C files are being compiled, and eventually, the process should complete without errors.

### Tested Environment

- macos 10.4
- Intel X86 chipset