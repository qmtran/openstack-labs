# Lab 0

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

    From this point on you can edit and commit changes to your own copy of the lab repository.  You can do this from right inside of github (click edit on any file)


## Connect to Jumper Instance

  A jumper is a simple linux machine you will use as a launching point into the lab environment.  
  We will ssh into this host in order to connect to all other instances in the lab environments.

  *Jumper Instance Detials*

  | Attribute          | Value    |
  | ------------------ | -------- |
  | size               | t2.micro |
  | OS image           | CentOS 7 -x86_64- with Updates HVM |
  | Public IP address  | x.x.x.x |
  | Private IP address | y.y.y.y |

  0. Edit the Public IP address above (in your forked repo) and change 
     x.x.x.x to be the public IP address provided by your instructor
  0. `ssh root@<Jumper Public IP Address> -i student.pem`
  0. `sudo yum install vim nano -y` # this host is super bare-bones
  0. `sudo hostname jumper`
  0. `sudo vi /etc/hostname` or `sudo nano /etc/hostname`
    
    ```
    jumper
    ```

  0. `exit`
  0. `ssh root@<Jumper Public IP Address> -i student.pem`

    bash should look like this now: `[centos@jumper ~]`

  0. `ip addr show dev eth0`
  0. Edit the Public IP address above (in your forked repo) and change 
     y.y.y.y. to be the private IP address (eth0)


## Checkout your forked repository

  0. `sudo yum install git -y`
  0. `git clone https://github.com/<Your username>/openstack-labs"

  * :red_circle: TODO fill this out with instructions and screen shots
  0. make a change to a file
  0. commit the change
  0. push the change into github so it can be viewed on the webpage


#### [Continue to lab-01](../lab-01)
