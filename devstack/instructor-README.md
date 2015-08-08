# DevStack Lab Implementation Notes

Notes for implementation:
* aws vm's need to in a security group that allows a crap-ton of ports, opening all of them for now 
* devstack install fails on t2.micro ubuntu. :( t2.medium worked
* devstack install takes about 15 minutes, might want to ansibalize that? 
* Anytime ./stack.sh fails we should document the error and solution in [common errors](common-errors.md), most of my time spent on this lab was mis-configuring local.conf and seeing what errors show up
* is the time waiting for devstack to install useful for students or should we do it for them?  
