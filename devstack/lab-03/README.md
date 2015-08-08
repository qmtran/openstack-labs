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
  0. Edit the 'local.conf` file, it should look like [example-local.conf](example-local.conf) 
    
     `nano local.conf` or `vim local.conf`

  0. Run `ip addr show`
  0. Run stack.sh, this will take a little bit less time that Lab 1
    
     `./stack.sh 2>&1 | tee stack.log`

  0. Run `ip addr show` again and notice the added interfaces and bridges
  0. Login to the OpenStack Horizon Web Interface by navigating your browser to the public IP address of the controller
  0. Admin > System > Hypervisors and marvel at the number of Hypervisors
   
     ![TWO HYPERVISORS](img/horizon-twohyper.png)

  0. Launch another Instance and ping between the two currently running instances 

     Project > Compute > Instances > Launch Instance
     
     ![Instances](img/horizon-instances.png)
     ![Ping Pong](img/horizon-ping.png)
     ![Ping Pong](img/horizon-pong.png)
      
