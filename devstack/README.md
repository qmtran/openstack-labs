# DevStack Lab

:red_circle: TODO A well thoughout over-view paragraph about what this lab is about should go here.

Lab Objectives:

  0. Install a DevStack controller
  0. Become familiar with the OpenStack Horizon Interface
  0. Launch an instance from the Horizon Interface
  0. Install a DevStack compute node
  0. Become familiar with adding a Floating IP Address
  0. Become familiar with adding Security Groups
  0. Become familiar with the openstack command line utilities

## Lab 0 - Document Lab IP addresses
 
Your instructor will provide two IP addresses for this lab. 

         | Controller    | Compute     |
-------- | ------------- | ----------- |
Public   | W.X.Y.Z       | W.X.Y.Z     |
Internal | A.B.C.D       | A.B.C.D     |

0. Edit this README.md file and add the ip addresses to your forked repository.
  * You can make these changes in the github webpage or from your checkedout version.
  * Make sure your changes are committed and pushed to github.com and then refresh the page.

0. Record your instance's internal IP address in the table
  
   * `ssh ubuntu@<CONTROLLER IP> -i student.pem` 
   * `ip addr show dev eth0`

0. Set the hostname on each to help with command line differentiation

   * `sudo hostname <controller or compute>`
   * `bash` to show the result 

