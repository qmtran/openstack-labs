# openstack-labs

## Lab 1

Connect to Instance:
1. `chmod 400 student-key-###.pem`
1. `ssh ubuntu@W.X.Y.Z -i student-key-###.pem`
1. `sudo whoami`

Install DevStack:
1. `sudo apt-get install git`
1. `git clone https://git.openstack.org/openstack-dev/devstack`

> :white_check_mark: **Additional Info**
> 
> `stack.sh` is a very long, but well documented script.  Check it out and peruse it [here](http://docs.openstack.org/developer/devstack/stack.sh.html) while you are being patient.

* user can sudo
* git is intalled
* clone openstack
* edit config (new local.conf)

:question: why are they setting MULTI_HOST, not likely that we are using more than one host

Run stack.sh:
`./stack.sh 2>&1 | tee stack.out`

> :white_check_mark: **Additional Info**
>
> In order to capture the printed results of `stack.sh` we pipe it to a file
>
> * `2>&1` pipes stderr to stdout (allowing us to capture both)
> * `|` is a pipe, it sends values to the next command
> * `tee` is splits a pipe (like a "T) it sends printed results to a file `stack.log` in addition to printing to the screen

* :red_circle: aws vm's need to in a security group that allows ports: 22, 80* 
* :red_circle: devstack install fails on t2.micro ubuntu :(
