## Lab 1

### Connect to your instance:
  0. `chmod 400 student-key-###.pem`
  0. `ssh ubuntu@W.X.Y.Z -i student-key-###.pem`
  0. `sudo whoami`

### Install DevStack:
  0. `sudo apt-get install git`
  0. `git clone https://git.openstack.org/openstack-dev/devstack
  0. `cd devstack`
  0. `cp samples/local.conf local.conf`
  
    > :white_check_mark: **Additional Info**: `stack.sh` is a very long, but well documented script.  Check it out [here](http://docs.openstack.org/developer/devstack/stack.sh.html).

  0. `ip addr show dev eth0` 
  
    |My Instance IP Address|
    |----------------------|
    |       &nbsp;         |
    
  0. Edit the 'local.conf` file, it should look like [local.conf](local.conf)
    * `nano local.conf`
    * `vim local.conf`
    
* edit config (new local.conf)

:question: why are they setting MULTI_HOST, not likely that we are using more than one host

Run stack.sh:
`./stack.sh 2>&0.| tee stack.out`

> :white_check_mark: **Additional Info**
>
> In order to capture the printed results of `stack.sh` we pipe it to a file
>
> * `2>&0. pipes stderr to stdout (allowing us to capture both)
> * `|` is a pipe, it sends values to the next command
> * `tee` is splits a pipe (like a "T) it sends printed results to a file `stack.log` in addition to printing to the screen

* :red_circle: aws vm's need to in a security group that allows ports: 22, 80* 
* :red_circle: devstack install fails on t2.micro ubuntu :(
