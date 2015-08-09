# Lab 1 - RDO Controller

  Lab Objectives:

  0. Install a RDO controller

## Connect to your _controller_ instance:
  0. `chmod 400 student.pem`
  0. `ssh centos@<CONTROLLER IP> -i student.pem`
  0. `sudo whoami` 

## Install DevStack:

  For future reference see [RDO Quick Start](https://www.rdoproject.org/Quickstart)

  0. `sudo yum update -y`
  0. `sudo yum install -y https://rdoproject.org/repos/rdo-release.rpm`
  0. `sudo yum isntall openstack-packstack vim htop -y`
  0. `packstack --gen-answer-file packstack-answers.txt`

  0. Enable root ssh access
     0. Permit root login and restart ssh daemon
      
        * `sudo vim /etc/ssh/sshd_config`
        * `sudo nano /etc/ssh/sshd_config`
       
          ``` 
            # Authentication:

            #LoginGraceTime 2m
            PermitRootLogin Yes
            #StrictModes yes
            #MaxAuthTries 6
            #MaxSessions 10
          ```

        *  `sudo service sshd restart`

     0. Setup root private key login
        * `ssh root@localhost` - expected failure
        * `cat /root/.ssh/authorized_keys` - the keys currently allowed
        * `cat /home/centos/.ssh/id_rsa.pub` - the controller's public key (if absent generate with `ssh-keygen`)
        * `cat /home/centos/.ssh/id_rsa.pub | sudo tee -a /root/.ssh/authorized_keys` - append controllers key
        * `ssh localhost` - expected success

