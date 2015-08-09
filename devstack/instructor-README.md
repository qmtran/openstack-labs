# DevStack Lab Implementation Notes

Notes for implementation:
* aws vm's need to in a security group that allows a crap-ton of ports, opening all of them for now 
* devstack install fails on t2.micro ubuntu. :( t2.medium worked
* devstack install takes about 15 minutes, plan appropriately
* Anytime ./stack.sh fails we should document the error and solution in [common errors](common-errors.md), most of my time spent on this lab was mis-configuring local.conf and seeing what errors show up
* VPC == 172.30.1.0/24, needs changed in local.conf's if not correct
