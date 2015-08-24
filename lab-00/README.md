# Lab 0 - Lab Environment Setup

  Lab Objectives:

  0. Setup your own git fork of these labs
  0. Document Public IP and EC2 Internal IP addresses of lab instances
  0. Checkout (clone) this repository into your Jumper instance


## Setup Github Lab Repository

  0. In a new tab, [Create a Github account](https://github.com/join) or [Login](https://github.com/login)

    ![Create an account](img/github-create.png)
      
  0. Return to this tab, refresh, you are now logged in.

  0. Star and this lab's repository

    If you aren't already here it is located at https://github.com/alta3/openstack-labs
    
    ![Star this repository](img/github-star.png)

    > :white_check_mark: **Additional Info**:
    >
    > Staring is like a bookmark on github.com,  you can view and search your stared repositories at [github.com/stars](github.com/stars)

  0. Fork the lab repository into your account

    ![Fork this repository](img/github-fork1.png)

    ![Fork this repository](img/github-fork2.png)

    ![Fork this repository](img/github-fork3.png)

    From this point on you can edit and commit changes to your own copy 
    of the lab repository.  You can do this from right inside of github 
    (click edit on any file)

## Lab environment 

  This lab will utilize three hosts.  Below is a brief description of each host and 
  what it will be used for 

  **Jumper**: 
  
  A jumper is a simple linux machine you will use as a launching point into the lab environment.  
  We will ssh into this host in order to connect to all other instances in the lab environments. This machine will retain
  a copy of student.pem, which serves as an authentication key, for all of the machines you will admin.
  
  :red_circle: TODO include student.pem in jumper

  **Controller**:
   
  :red_circle: TODO explain Controller

  **Compute**: 

  :red_circle: TODO explain Compute

## Connect to Lab Instances


  **Lab Instance Detials**

| Attribute          | Jumper   | Controller | Compute   |
| ------------------ | -------- | ---------- | --------- |
| Size               | t2.micro | t2.medium  | t2.medium |
| OS image           | CentOS 7 | CentOS 7   | CentOS 7  |
| Public IP address  | x.x.x.x  | x.x.x.x    | x.x.x.x   |
| Private IP address | x.x.x.x  | x.x.x.x    | x.x.x.x   |

  0. Your instructor will provide you three public IP addresses.  
    Edit this README.md file and add the public IP addresses for the appropriate hosts.

    Alternatively (and perhaps additionally), also record all of this information on a piece of paper.
  
    :red_circle: TODO Pictures of editing a github file

  0. Record your instance's internal IP address in the table
    
     * `ssh centos@<Public IP Address of JUMPER> -i student.pem`
       
        If using PuTTy, login as 'centos' and use the student.ppk keyfile (takes place of a password)

     * `ip addr show dev eth0`
       
        Record the displayed IPv4 address, not the IPv6 address. When you record this address, be sure to note that it is jumper so you don't get confused. In the following example, your IPv4 address would occupy the location of x.x.x.x
        
        ```
        $ ip addr show dev eth0
        
    2: eth0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 9001 qdisc pfifo_fast state UP qlen 1000
        link/ether 0a:6f:52:8c:f0:ef brd ff:ff:ff:ff:ff:ff
        inet x.x.x.x/24 brd 192.168.0.255 scope global dynamic eth0
          valid_lft 2829sec preferred_lft 2829sec
        inet6 fe80::86f:52ff:fe8c:f0ef/64 scope link
          valid_lft forever preferred_lft forever
        ```

  0. Set the hostname on 'jumper' to help with command line differentiation

    * `sudo yum install -y vim nano`
    
        These hosts are super bare-bones. This command installs nano, a common (user friendly) CLI text editor. You can use vi or vim, however, all lab instructions will be given assuming the use of nano.
        
    * `sudo hostname jumper`
    
        This command sents the name of the 'jumper' machine to 'jumper', for the current session. Please use 'jumper' and not an inventive naming scheme. This helps make the troubleshooting process manageable.

    * `sudo nano /etc/hosts`
    
        Add a single line to the bottom of /etc/hosts where x.x.x.x is the internal eth0 IPv4 address of your JUMPER machine (you just recorded this). This will ensure that the machine can resolve its own local hostname to an IP address.
        
        `x.x.x.x jumper`
        
        After you have added this file, save and exit. If this is your first time working with nano, press (CTRL + o), press ENTER, then press (CTRL + x)
  
    * `sudo nano /etc/hostname`
  
      This command edits the hostname file for the local machine. By editing this file, we are ensuring that the machine is still named 'jumper' even after a reboot. Delete anything in this file (usually just one line). The only content of the file should be the single, lowercase, name of the instance as follows:
      
      `jumper`
      
       After you have added this file, save and exit. If this is your first time working with nano, press (CTRL + o), press ENTER, then press (CTRL + x)
      
    * `exit`
    
        The terminal session will exit. After it does, log right back in...
    
    * `ssh centos@<Public IP Address of JUMPER> -i student.pem`
    
        Of course, you might be using PuTTy to perform the above command. Regardless of how you start an SSH session with jumper, bash should look like this now: `[centos@jumper ~]`

  0. Log into controller and learn the internal IP address
  
      From jumper, issue the following command to log into the controller. If prompted, respond with 'yes' to import the new key.

    * `ssh centos@<Public IP Address of CONTROLLER> -i student.pem`
    
    * `ip addr show dev eth0`
    
        Record the displayed IPv4 address, not the IPv6 address. When you record this address, be sure to note that it is CONTROLLER so you don't get confused.
        
    * `sudo yum install -y vim nano`
    
    * `sudo hostname controller`
        
        This command sets the name of the 'controller' to 'controller', for the current session. Please use 'controller' and not an inventive naming scheme. This helps make the troubleshooting process manageable.

    * `sudo nano /etc/hosts`
    
        Add a single line to the bottom of /etc/hosts where x.x.x.x is the internal eth0 IPv4 address of your CONTROLLER machine (you just recorded this). This will ensure that the machine can resolve its own local hostname to an IP address.
        
        `x.x.x.x controller`
        
        After you have added this file, save and exit. If this is your first time working with nano, press (CTRL + o), press ENTER, then press (CTRL + x)
  
    * `sudo nano /etc/hostname`
  
      This command edits the hostname file for the local machine. By editing this file, we are ensuring that the machine is still named 'controller' even after a reboot. Delete anything in this file (usually just one line). The only content of the file should be the single, lowercase, name of the instance as follows:
      
      `controller`
      
      After you have added this file, save and exit. If this is your first time working with nano, press (CTRL + o), press ENTER, then press (CTRL + x)
      
  0. Prevent hostname updates on reboot & add controller internal IP to jumper

      CentOS has the ability to detect when it is running in a cloud (such as AWS), it checks for a new hostname everytime it is launched. To ensure a predictable hostname, we'll disable this feature.

    * `sudo nano /etc/cloud/cloud.cfg`

    Comment out these two entries under `cloud_init_modules`:

    ```
    - set_hostname
    - update_hostname
    ```
    
    When you are done editing /etc/cloud/cloud.cfg those entires should look like this:
    
    ```
    # - set_hostname
    # - update_hostname
    ```
    
    If this is your first time working with nano, press (CTRL + o), press ENTER, then press (CTRL + x)
      
    * `exit`
    
        You should now be back at your jumper machine (bash should look like this now: `[centos@jumper~]`
        
        We want to add the INTERNAL IP address of the CONTROLLER to the /etc/hosts in JUMPER. Therefore, once again, issue the following command:
        
    * `sudo nano /etc/hosts`
    
        Add a single line to the bottom of /etc/hosts where x.x.x.x is the internal eth0 IPv4 address of your CONTROLLER machine. This will ensure that the JUMPER machine can resolve controller to the local IP address of the CONTROLLER.
    
       `x.x.x.x controller`
    
        After you have added this file, save and exit. If this is your first time working with nano, press (CTRL + o), press ENTER, then press (CTRL + x)        
  
  0. Log into compute and learn the internal IP address

    From the jumper box, issue the following command to log into compute. If prompted, respond with 'yes' to import the new key.

    * `ssh centos@<Public IP Address of COMPUTE> -i student.pem`
    
    * `ip addr show dev eth0`
    
        Record the displayed IPv4 address, not the IPv6 address. When you record this address, be sure to note that it is COMPUTE so you don't get confused.
        
    * `sudo yum install -y vim nano`
    
    * `sudo hostname compute`
        
        This command sets the name of the 'compute' to 'compute', for the current session. Please use 'compute' and not an inventive naming scheme. This helps make the troubleshooting process manageable.

    * `sudo /etc/hosts`
    
        Add a single line to the bottom of /etc/hosts where x.x.x.x is the internal eth0 IPv4 address of your COMPUTE machine (you just recorded this). This will ensure that the machine can resolve its own local hostname to an IP address.
        
        `x.x.x.x compute`
        
        After you have added this file, save and exit. If this is your first time working with nano, press (CTRL + o), press ENTER, then press (CTRL + x)
  
    * `sudo nano /etc/hostname`
  
      This command edits the hostname file for the local machine. By editing this file, we are ensuring that the machine is still named 'compute' even after a reboot. Delete anything in this file (usually just one line). The only content of the file should be the single, lowercase, name of the instance as follows:
      
      `compute`
      
      After you have added this file, save and exit. If this is your first time working with nano, press (CTRL + o), press ENTER, then press (CTRL + x)
      
  0. Prevent hostname updates on reboot & add compute internal IP to jumper

      CentOS has the ability to detect when it is running in a cloud (such as AWS), it checks for a new hostname everytime it is launched. To ensure a predictable hostname, we'll disable this feature.

    * `sudo nano /etc/cloud/cloud.cfg`

    Comment out these two entries under `cloud_init_modules`:

    ```
    - set_hostname
    - update_hostname
    ```
    
    When you are done editing /etc/cloud/cloud.cfg those entires should look like this:
    
    ```
    # - set_hostname
    # - update_hostname
    ```
    
    If this is your first time working with nano, press (CTRL + o), press ENTER, then press (CTRL + x)
      
    * `exit`
    
        You should now be back at your jumper machine (bash should look like this now: `[centos@jumper~]`
        
        We want to add the INTERNAL IP address of the COMPUTE to the /etc/hosts in JUMPER. Therefore, once again, issue the following command:
        
    * `sudo nano /etc/hosts`
    
        Add a single line to the bottom of /etc/hosts where x.x.x.x is the internal eth0 IPv4 address of your COMPUTE machine. This will ensure that the JUMPER machine can resolve controller to the local IP address of the COMPUTE.
    
       `x.x.x.x compute`
    
        After you have added this file, save and exit. If this is your first time working with nano, press (CTRL + o), press ENTER, then press (CTRL + x)        

  0. Prevent hostname updates on reboot

      CentOS has the ability to detect when it is running in a cloud (such as AWS), it checks for a new hostname everytime it is launched. To ensure a predictable hostname, we'll disable this feature.

    * `sudo nano /etc/cloud/cloud.cfg`

    Comment out these two entries under `cloud_init_modules`:

    ```
    - set_hostname
    - update_hostname
    ```
    
    When you are done editing /etc/cloud/cloud.cfg those entires should look like this:
    
    ```
    # - set_hostname
    # - update_hostname
    ```
    
    If this is your first time working with nano, press (CTRL + o), press ENTER, then press (CTRL + x)
    
    * `sudo reboot`
    
      It may take around 180 seconds for the machine to fully powercycle.

## Log back into jumper, test your work, install git, and clone your forked repository

  0. Log back into jumper. Of course you could use PuTTy, or if working from the CLI, issue:
    * `ssh centos@<Jumper Public IP> -i student.pem`
      
  0. Test that the following commands resolve and receive ping responses. If they do not, now is the time to let the instructor know. FYI, you'll need to press (CTRL + C) in order to stop pinging.
     * `ping jumper`
     * `ping controller`
     * `ping compute`

  0. Install git to the linux CLI. This is a standarded utility you will NEED to understand if you wish to work with OpenStack, as git is the service that distrubutes the OpenStack project. In order to force git comprehension, we will also use git to distribute our lab manual.
     
      * `sudo yum install -y git`
    
  0. Now clone the Alta3 Reserach OpenStack lab manual

      * `git clone https://github.com/<Your username>/openstack-labs`

  0. :red_circle: TODO fill this out with instructions and screen shots
    * make a change to a file
    * commit the change
    * push the change into github so it can be viewed on the webpage


#### [Continue to the next lab](../lab-01)
