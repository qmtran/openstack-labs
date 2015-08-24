# Lab 1 - Controller Install

  Lab Objectives:

  0. Install a OpenStack Controller (with RDO & PackStack)

## Connect to your controller instance:

  0. `chmod 400 student.pem`
  0. `ssh centos@<Controller IP> -i student.pem`

## Install PackStack:

  :red_circle: TODO: brief paragraph about packstack (i.e. that it is puppet based)

  0. Install dependencies 

    * `sudo yum update -y`
    * `sudo yum install -y https://rdoproject.org/repos/rdo-release.rpm`
    * `sudo yum install -y openstack-packstack vim nano htop screen`

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
        * `exit` - exit successful ssh session

  0. Generate a PackStack Config file (answers)

     * `packstack --gen-answer-file packstack-answers.txt`

  0. Edit packstack answers to tweak install configuration 
  
     * `vim packstack-answers.txt` or `nano packstack-answers.txt`
     
       Find these configuration options and replace them with the appropriate values

       ```
       # Please replace both x.x.x.x below with the controller public IP
       CONFIG_CONTROLLER_HOST=x.x.x.x
       CONFIG_KEYSTONE_ADMIN_PW=supersecret
       CONFIG_PROVISION_DEMO=n
       CONFIG_PROVISION_ALL_IN_ONE_OVS_BRIDGE=n
       ```

       These Nova and VNC are not included by default in the answers file.  
       Add these configurations to the bottom of the answers file

       ```
       # Please replace x.x.x.x below with the controller **public** IP
       CONFIG_NOVA_VNCPROXY_HOST=x.x.x.x
       NOVNCPROXY_URL="http://x.x.x.x:6080/vnc_auto.html"
       NOVA_VNC_ENABLED=True

       # Please replace x.x.x.x below with the controller **internal** IP
       VNCSERVER_LISTEN=x.x.x.x
       VNCSERVER_PROXYCLIENT_ADDRESS=x.x.x.x
       ```
  
     :red_circle: run this to make sure configurations got set correctly
     `cat /etc/nova/nova.conf | grep 'novnc\|vncserver'`


  0. `packstack --answer-file packstack-answers.txt`
  
    Expected Result:

    ```
    **** Installation completed successfully ******

    Additional information:
     * Time synchronization installation was skipped. Please note that unsynchronized time on server instances might be problem for some OpenStack components.
     * File /root/keystonerc_admin has been created on OpenStack client host 52.2.224.157. To use the command line tools you need to source the file.
     * To access the OpenStack Dashboard browse to http://x.x.x.x/dashboard .
    Please, find your login credentials stored in the keystonerc_admin in your home directory.
     * To use Nagios, browse to http://x.x.x.x/nagios username: nagiosadmin, password: 888aa1cb6e544ffa
     * Because of the kernel update the host x.x.x.x requires reboot.
     * Because of the kernel update the host x.x.x.x requires reboot.
     * The installation log file is available at: /var/tmp/packstack/20150824-002755-FL1Fzg/openstack-setup.log
     * The generated manifests are available at: /var/tmp/packstack/20150824-002755-FL1Fzg/manifests
    ```

  0. `sudo reboot`

  Official reference documentation: [RDO Quick Start](https://www.rdoproject.org/Quickstart)
  
#### [Continue to the next lab](../lab-02)
