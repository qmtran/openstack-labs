# Lab 5 - DevStack cli 

  Lab Objectives:

  0. Become familiar with the openstack command line utility

## Setup

  0. Connect (ssh) into the controller
  0. `cd ~/devstack`
  0. `source openrc admin`
  0. `openstack` (starts openstack promt)

## Create a Project and User

  0. `project create Alta3Project`

     ![Create Project](img/os-project.png)

  0. `user create --email ubuntu@localhost --project Alta3Project --password supersecret student1

     ![Create User](img/os-user.png)

## List all the things!

  0. `endpoint list` - service endpoints and their ID's
  
     :red_circle: TODO ![Endpoints](img/os-endpoint.png) 

  0. `hypervisor list` - compute hypervisors

     ![Hypervisors](img/os-hyperv.png) 

  0. `host list` - openstack services and the host they are running on

     ![Hosts](img/os-hosts.png) 

  0. `image list` - glance OS images (from basic stack.sh install)

     ![Images](img/os-image.png) 

  0. `flavor list` - instance flavors (resources)

     ![Flavor Flave](img/os-flavor.png) 

  0. `user list` - user IDs

     ![User IDs](img/os-user2.png) 

  0. `project list` - projects 

     ![Projects](img/os-projects.png) 

  0. `catalog list` - API endponts

     ![Catalog](img/os-catalog.png) 

  0. `help` - all commands
  0. `exit`


## Switch users for a few other commands

  0. `source openrc student1`
  0. `openstack`
  0. `server list` (list instances)


