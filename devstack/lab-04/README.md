# Lab 4 - DevStack Security Groups & Floating IP 

  Lab Objectives:

  0. Become familiar with adding Security Groups
  0. Become familiar with adding a Floating IP Address

## Create a Security Group

  0. Login to the OpenStack Horizon Web Interface by navigating your browser to the public IP address of the controller
  0. :red_circle: TODO login as user?
  0. Navigate to: Project > Compute > Access > Create Security Group

     ![Create Security Group](security-create.png)
     ![Create Security Group](security-create2.png)

  0. Manage the new group and add an SSH rule
  
     ![Manage Group](security-manage.png) 
     ![Add Rule](secuirty-add.png) 
     ![Create Rule](security-ssh.png) 

  0. Create another rule for HTTPS

     ![New Rules](security-rules.png)
