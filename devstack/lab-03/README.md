# Lab 3 - DevStack Compute

  Lab Objectives:

  0. Install a DevStack Compute node

## Connect to your controller instance:
  0. `ssh ubuntu@W.X.Y.Z -i student.pem`
  0. `sudo whoami` 

## Install DevStack:
  0. `sudo apt-get install git`
  0. `git clone https://git.openstack.org/openstack-dev/devstack`
  0. `cd devstack`
  0. `cp samples/local.conf local.conf`
  0. `ip addr show dev eth0` and record your instance's internal IP address in the [Lab 0 table](../README.md) 
  0. `nano local.conf` or `vim local.conf`
      
      Edit the 'local.conf` file, it should look like [example-local.conf](example-local.conf) 

