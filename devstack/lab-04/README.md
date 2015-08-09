# Lab 4 - DevStack Security Groups & Floating IP 

  Lab Objectives:

  0. Become familiar with adding a Floating IP Address
  0. Become familiar with adding Security Groups

## Create and apply a Floating IP address

  0. Navigate to: Project > Compute > Instances
  0. Add a floating IP address to a running instance

     ![Add Floadint IP](img/floating-add.png)
     ![Add Floadint IP](img/floating-add2.png)

  0. Test that this 

## Create and apply a Security Group

  0. Login to the OpenStack Horizon Web Interface by navigating your browser to the public IP address of the controller
  0. :red_circle: TODO login as user?
  0. Navigate to: Project > Compute > Access > Create Security Group

     ![Create Security Group](img/security-create.png)
     ![Create Security Group](img/security-create2.png)

  0. Manage the new group and add an SSH rule
  
     ![Manage Group](img/security-manage-rule.png) 
     ![Add Rule](img/security-add.png) 
     ![Create Rule](img/security-ssh.png) 

  0. Create another rule for HTTPS, the resulting Security Group should look like this

     ![New Rules](img/security-rules.png)
  
  0. Add the security group to a running instance
  

     ![Add Security Group](img/security-associate.png)
     ![Add Security Group](img/security-associate2.png)

     Click the `+` on the Basic line and then Save

