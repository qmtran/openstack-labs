# Lab 1 - RDO Controller

  Lab Objectives:

  0. Install a PackStack (RDO) controller

## Connect to your _controller_ instance:
  0. `chmod 400 student.pem`
  0. `ssh centos@<CONTROLLER IP> -i student.pem`
  0. `sudo whoami` 

## Install PackStack:

:red_circle: TODO: brief paragraph about packstack (i.e. that it is puppet based)

  0. `sudo yum update -y`
  0. `sudo yum install -y https://rdoproject.org/repos/rdo-release.rpm`
  0. `sudo yum isntall openstack-packstack vim htop -y`
  0. Enable root ssh access

     0. Alter SSH Daemon config to permit root login and restart it to take effect
      
        * `sudo vim /etc/ssh/sshd_config` or `sudo nano /etc/ssh/sshd_config`
       
          ``` 
            ...
            # Authentication:

            #LoginGraceTime 2m
            PermitRootLogin Yes
            #StrictModes yes
            #MaxAuthTries 6
            #MaxSessions 10
            ...
          ```

        *  `sudo service sshd restart`

     0. Setup root private key login
        * `ssh root@localhost` - expected failure
        * `cat /root/.ssh/authorized_keys` - the keys currently allowed
        * `cat /home/centos/.ssh/id_rsa.pub` - the controller's public key (if absent generate with `ssh-keygen`)
        * `cat /home/centos/.ssh/id_rsa.pub | sudo tee -a /root/.ssh/authorized_keys` - append controllers key
        * `ssh localhost` - expected success

  0. Generate a PackStack Config gile (answers)

     * `packstack --gen-answer-file packstack-answers.txt`

  0. Edit packstack answers to tweak install configuration 
  
     * `vim packstack-answers.txt` or `nano packstack-answers.txt`

       ```
         CONFIG_CONTROLLER_HOST=<CONTROLLER IP> 
         CONFIG_KEYSTONE_ADMIN_PW=supersecret

       ```

  0. `packstack --answers-file packstack-answers.txt`

  0. Login to the OpenStack Horizon Web Interface by navigating your browser to the public IP address of your instance, explore the accessible pages and fill in the table of information

    ![Image of login](img/horizon-login.png)
    
    ![Image Dashboard](img/horizon-dashboard.png)

    :red_circle: TODO items from interface

    | Info to find | Value |
    | -------------| ----- |
    | Item 1 | |
    | Item 2 | |
    

  For future reference see [RDO Quick Start](https://www.rdoproject.org/Quickstart)
  
#### [Next Lab](../lab-02)    
