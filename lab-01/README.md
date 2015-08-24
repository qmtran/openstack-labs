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
    * `sudo yum install -y openstack-packstack vim nano screen`

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

  0. Run packstack (`\` indicates newlines, not required)

    ```
    # replace x.x.x.x with the controller public ip address
    packstack \
      --install-hosts=x.x.x.x \
      --keystone-admin-passwd=supersecret \
      --provision-demo=n
    ```
  
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

  0. Fix the nova vnc proxy service

    * `sudo vim /etc/nova/nova.conf` or `sudo nano /etc/nova/nova.conf`

    ```
    # Please replace x.x.x.x with the Controller Public IP address
    vncserver_proxyclient_address=x.x.x.x

    ```
    * `sudo systemctl restart openstack-nova-novncproxy.service`
    * `sudo systemctl restart openstack-nova-compute.service`

  0. `sudo reboot`

  Official reference documentation: [RDO Quick Start](https://www.rdoproject.org/Quickstart)
  
#### [Continue to the next lab](../lab-02)
