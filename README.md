# redisdev-vagrant
# RedisDev Vagrant

This repository provides a Vagrant configuration for a Redis development environment.

## Prerequisites

* Git
* Vagrant
* VirtualBox

## Usage

1. Clone your Redis repository to a location of your choice.
2. Clone this repository.
3. From the root directory of this repository, run `REDIS_SRC_PATH=/path/to/redis vagrant up`, replacing `/path/to/redis` with the path to your cloned Redis repository.

The Redis server will be accessible from port 9001 on your host machine.
