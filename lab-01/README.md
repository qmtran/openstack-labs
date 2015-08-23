# Lab 1 - Controller

  Lab Objectives:

  0. Install a PackStack (RDO) controller

## Connect to your _controller_ instance:
  0. `chmod 400 student.pem`
  0. `ssh centos@<Controller IP> -i student.pem`
  0. `sudo whoami` 

## Install PackStack:

  :red_circle: TODO: brief paragraph about packstack (i.e. that it is puppet based)

  0. Install dependencies 

    * `sudo yum update -y`
    * `sudo yum install -y https://rdoproject.org/repos/rdo-release.rpm`
    * `sudo yum install -y openstack-packstack vim nano htop`

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

        *  `sudo systemctl restart sshd.service`

     0. Setup root private key login
        * `ssh root@localhost` - expected failure
        * `sudo cat /root/.ssh/authorized_keys` - the keys currently allowed
        * `ssh-keygen` - accept defaults
        * `cat /home/centos/.ssh/id_rsa.pub` - the controller's public key (if absent generate with `ssh-keygen`)
        * `cat /home/centos/.ssh/id_rsa.pub | sudo tee -a /root/.ssh/authorized_keys` - append controllers key
        * `sudo cat /root/.ssh/authorized_keys` - one more key should be there
        * `ssh root@localhost` - expected success

  0. Generate a PackStack Config file (answers)

     * `packstack --gen-answer-file packstack-answers.txt`

  0. Edit packstack answers to tweak install configuration 
  
     * `vim packstack-answers.txt` or `nano packstack-answers.txt`
     
       Find these configuration options and replace them with the appropriate values

       ```
       # Please replace both x.x.x.x below with the controller public IP
       CONFIG_CONTROLLER_HOST=x.x.x.x
       CONFIG_KEYSTONE_ADMIN_PW=supersecret
       CONFIG_NOVA_VNCPROXY_HOST=x.x.x.x
       ```

       These Nova and VNC are not included by default in the answers file
       Add these configurations to the bottom of the answers file

       ```
       # Please replace x.x.x.x below with the controller **public** IP
       NOVNCPROXY_URL="http://x.x.x.x:6080/vnc_auto.html"
       NOVA_VNC_ENABLED=True

       # Please replace x.x.x.x below with the controller **internal** IP
       VNCSERVER_LISTEN=x.x.x.x
       VNCSERVER_PROXYCLIENT_ADDRESS=x.x.x.x
       ```
  
     :red_circle: run this to make sure configurations got set correctly
     `cat /etc/nova/nova.conf | grep 'novnc\|vncserver'`


  0. `packstack --answer-file packstack-answers.txt`

  0. `sudo reboot`

  Official reference documentation: [RDO Quick Start](https://www.rdoproject.org/Quickstart)
  
#### [Next Lab](../lab-02)    
