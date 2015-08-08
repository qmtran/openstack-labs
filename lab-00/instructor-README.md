# Instructor Setup

## EC2

  Lots of notes will go here about how to setup the EC2 instances for the students.
  0. Turn on instances
  0. Create a shared ssh private key

## Ansible
  Ansible is used to automate and test lab environments.  Think of it as a robo-student.  You will need to install and configure a few files in order for ansible to be usable within the lab environment.

  0. [Install Ansible](http://docs.ansible.com/ansible/intro_installation.html) on your system
  0. Update the [lab-hosts](../lab-hosts) public IP addresses (`ansible_ssh_host`) of the instances

## Update && Upgrade instances

  0. Each lab will have a `lab-hosts` file.  Once the public IP addresses are set in this file you can test connectivity to the hsts
  
  `ansible -i lab-hosts all -m ping -vvvv`
  
  0. Up[date,grade]: `ansible-playbook -i lab-hosts lab-00/ansible/main.yml`
