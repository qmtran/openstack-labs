# Lab 1 - Controller Install

  Lab Objectives:

  0. Install a OpenStack controller (with RDO & PackStack)

## Connect to your controller instance:

  0. `chmod 400 student.pem`
  0. `ssh centos@<Controller IP> -i student.pem`

## Install PackStack on controller:

  :red_circle: TODO: brief paragraph about packstack (i.e. that it is puppet based)

  0. Install PackStack dependencies
  
    NOTE: bash should look like this now: `[centos@controller ~]`

    * `sudo yum update -y`
    * `sudo yum install -y https://rdoproject.org/repos/rdo-release.rpm`
    * `sudo yum install -y openstack-packstack vim nano screen`

  0. Enable root ssh access 

     `packstack` requires the ability to ssh as root into the target machine 
     (the machine which is getting OpenStack services are being installed to, 
     in our case the controller instance).  The following config changes enables
     key-enabled root ssh login to our controller and setup authorized keys to allow
     the centos user to ssh in as root using their private key. 

     0. Alter SSH Daemon config to permit root login and restart it to take effect
     
          Edit the sshd_config file by removing the comment on PermitRootLogin and set it to yes.
      
        * `sudo nano /etc/ssh/sshd_config`
       
          ``` 
          # --- snip --- #
          # Authentication:

          #LoginGraceTime 2m
          PermitRootLogin yes
          #StrictModes yes
          #MaxAuthTries 6
          #MaxSessions 10
          # --- end-snip --- #
          ```

        *  `sudo systemctl restart sshd.service`

     0. Setup root private key login and appropriate keys

        * `ssh root@localhost` - expected failure
        * `sudo cat /root/.ssh/authorized_keys` - the keys currently allowed
        * `ssh-keygen` - accept defaults
        * `cat /home/centos/.ssh/id_rsa.pub` - the user's public key
        * `cat /home/centos/.ssh/id_rsa.pub | sudo tee -a /root/.ssh/authorized_keys` - append controllers key
        * `sudo cat /root/.ssh/authorized_keys` - one more key should be there
        * `ssh root@localhost` - expected success
        * `exit` - exit successful ssh session

  0. Run packstack (newlines and `\`'s are for clarity, not required)

    Replace x.x.x.x below with the Controller Internal IP address

    * `packstack --install-hosts=x.x.x.x --keystone-admin-passwd=supersecret --provision-demo=n`
  
    Expected Result:

    ```
    Welcome to the Packstack setup utility

    The installation log file is available at: /var/tmp/packstack/20150824-185121-1WICWt/openstack-setup.log

    Installing:
    Clean Up                                             [ DONE ]
    Discovering ip protocol version                      [ DONE ]
    Setting up ssh keys                                  [ DONE ]
    Preparing servers                                    [ DONE ]
    Pre installing Puppet and discovering hosts' details [ DONE ]
    Adding pre install manifest entries                  [ DONE ]
    Setting up CACERT                                    [ DONE ]

    ----- snip, many hundreds of seconds pass -----

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
 
  0. Fix the Horizon Dashboard ServerAlias configuration

    * `sudo nano /etc/httpd/conf.d/15-horizon_vhost.conf`

    ```
    # Please replace add another Server Alias like shown below and replace x.x.x.x with the Controller Public IP address
    # ---- snip ---- #
    ## Server aliases
    ServerAlias 192.168.0.195
    ServerAlias ip-192-168-0-195.ec2.internal
    ServerAlias localhost
    ServerAlias x.x.x.x
    # -- end-snip -- #
    ```

    * `sudo systemctl restart httpd.service`

  0. Fix the nova vnc proxy service

    * `sudo vim /etc/nova/nova.conf` or `sudo nano /etc/nova/nova.conf`

    ```
    # Please replace x.x.x.x below with the Controller Public IP address
    novncproxy_base_url=http://x.x.x.x:6080/vnc_auto.html
    vncserver_proxyclient_address=x.x.x.x

    ```
    * `sudo systemctl restart openstack-nova-novncproxy.service`
    * `sudo systemctl restart openstack-nova-compute.service`


  Official reference documentation: [RDO Quick Start](https://www.rdoproject.org/Quickstart)
  
#### [Continue to the next lab](../lab-02)
