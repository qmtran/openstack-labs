# Instructor Setup
  
  Each lab will have an instructor-README.md like this one. 
  This is wheres spcific infrastructure requirements and pre-lab setup will be explained. 
  (i.e. what type of hosts and security groups need launched).

## EC2

  All of the labs in this repository rely on a shared private key that is commited to this repository.
  This is INSECURE and is done intentionally for the convienences of a lab environment.
  It is definitely worth mentioning to students that they should never do this in 'the real world'
  The below steps explain the process of updating the private key for each new course offering.
  
  0. Create a shared ssh private key
  0. :red_circle: TODO, document this 

## Ansible

  As an instructor it is super useful to have ansible installed and ready to use.
  Every lab should contain a /ansible directory with a playbook that automates the student portion of the lab.
  This is super useful if you need to get the student's environment into a known state.
  A great example would be a student who joins late and needs previous labs completed in order to continue with the class.
  Ansible is used to automate and test lab environments.  Think of it as a robo-student.  You will need to install and configure a few files in order for ansible to be usable within the lab environment.

  0. [Install Ansible](http://docs.ansible.com/ansible/intro_installation.html) on your system

## Connectivity Testing

  Each lab will have a `lab-hosts` file.  Once the public IP addresses are set in this file you can test connectivity:
  
  `ansible -i lab-hosts all -m ping -vvvv`
  
